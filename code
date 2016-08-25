#include <IRremote.h>
#include <IRremoteInt.h>


float sinVal;
float toneVal;
int RECV_PIN = 11;
int buzzer = 8; 

IRrecv irrecv(RECV_PIN);
decode_results results;
void setup(){
Serial.begin(9600);
irrecv.enableIRIn();
pinMode(buzzer,OUTPUT); // define LED as output signal
}
void loop() {
if (irrecv.decode(&results)) {
Serial.println(results.value, HEX);
//once receive code from power button, the state of LED is changed from HIGH
//to LOW or from LOW to HIGH.
if(results.value == 0xFD00FF){
for(int x=0; x<180; x++){
    //convert angle of sinusoidal to radian measure
    sinVal = (sin(x*(3.1412/180)));
    //generate sound of different frequencies by sinusoidal value
    toneVal = 2000+(int(sinVal*1000));
    //Set a frequency for Pin-out 8
    tone(buzzer,toneVal);
    delay(2);
  }
}
else{
    tone(buzzer, 0);
    
  }
}
}
