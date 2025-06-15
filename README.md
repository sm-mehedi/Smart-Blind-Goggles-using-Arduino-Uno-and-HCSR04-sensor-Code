<h1 align="center">👓 Smart Vision: Ultrasonic Goggles for the Visually Impaired using Arduino</h1>



<hr>

<h2>📽️ Project Demonstration</h2>
<p>
  <a href="https://youtu.be/NryeHlxK-iQ?si=rGh0vEzg2MLM_4n5" target="_blank">▶️ Watch the Demo Video</a>
</p>

<hr>

<h2>🧠 Project Overview</h2>
<p>
  <strong>Smart Vision</strong> is an assistive technology prototype built using Arduino that helps visually impaired individuals detect nearby obstacles using ultrasonic sensors and alerts them with a buzzer. The goggles are lightweight, easy to use, and ideal for low-cost deployment.
</p>

<hr>

<h2>🔩 Components Used</h2>
<ul>
  <li>Arduino Uno R3</li>
  <li>HC-SR04 Ultrasonic Sensor</li>
  <li>Buzzer (Piezo)</li>
  <li>9V Battery + Connector</li>
  <li>Jumper Wires (Male-to-Male)</li>
  <li>Breadboard</li>
  <li>Safety Glasses (used to mount sensors)</li>
</ul>

<hr>

<h2>⚙️ Features</h2>
<ul>
  <li>Obstacle detection within a customizable distance (default: 50cm)</li>
  <li>Audio alert using a buzzer for proximity</li>
  <li>Low power consumption</li>
  <li>Portable and wearable</li>
</ul>

<hr>

<h2>📐 Circuit Diagram</h2>
<p>
  <strong>Connection Summary:</strong><br>
  <ul>
    <li><code>HC-SR04 TRIG</code> → Pin 9</li>
    <li><code>HC-SR04 ECHO</code> → Pin 8</li>
    <li><code>Buzzer</code> → Pin 11</li>
    <li><code>VCC</code> → 5V</li>
    <li><code>GND</code> → GND</li>
  </ul>
</p>

<hr>

<h2>💻 Arduino Code Explanation</h2>

<pre>
<code>
#define TRIG_PIN 9
#define ECHO_PIN 8
#define BUZZER_PIN 11

void setup() {
  pinMode(TRIG_PIN, OUTPUT);
  pinMode(ECHO_PIN, INPUT);
  pinMode(BUZZER_PIN, OUTPUT);
  Serial.begin(9600);
}

void loop() {
  long duration;
  float distance;

  digitalWrite(TRIG_PIN, LOW);
  delayMicroseconds(2);
  digitalWrite(TRIG_PIN, HIGH);
  delayMicroseconds(10);
  digitalWrite(TRIG_PIN, LOW);

  duration = pulseIn(ECHO_PIN, HIGH);
  distance = duration * 0.034 / 2;

  Serial.print("Distance: ");
  Serial.print(distance);
  Serial.println(" cm");

  if (distance < 50) {
    digitalWrite(BUZZER_PIN, HIGH); // Object detected
  } else {
    digitalWrite(BUZZER_PIN, LOW);  // No object
  }

  delay(200);
}
</code>
</pre>

<p>
  This code continuously measures distance using the ultrasonic sensor. If an object is detected within 50 cm, the buzzer is activated.
</p>

<hr>

<h2>📦 How to Use</h2>
<ol>
  <li>Connect all components as shown above.</li>
  <li>Upload the code to your Arduino using the Arduino IDE.</li>
  <li>Mount the ultrasonic sensor on the goggles and wear them.</li>
  <li>Power the Arduino with a 9V battery or USB.</li>
</ol>

<hr>

<h2>📚 Future Improvements</h2>
<ul>
  <li>Add vibration motor for silent feedback</li>
  <li>Use rechargeable lithium battery with charging circuit</li>
  <li>Improve design to include multiple sensors for 180° detection</li>
</ul>

<hr>


<p align="center">⭐️ Star this repo if you found it helpful!</p>
