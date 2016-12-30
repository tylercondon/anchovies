# Voice Recognition

## Problem to Solve

Usage for this code is when you are going to bed but you do not want to climb out of bed and flip the switch with this code you can say a keyword (ex. anchovies). You will then say your command example. Turn off lights. Turn on lights. and this is the usage

## Goal

What my goal is to find a better way of home lighting when this experiment is done I hope that I am able to continue to work on this project. And make my program be able to control a entire house.

## Materials

1. Raspberry Pi
2. HDMI chord
3. 1 SD card
4. 1 computer
5. USB mouse
6. USB keyboard
7. USB microphone

## How it Works

It works by you saying a key word then you say a command which goes to Google Speech API. Google Speech API
then gives you back text to use in the program.

I researched on how to get this to work together and found PiAUISuite a program that triggers on a keyword and calls commands that you create. Here is a link to the GitHub project: [https://github.com/StevenHickson/PiAUISuite](https://github.com/StevenHickson/PiAUISuite)

Here is a diagram to show how it works:

![PiAUISuite](https://github.com/tylercondon/anchovies/raw/master/drawings/PiAUISuite.png)

There were many software pieces I had to learn to use, or create myself to make this work.

### Google Speech API

Google Speech API is a web site that turns speech into text and text into speech.

### Arecord

Arecord records audio file from the microphone.

### PiAUISuite

PiAUISuite is a program that trigger on a keyword and calls commands that you create. Here's a snippet from the configuration file, `.commands.conf` that calls the commands:

```
lights on==/home/pi/led_on
lights off==/home/pi/led_off
```

### led_on

Script to say "turning on lights" and calls the `LED_ON.py` program. Notice the call to `tts`. That's a small program that calls the Google Speech API and turns text into audio.

```
#!/bin/bash
tts "Turning on lights!"
sudo python /home/pi/LED_ON.py
```

### led_off

Script to say "turning off lights" and calls the `LED_OFF.py` program.

```
#!/bin/bash
tts "Turning off lights!"
sudo python /home/pi/LED_OFF.py
```

### Python and Python Code

Python runs the code to control the GPIO. Here's the Python program, `LED_ON.py`, that turns on the LED by setting the GPIO high:

```python
import RPi.GPIO as GPIO
GPIO.setmode(GPIO.BCM)
GPIO.setwarnings(False)
GPIO.setup(18,GPIO.OUT)
print "LED on"
GPIO.output(18,GPIO.HIGH)
```

The code, `LED_OFF.py`, that turns the LED off by setting the GPIO low:

```python
import RPi.GPIO as GPIO
GPIO.setmode(GPIO.BCM)
GPIO.setwarnings(False)
GPIO.setup(18,GPIO.OUT)
print "LED off"
GPIO.output(18,GPIO.LOW)
```

### GPIO

Used to output a high or low voltage to a pin in the circuit for the LED.

## Work Log

This is the steps of what I have done over three days.

### Day 1

I had to download a bunch of programs. That took hours then I started to research on how to use the Raspberry Pi and I found DIY hacking that had a great tutorial on how to build a voice recognition program but it had bugs and I am still fixing them.

### Day 2

Today I am writing more of my report. the voice recognition is working. but I haven't got the lights to work yet. 

### Day 3

Today I finished the program the light works and I am just finishing up the report.

## Conclusion

I have finished project Anchovies. (That is what I called it ). It was a complete success. I was able to make an LED light turn on with a voice command. It was hard but I know that it paid off. Thank you to my dad he is a software engineer and helped me a lot during the experiment.