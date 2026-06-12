---
title: "Optical Audio IEC958 is detected but no sound in Ubuntu 10.04"
date: 2010-05-04
forum: Multimedia Software
---

### Post by plutoprime on 2010-05-04
Hi, I have an Asus p5B Plus Motherboard (ICH8R southbridge and p965 northbridge i believe). Ubuntu has sound through regular audio jack and Optical Audio shows up in the Pulse Audio settings. 

Using the volume control applet, I set my hardware output to IEC958, and input to Analog and during playback of audio I can see the visual meter bouncing around but no sound is coming out of my speakers? What gives? 

My speaker receiver setup works fine with other OSs.. :( Any suggestions? Possibly a magical mute button that I can flip for this to start working?

---

### Post by Boludinux on 2010-07-17
I have exacly the same problem, bump

---

### Post by Karmalicious on 2010-07-18
I have no idea if this applies to your problem, but i had the same problem, only I wanted HDMI to output sound. I had the analog working just fine.
You could try this:

[LIST]
[*]aplay -L 
To find your iec958
[*]Download the surround test file from  [http://sverigesradio.se/laddahem/mul...est_011212.zip]("http://sverigesradio.se/laddahem/multikanal/dts/surroundtest_011212.zip")  and unpack it.
(Presumably any file will do, but since that's the one I used you might as well try it)
[*]aplay -D iec958:CARD=NVidia,DEV=0 ./SURROUNDTEST_011212.wav
(after -D you would input whatever aplay -L told you for the iec958 row, and the path to where you unpacked your .wav)
[/LIST]
It's quick to test, and it did help me so I just figured it might help you to.

---

### Post by Boludinux on 2010-07-18
Let's see the first command gave me:

> ariel@ariel-laptop:/$ aplay -l
**** Lista de PLAYBACK dispositivos hardware ****
tarjeta 0: Intel [HDA Intel], dispositivo 0: ALC268 Analog [ALC268 Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: Intel [HDA Intel], dispositivo 1: ALC268 Digital [ALC268 Digital]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: Intel [HDA Intel], dispositivo 6: Si3054 Modem [Si3054 Modem]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
I get this trying the first device but no sound:

> ariel@ariel-laptop:~/test$ aplay -D iec958:CARD=Intel,DEV=0 ./SURROUNDTEST_011212.wav 
Sonando WAVE './SURROUNDTEST_011212.wav' : Signed 16 bit Little Endian, Ratio 44100 Hz, Estéreo
:-({|= damn Lucid I had no problems in Jaunty

---

### Post by lidex on 2010-07-18
Use gnome-alsamixer to make sure digital outs are enabled. I believe they are muted by default. Also try toggling off/on. 
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

---

### Post by mitchlhannah on 2011-01-04
I have the same issue. I can't get sound out of the optical by anything I do with the mixer, yet the test file plays perfectly, and I can hear it directing sound to the various speakers as it plays. It seems that GNOME-Alsamixer isn't really doing anything. I've got Envy control installed also and it won't even show volumes playing through the computer speaker system. I'm running Ubuntu 10.10 and using a DMX 6Fire from Terratec.

---

### Post by guisar on 2011-01-04
> **mitchlhannah said:**
> I have the same issue. I can't get sound out of the optical by anything I do with the mixer, yet the test file plays perfectly, and I can hear it directing sound to the various speakers as it plays. It seems that GNOME-Alsamixer isn't really doing anything. I've got Envy control installed also and it won't even show volumes playing through the computer speaker system. I'm running Ubuntu 10.10 and using a DMX 6Fire from Terratec.

I would recommend downloading paman and ensuring that digital out is the default sink for the pulseaudio server. You can then go into the default sound card and ensure this same card (if you have more than one) is selected and finally into system settings and ensuring the pulseaudio server is selected for system sounds, music or whatever (it's under the multimedia control). Hope this helps.... Yeah- linux sound for noobs (and everyone else) needs a lot of help... Let's hope canonical fixes this for ubuntu and the other distros as well.

---

### Post by guisar on 2011-01-04
> **mitchlhannah said:**
> I have the same issue. I can't get sound out of the optical by anything I do with the mixer, yet the test file plays perfectly, and I can hear it directing sound to the various speakers as it plays. It seems that GNOME-Alsamixer isn't really doing anything. I've got Envy control installed also and it won't even show volumes playing through the computer speaker system. I'm running Ubuntu 10.10 and using a DMX 6Fire from Terratec.

I would recommend downloading paman and ensuring that digital out is the default sink for the pulseaudio server. You can then go into the default sound card and ensure this same card (if you have more than one) is selected and finally into system settings and ensuring the pulseaudio server is selected for system sounds, music or whatever (it's under the multimedia control). Hope this helps.... Yeah- linux sound for noobs (and everyone else) needs a lot of help... Let's hope canonical fixes this for ubuntu and the other distros as well.

---

### Post by allxk on 2011-02-23
> **Boludinux said:**
> I have exacly the same problem, bump
I have exacly the same problem

---

