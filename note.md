# 📱 Calculator UI Design Notes

---

# File: app/src/main/java/com/example/calculator/MainActivity.kt

Action:
Replace Existing File

```kotlin
package com.example.calculator

import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle

class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
    }
}
```

---

# File: app/src/main/res/values/colors.xml

Action:
Edit Existing File

```xml
<?xml version="1.0" encoding="utf-8"?>
<resources>

    <!-- Background -->
    <color name="background">#202124</color>

    <!-- Number Button -->
    <color name="numberButton">#3C4043</color>

    <!-- Function Button -->
    <color name="functionButton">#5F6368</color>

    <!-- Operator Button -->
    <color name="operatorButton">#F9AB00</color>

    <!-- Text -->
    <color name="white">#FFFFFF</color>
    <color name="black">#000000</color>

</resources>
```

---

# File: app/src/main/res/drawable/button_number.xml

Action:
Create New File

```xml
<?xml version="1.0" encoding="utf-8"?>

<shape xmlns:android="http://schemas.android.com/apk/res/android">

    <solid android:color="@color/numberButton"/>

    <corners android:radius="18dp"/>

    <padding
        android:left="8dp"
        android:right="8dp"
        android:top="8dp"
        android:bottom="8dp"/>

</shape>
```

---

# File: app/src/main/res/drawable/button_function.xml

Action:
Create New File

```xml
<?xml version="1.0" encoding="utf-8"?>

<shape xmlns:android="http://schemas.android.com/apk/res/android">

    <solid android:color="@color/functionButton"/>

    <corners android:radius="18dp"/>

    <padding
        android:left="8dp"
        android:right="8dp"
        android:top="8dp"
        android:bottom="8dp"/>

</shape>
```

---

# File: app/src/main/res/drawable/button_operator.xml

Action:
Create New File

```xml
<?xml version="1.0" encoding="utf-8"?>

<shape xmlns:android="http://schemas.android.com/apk/res/android">

    <solid android:color="@color/operatorButton"/>

    <corners android:radius="18dp"/>

    <padding
        android:left="8dp"
        android:right="8dp"
        android:top="8dp"
        android:bottom="8dp"/>

</shape>
```

---

# File: app/src/main/res/values/themes.xml

Action:
Edit Existing File

```xml
<resources xmlns:tools="http://schemas.android.com/tools">

    <style
        name="Theme.Calculator"
        parent="Theme.Material3.DayNight.NoActionBar">

        <item name="android:statusBarColor">@color/background</item>

        <item name="android:navigationBarColor">@color/background</item>

        <item name="colorPrimary">@color/operatorButton</item>

    </style>

</resources>
```

---

# File: app/src/main/res/values/strings.xml

Action:
Edit Existing File

```xml
<resources>

    <string name="app_name">Calculator</string>

</resources>
```
---

## 📂 File Location

```
app
└── src
    └── main
        └── res
            └── layout
                └── activity_main.xml
```

---

## 📝 Action

```
Replace Existing File
```

---




- Root ConstraintLayout
- Toolbar
- Display Section

---

## 💻 Code

```xml
<?xml version="1.0" encoding="utf-8"?>

<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"

    android:layout_width="match_parent"
    android:layout_height="match_parent"

    android:background="@color/background"

    android:padding="16dp"

    tools:context=".MainActivity">

    <!-- ================= Toolbar ================= -->

    <LinearLayout
        android:id="@+id/topBar"
        android:layout_width="0dp"
        android:layout_height="56dp"
        android:orientation="horizontal"
        android:gravity="center_vertical"

        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent">

        <ImageButton
            android:id="@+id/btnMenu"
            android:layout_width="40dp"
            android:layout_height="40dp"
            android:background="@android:color/transparent"
            android:src="@android:drawable/ic_menu_sort_by_size"
            android:tint="@color/white"/>

        <TextView
            android:id="@+id/tvTitle"
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_weight="1"
            android:text="Standard"
            android:textColor="@color/white"
            android:textStyle="bold"
            android:textSize="20sp"
            android:gravity="center"/>

        <ImageButton
            android:id="@+id/btnMore"
            android:layout_width="40dp"
            android:layout_height="40dp"
            android:background="@android:color/transparent"
            android:src="@android:drawable/ic_menu_more"
            android:tint="@color/white"/>

    </LinearLayout>

    <!-- ================= Display ================= -->

    <LinearLayout
        android:id="@+id/displayLayout"
        android:layout_width="0dp"
        android:layout_height="180dp"
        android:orientation="vertical"
        android:gravity="bottom|end"
        android:padding="8dp"

        app:layout_constraintTop_toBottomOf="@id/topBar"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent">

        <TextView
            android:id="@+id/tvExpression"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="25 + 75"
            android:textColor="@color/white"
            android:textSize="28sp"/>

        <TextView
            android:id="@+id/tvResult"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="100"
            android:textColor="@color/white"
            android:textStyle="bold"
            android:textSize="54sp"/>

    </LinearLayout>
```

