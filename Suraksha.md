# Suraksha
SURAKSHA, aims to restrict the speed, in vicinity of deemed accident prone areas like  schools, hospitals, hairpins curves and other places where speed limit is enforced. Background Details: Suraksha enforces cost effectiveness, and energy efficiency by using LEDs for determining the vicinity of accident prone areas. Suraksha, can be incorporated to street lights or caution signals so that ordinary illumination is converted into smart transmitting devices(Retrofitting ). When the vehicle is near the vicinity, a decoder attached to vehicle decodes this signal to effectively control the speed.
// Base Transmitter
#include <SoftwareSerial.h>

SoftwareSerial slow(11, 3); // RX, TX
SoftwareSerial fast(12,2);

void setup()
{
  // Open serial communications and wait for port to open:
  Serial.begin(2400);
  while (!Serial) {
    ; // wait for serial port to connect. Needed for Leonardo only
  }


  //Serial.println("Goodnight moon!");

  // set the data rate for the SoftwareSerial port
  slow.begin(2400);
  fast.begin(2400);
  
}

void loop() // run over and over
{
slow.println("0");
fast.println("1");
//digitalWrite(2,1);

//digitalWrite(3,1);

//delay(100);
}
//MOVING VEHICLE CODE

#include <LiquidCrystal.h>
LiquidCrystal lcd(12, 11, 5, 4, 3, 2);




int data;
void setup()
{
  
  pinMode(7,OUTPUT);//same as above
  pinMode(8,OUTPUT);//for second one 

  lcd.begin(16, 2);
  Serial.begin(9600);
  
  
} 
int pwm=0;



void frwd(int del)
{
  
  digitalWrite(6,1);
digitalWrite(7,1);
delay(del);
digitalWrite(6,0);
digitalWrite(7
,0);
delay(2*del);
 
   
      
}
int flag=0;
int set=0;
int mil;
void loop() 
{
  //Serial.println(analogRead(A0));
  if(analogRead(A0)>800)
  {
  
  lcd.setCursor(0, 0);
   lcd.print("Speed Lt Enabled");
   lcd.setCursor(0, 1);
   lcd.print("Max Speed:25KMPH");
    frwd(200);
    //delay(10);
     
  }

  else
  {
    
    frwd(100);
    delay(10);
    lcd.setCursor(0, 0);
   lcd.print("Speed Lt Disabld");
   lcd.setCursor(0, 1);
   lcd.print("Drive Safely..."); 
  
  }
  

      //lcd.print(data);
  
   
  // lcd.setCursor(0,0);

//lcd.clear();

  
  /*if(data>upperThreshold)
  {
   dely=100;
   lcd.setCursor(0, 0);
   lcd.print("Speed Lt Enabled");
   lcd.setCursor(0, 1);
   lcd.print("Max Speed:25KMPH"); 
  }
  else if(data<lowerThreshold)
  {
   dely=255;
   lcd.setCursor(0, 0);
   lcd.print("Speed Lt Disabld");
   lcd.setCursor(0, 1);
   lcd.print("Drive Safely..."); 
    
  }
  */
  //delay(100);
}
