int sensorPin = A0;   // water sensor
int redLED = 2;
int yellowLED = 3;
int greenLED = 4;

int value = 0;

void setup() {
  pinMode(redLED, OUTPUT);
  pinMode(yellowLED, OUTPUT);
  pinMode(greenLED, OUTPUT);
  Serial.begin(9600);
}

void loop() {
  value = analogRead(sensorPin);
  Serial.println(value);

  if (value < 300) {
    // LOW
    digitalWrite(redLED, HIGH);
    digitalWrite(yellowLED, LOW);
    digitalWrite(greenLED, LOW);
  }
  else if (value >= 300 && value < 600) {
    // MEDIUM
    digitalWrite(redLED, LOW);
    digitalWrite(yellowLED, HIGH);
    digitalWrite(greenLED, LOW);
  }
  else {
    // HIGH
    digitalWrite(redLED, LOW);
    digitalWrite(yellowLED, LOW);
    digitalWrite(greenLED, HIGH);
  }

  delay(500);
}