---

## 📱 Current Output

```
☰          Standard          ⋮


               25 + 75

                  100
```
---

<!-- ============================= -->
<!-- Calculator Buttons -->
<!-- ============================= -->
```
<androidx.gridlayout.widget.GridLayout
    android:id="@+id/calculatorGrid"
    android:layout_width="0dp"
    android:layout_height="0dp"
    android:layout_marginTop="12dp"
    android:columnCount="4"
    android:rowCount="5"
    android:alignmentMode="alignMargins"
    android:useDefaultMargins="true"
    app:layout_constraintTop_toBottomOf="@id/displayLayout"
    app:layout_constraintBottom_toBottomOf="parent"
    app:layout_constraintStart_toStartOf="parent"
    app:layout_constraintEnd_toEndOf="parent">

    <!-- ================= Row 1 ================= -->

    <com.google.android.material.button.MaterialButton
        android:id="@+id/btnAC"
        android:layout_width="0dp"
        android:layout_height="70dp"
        android:layout_columnWeight="1"
        android:text="AC"
        android:textSize="20sp"
        android:textStyle="bold"
        android:textColor="@color/white"
        android:background="@drawable/button_function"/>

    <com.google.android.material.button.MaterialButton
        android:id="@+id/btnPercent"
        android:layout_width="0dp"
        android:layout_height="70dp"
        android:layout_columnWeight="1"
        android:text="%"
        android:textSize="20sp"
        android:textStyle="bold"
        android:textColor="@color/white"
        android:background="@drawable/button_function"/>

    <com.google.android.material.button.MaterialButton
        android:id="@+id/btnDelete"
        android:layout_width="0dp"
        android:layout_height="70dp"
        android:layout_columnWeight="1"
        android:text="⌫"
        android:textSize="20sp"
        android:textStyle="bold"
        android:textColor="@color/white"
        android:background="@drawable/button_function"/>

    <com.google.android.material.button.MaterialButton
        android:id="@+id/btnDivide"
        android:layout_width="0dp"
        android:layout_height="70dp"
        android:layout_columnWeight="1"
        android:text="÷"
        android:textSize="22sp"
        android:textStyle="bold"
        android:textColor="@color/black"
        android:background="@drawable/button_operator"/>

    <!-- ================= Row 2 ================= -->

    <com.google.android.material.button.MaterialButton
        android:id="@+id/btn7"
        android:layout_width="0dp"
        android:layout_height="70dp"
        android:layout_columnWeight="1"
        android:text="7"
        android:textSize="22sp"
        android:textColor="@color/white"
        android:background="@drawable/button_number"/>

    <com.google.android.material.button.MaterialButton
        android:id="@+id/btn8"
        android:layout_width="0dp"
        android:layout_height="70dp"
        android:layout_columnWeight="1"
        android:text="8"
        android:textSize="22sp"
        android:textColor="@color/white"
        android:background="@drawable/button_number"/>

    <com.google.android.material.button.MaterialButton
        android:id="@+id/btn9"
        android:layout_width="0dp"
        android:layout_height="70dp"
        android:layout_columnWeight="1"
        android:text="9"
        android:textSize="22sp"
        android:textColor="@color/white"
        android:background="@drawable/button_number"/>

    <com.google.android.material.button.MaterialButton
        android:id="@+id/btnMultiply"
        android:layout_width="0dp"
        android:layout_height="70dp"
        android:layout_columnWeight="1"
        android:text="×"
        android:textSize="22sp"
        android:textStyle="bold"
        android:textColor="@color/black"
        android:background="@drawable/button_operator"/>

        

<!-- ================= Row 3 ================= -->

<com.google.android.material.button.MaterialButton
    android:id="@+id/btn4"
    android:layout_width="0dp"
    android:layout_height="70dp"
    android:layout_columnWeight="1"
    android:text="4"
    android:textSize="22sp"
    android:textColor="@color/white"
    android:background="@drawable/button_number"/>

<com.google.android.material.button.MaterialButton
    android:id="@+id/btn5"
    android:layout_width="0dp"
    android:layout_height="70dp"
    android:layout_columnWeight="1"
    android:text="5"
    android:textSize="22sp"
    android:textColor="@color/white"
    android:background="@drawable/button_number"/>

<com.google.android.material.button.MaterialButton
    android:id="@+id/btn6"
    android:layout_width="0dp"
    android:layout_height="70dp"
    android:layout_columnWeight="1"
    android:text="6"
    android:textSize="22sp"
    android:textColor="@color/white"
    android:background="@drawable/button_number"/>

<com.google.android.material.button.MaterialButton
    android:id="@+id/btnMinus"
    android:layout_width="0dp"
    android:layout_height="70dp"
    android:layout_columnWeight="1"
    android:text="-"
    android:textSize="24sp"
    android:textStyle="bold"
    android:textColor="@color/black"
    android:background="@drawable/button_operator"/>

<!-- ================= Row 4 ================= -->

<com.google.android.material.button.MaterialButton
    android:id="@+id/btn1"
    android:layout_width="0dp"
    android:layout_height="70dp"
    android:layout_columnWeight="1"
    android:text="1"
    android:textSize="22sp"
    android:textColor="@color/white"
    android:background="@drawable/button_number"/>

<com.google.android.material.button.MaterialButton
    android:id="@+id/btn2"
    android:layout_width="0dp"
    android:layout_height="70dp"
    android:layout_columnWeight="1"
    android:text="2"
    android:textSize="22sp"
    android:textColor="@color/white"
    android:background="@drawable/button_number"/>

<com.google.android.material.button.MaterialButton
    android:id="@+id/btn3"
    android:layout_width="0dp"
    android:layout_height="70dp"
    android:layout_columnWeight="1"
    android:text="3"
    android:textSize="22sp"
    android:textColor="@color/white"
    android:background="@drawable/button_number"/>

<com.google.android.material.button.MaterialButton
    android:id="@+id/btnPlus"
    android:layout_width="0dp"
    android:layout_height="70dp"
    android:layout_columnWeight="1"
    android:text="+"
    android:textSize="22sp"
    android:textStyle="bold"
    android:textColor="@color/black"
    android:background="@drawable/button_operator"/>

<!-- ================= Row 5 ================= -->

<com.google.android.material.button.MaterialButton
    android:id="@+id/btn0"
    android:layout_width="0dp"
    android:layout_height="70dp"
    android:layout_columnWeight="1"
    android:text="0"
    android:textSize="22sp"
    android:textColor="@color/white"
    android:background="@drawable/button_number"/>

<com.google.android.material.button.MaterialButton
    android:id="@+id/btnDot"
    android:layout_width="0dp"
    android:layout_height="70dp"
    android:layout_columnWeight="1"
    android:text="."
    android:textSize="22sp"
    android:textColor="@color/white"
    android:background="@drawable/button_number"/>

<com.google.android.material.button.MaterialButton
    android:id="@+id/btnEqual"
    android:layout_width="0dp"
    android:layout_height="70dp"
    android:layout_columnSpan="2"
    android:layout_columnWeight="2"
    android:text="="
    android:textSize="24sp"
    android:textStyle="bold"
    android:textColor="@color/black"
    android:background="@drawable/button_operator"/>

</androidx.gridlayout.widget.GridLayout>

</androidx.constraintlayout.widget.ConstraintLayout>
---

# Project Structure


app

└── src

    └── main

        ├── java

        │      MainActivity.kt

        │

        └── res

            ├── drawable

            │      button_number.xml

            │      button_function.xml

            │      button_operator.xml

            │

            ├── layout

            │      activity_main.xml

            │

            └── values

                   colors.xml

                   themes.xml

                   strings.xml
```

