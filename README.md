# VOICE-ACTIVATION

It is a prototype of the Home Automation. It helps to control your Arduino by Bluetooth connectivity with voice commands using an Android Smartphone. It easily control our Household Appliances like TV, Computer , Fan , AC , Lights and many more.

Before we make a voice activated home automation system, we must first learn the basic principles of the experiment. This guide will let you command the Arduino using your Android smartphone and a HC-05 Bluetooth module.

STEP 1: 
Thing that you'll need:
- 5 LED Indicators (the color of your choice)
- Arduino UNO (a clone works fine)
- HC-05 Serial Bluetooth Module
- Solderless Breadboard
- Jumper Cables

STEP 2:
Connection of Arduino to Bluetooth module:
POWER- Bluetooth 5V------Arduino 5V
GND- Bluetooth GND-------Arduino GND
TX-  Bluetooth TX--------Arduino TX
RX-  Bluetooth RX--------Arduino RX

STEP 3:
Connection of LEDs:
led1 = 2, //Connect LED 1 To Pin #2 
led2 = 3, //Connect LED 2 To Pin #3 
led3 = 4, //Connect LED 3 To Pin #4 
led4 = 5, //Connect LED 4 To Pin #5 
led5 = 6; //Connect LED 5 To Pin #6 

STEP 4:
Programming of VOICE AUTOMATION:
//Coded By: Shubhangi Singh (20/6/2018)
//Voice Activated Arduino (Bluetooth + Android)
//Feel free to modify it but remember to give credit


String voice;
int 
led1 = 2, //Connect LED 1 To Pin #2 
led2 = 3, //Connect LED 2 To Pin #3 
led3 = 4, //Connect LED 3 To Pin #4 
led4 = 5, //Connect LED 4 To Pin #5 
led5 = 6; //Connect LED 5 To Pin #6 
//--------------------------Call A Function-------------------------------//  
void allon(){
     digitalWrite(led1, HIGH); 
     digitalWrite(led2, HIGH); 
     digitalWrite(led3, HIGH); 
     digitalWrite(led4, HIGH); 
     digitalWrite(led5, HIGH); 
}
void allof(){
     digitalWrite(led1, LOW); 
     digitalWrite(led2, LOW); 
     digitalWrite(led3, LOW); 
     digitalWrite(led4, LOW); 
     digitalWrite(led5, LOW);
}
//-----------------------------------------------------------------------//  
void setup() {
  Serial.begin(9600);
  pinMode(led1, OUTPUT); 
  pinMode(led2, OUTPUT); 
  pinMode(led3, OUTPUT); 
  pinMode(led4, OUTPUT); 
  pinMode(led5, OUTPUT); 
}
//-----------------------------------------------------------------------//  
void loop() {
  while (Serial.available()){  //Check if there is an available byte to read
  delay(10); //Delay added to make thing stable 
  char c = Serial.read(); //Conduct a serial read
  if (c == '#') {break;} //Exit the loop when the # is detected after the word
  voice += c; //Shorthand for voice = voice + c
  }  
  if (voice.length() > 0) {
    Serial.println(voice); 
//-----------------------------------------------------------------------//    
  //----------Control Multiple Pins/ LEDs----------//  
       if(voice == "*all on") {allon();}  //Turn Off All Pins (Call Function)
  else if(voice == "*all of"){allof();} //Turn On  All Pins (Call Function)
  
  //----------Turn On One-By-One----------// 
  else if(voice == "*TV on") {digitalWrite(led1, HIGH);} 
  else if(voice == "*fan on") {digitalWrite(led2, HIGH);}
  else if(voice == "*computer on") {digitalWrite(led3, HIGH);}
  else if(voice == "*bedroom lights on") {digitalWrite(led4, HIGH);}
  else if(voice == "*bathroom lights on") {digitalWrite(led5, HIGH);}
  //----------Turn Off One-By-One----------// 
  else if(voice == "*TV off") {digitalWrite(led1, LOW);} 
  else if(voice == "*fan off") {digitalWrite(led2, LOW);}
  else if(voice == "*computer off") {digitalWrite(led3, LOW);}
  else if(voice == "*bedroom lights off") {digitalWrite(led4, LOW);}
  else if(voice == "*bathroom lights off") {digitalWrite(led5, LOW);}
//-----------------------------------------------------------------------//  
voice="";}} //Reset the variable after initiating

STEP 5:
Download the APK of the App which I have given to you.

STEP 6:
LEARN HOW TO USE THE APP:
1. On your Bluetooth in your mobile.
2. Connecting to HC-05
3. Tap to say command which are written in code.
4. You say TV ON then TV will ON.





