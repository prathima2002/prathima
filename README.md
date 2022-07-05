# prathima
package com.example.age; 
import 
android.app.DatePickerDialog; 
import android.graphics.Color; 
import 
android.graphics.drawable.ColorDrawable; 
import android.os.Bundle; 
import android.view.View; import 
android.widget.Button; import 
android.widget.DatePicker; 
import android.widget.TextView; 
import android.widget.Toast; 
importandroidx.appcompat.app.AppCompatActivit;
import org.joda.time.Period; 
import org.joda.time.PeriodType; 
import java.text.ParseException; 
importjava.text.SimpleDateFormat; 
import java.util.Calendar; import 
java.util.Date; 
public class MainActivity extends AppCompatActivity { 
 // initializing variables 
 Button btn_birth, btn_today, btn_calculate; 
 TextView tvResult; 
 DatePickerDialog.OnDateSetListener dateSetListener1, dateSetListener2; 
 @Override 
 protected void onCreate(Bundle savedInstanceState) { 
 super.onCreate(savedInstanceState); 
 setContentView(R.layout.activity_main); 
 // assign variables 
 btn_calculate = findViewById(R.id.btn_calculate); 
 tvResult = findViewById(R.id.tv_result); 
 // for year 
 int year = calendar.get(Calendar.YEAR); 
 // for month 
 int month = calendar.get(Calendar.MONTH); 
 // for date 
 int day = calendar.get(Calendar.DAY_OF_MONTH); 
 SimpleDateFormat simpleDateFormat = new SimpleDateFormat("dd/MM/yyyy"); 
btn_birth = findViewById(R.id.bt_birth);
btn_today = findViewById(R.id.bt_today);
 // to set the current date as by default 
 String date = simpleDateFormat.format(Calendar.getInstance().getTime()); 
 btn_today.setText(date); 
 // action to be performed when button 1 is clicked 
 btn_birth.setOnClickListener(new View.OnClickListener() { 
 @Override 
 public void onClick(View view) { 
 // date picker dialog is used 
 // and its style and color are also passed 
 DatePickerDialog datePickerDialog = new 
DatePickerDialog(MainActivity.this, 
android.R.style.Theme_Holo_Light_Dialog_MinWidth, dateSetListener1, 
year, month, day 
 ); 
 // to set background for datepicker 
 datePickerDialog.getWindow().setBackgroundDrawable(n
ew ColorDrawable(Color.TRANSPARENT)); 
 datePickerDialog.show(); 
 } 
 }); 
 // it is used to set the date which user selects 
 dateSetListener1 = new DatePickerDialog.OnDateSetListener() { 
 @Override 
{ 
 // here month+1 is used so that 
 // actual month number can be displayed 
 // otherwise it starts from 0 and it shows 
 // 1 number less for every month 
 // example- for january month=0 
 month = month + 1; 
 String date = day + "/" + month + "/" + year; 
 btn_birth.setText(date); 
 } 
 }; 
 // action to be performed when button 2 is clicked 
 btn_today.setOnClickListener(new View.OnClickListener() { 
 @Override 
 public void onClick(View view) { 
 // date picker dialog is used 
 // and its style and color are also passed 
 DatePickerDialog datePickerDialog = new 
DatePickerDialog(MainActivity.this, 
android.R.style.Theme_Holo_Light_Dialog_MinWidth, dateSetListener2, 
year, month, day 
 ); 
 // to set background for datepicker 
 datePickerDialog.getWindow().setBackgroundDrawable(n
ew ColorDrawable(Color.TRANSPARENT)); 
 datePickerDialog.show(); 
 } 
 }); 
 // it is used to set the date which user selects 
public void onDateSet(DatePicker view, int year, int month, int day)
long startdate = date1.getTime();
long endDate = date2.getTime();
 dateSetListener2 = new DatePickerDialog.OnDateSetListener() { 
 @Override 
{ 
 // here month+1 is used so that 
 // actual month number can be displayed 
 // otherwise it starts from 0 and it shows 
 // 1 number less for every month 
 // example- for january month=0 
 month = month + 1; 
 String date = day + "/" + month + "/" + year; 
 btn_today.setText(date); 
 } 
 }; 
 // action to be performed when calculate button is clicked 
 btn_calculate.setOnClickListener(new View.OnClickListener() { 
 @Override 
 public void onClick(View view) { 
 // converting the inputted date to string 
 SimpleDateFormat simpleDateFormat1 = 
new SimpleDateFormat("dd/MM/yyyy"); 
 try { 
 // converting it to date format 
 // condition 
 if (startdate <= endDate) { 
 org.joda.time.Period period = new 
Period(startdate, endDate, PeriodType.yearMonthDay()); 
 int years = period.getYears(); 
 int months = period.getMonths(); 
 int days = period.getDays(); 
 // show the final output 
 tvResult.setText(years + " Years |" + months + "Months 
|" + days + "Days"); 
 } else { 
 // show message 
 Toast.makeText(MainActivity.this, "BirthDate should 
not be larger then today's date!", Toast.LENGTH_SHORT).show(); 
 } 
 } catch (ParseException e) { 
 e.printStackTrace(); 
 } 
 } 
 }); 
} 
}
Date date1 = simpleDateFormat1.parse(sDate);
Date date2 = simpleDateFormat1.parse(eDate);
public void onDateSet(DatePicker view, int year, int month, int day)
String sDate = btn_birth.getText().toString();
String eDate = btn_today.getText().toString();
XML 
<?xml version="1.0" encoding="utf-8"?> 
<!-- Parent layout as linear layout--> 
<LinearLayout 
 xmlns:android="http://schemas.android.com/apk/res/android" 
 xmlns:tools="http://schemas.android.com/tools" 
 android:layout_width="match_parent" 
 android:layout_height="match_parent" 
 android:gravity="center" 
 android:orientation="vertical" 
 android:padding="10dp" 
 tools:context=".MainActivity"> 
 <!-- linear layout to show datepickers--> 
 <LinearLayout 
 android:layout_width="match_parent" 
 android:layout_height="wrap_content"> 
 <!-- to select the first date--> 
 <Button 
 android:id="@+id/bt_birth" 
 android:background="@android:color/transparent" 
 android:drawableRight="@drawable/ic_baseline" 
 android:text="01/01/2021" 
 android:textColor="@color/black" 
 android:textSize="13sp" /> 
 <!-- displaying message as "to"--> 
 <TextView 
 android:gravity="center_horizontal" 
 android:text="To" 
 android:textColor="@color/black" 
 android:textSize="20sp" 
 android:textStyle="bold" /> 
 <!-- to display date number 2--> 
 <Button 
 android:id="@+id/bt_today" 
 android:background="@android:color/transparent" 
 android:drawableRight="@drawable/ic_baseline" 
 android:textColor="@color/black" 
 android:textSize="13sp" /> 
 </LinearLayout> 
 <!-- to perform the calculation--> 
 <Button 
 android:id="@+id/btn_calculate" 
 android:layout_width="wrap_content" 
 android:layout_height="wrap_content" 
android:layout_width="145dp"
android:layout_height="50dp"
android:layout_width="100dp"
android:layout_height="50dp"
android:layout_width="150dp"
android:layout_height="50dp"
 android:layout_marginTop="10dp" 
 android:text="calculate" /> 
 <!-- to display the message "Result"--> 
 <TextView 
 android:layout_width="wrap_content" 
 android:layout_height="wrap_content" 
 android:layout_marginTop="50dp" 
 android:text="Result" 
 android:textColor="@android:color/holo_blue_bright" 
 android:textSize="30sp" 
 android:textStyle="bold" /> 
 <!-- To show the final output(age)--> 
 <TextView 
 android:id="@+id/tv_result" 
 android:layout_width="wrap_content" 
 android:layout_height="wrap_content" 
 android:layout_marginTop="10dp" 
 android:text="0 Years | 0 Months | 0 Days" 
 android:textSize="25sp" 
 android:textStyle="bold" /> 
</LinearLayout> 
IC BASE LINE XML 
<?xml version="1.0" encoding="utf-8"?> 
<selector xmlns:android="http://schemas.android.com/apk/res/android"> 
</selector> 
BUILD GRADLE 
plugins { 
} 
android { 
 compileSdk 32 
 defaultConfig { 
 applicationId "com.example.age" 
 minSdk 22 
 targetSdk 32 
 versionCode 1 
 versionName "1.0" 
 testInstrumentationRunner "androidx.test.runner.AndroidJUnitRunner" 
 } 
 buildTypes { 
 release { 
 minifyEnabled false 
id 'com.android.application'
 proguardFiles 
getDefaultProguardFile('proguard-android-optimize.txt'), 'proguard-rules.pro' 
 } 
 } 
 compileOptions { 
 } 
 buildFeatures { 
 viewBinding true 
} 
dependencies { 
 implementation 'joda-time:joda-time:2.9.1' 
 implementation 'androidx.appcompat:appcompat:1.4.1' 
 implementation 'com.google.android.material:material:1.5.0' 
 implementation 'androidx.constraintlayout:constraintlayout:2.1.3' 
 implementation 'androidx.navigation:navigation-fragment:2.4.1' 
 implementation 'androidx.navigation:navigation-ui:2.4.1' 
 testImplementation 'junit:junit:4.13.2' 
 androidTestImplementation 'androidx.test.ext:junit:1.1.3' 
}