# 📱 File: MainActivity.kt

## 📂 Location

```
app
└── src
    └── main
        └── java
            └── com
                └── example
                    └── calculator
                        └── MainActivity.kt
```

---

## Action

```
Replace Existing File
```

---

## Code

```kotlin
package com.example.calculator

import android.os.Bundle
import androidx.appcompat.app.AppCompatActivity

class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)

        // Load Login UI
        setContentView(R.layout.activity_main)

        // UI only
        // No Login Logic
        // No Firebase
        // No Database
    }
}
```

---

## Output

```
App Launch
      │
      ▼
MainActivity
      │
      ▼
activity_main.xml
      │
      ▼
Login Screen Display
```

---

## Next Step (Optional)

যদি Button Click দেখাতে চাও (কোনো Login Logic ছাড়া), তাহলে নিচের Code যোগ করতে পারো।

```kotlin
package com.example.calculator

import android.os.Bundle
import android.widget.Toast
import androidx.appcompat.app.AppCompatActivity
import com.google.android.material.button.MaterialButton

class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        val btnLogin = findViewById<MaterialButton>(R.id.btnLogin)

        btnLogin.setOnClickListener {

            Toast.makeText(
                this,
                "Login Button Clicked",
                Toast.LENGTH_SHORT
            ).show()

        }
    }
}
```



