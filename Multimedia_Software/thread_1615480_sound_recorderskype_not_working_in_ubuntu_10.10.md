---
title: "sound recorder/skype not working in ubuntu 10.10"
date: 2010-11-07
forum: Multimedia Software
---

### Post by anilsarwal on 2010-11-07
I love new Ubuntu 10.10. However, despite my best efforts, I cannot make sound recorder/skype work. That is, microphone would not simply record any sound. My mother board is Asus M2N68-AM. Can anyone help?

---

### Post by mrhhug on 2011-03-09
I had to ```
sudo killall pulseaudio
``` then system > preferences > sound

worked from there, if your unplugging and replugging a usb mic / webcam , i think there is a bug, cause i never had this problem (using Maverick Meerkat upgraded from lucid) until i decided to buy a USB extension and run my printer USB cable to my rear panel and then realised i didnt have enough ports..... blah blah ... sorry to bore you with my personal details...

try that , seemed to work for me!

---

### Post by prshah on 2011-03-10
> **anilsarwal said:**
> I cannot make sound recorder/skype work. That is, microphone would not simply record any sound.

Click the volume control applet, and choose "Sound preferences"; open the "Hardware" tab and ensure that you have atleast one input device (may be combined as a singe input/output device). Then, click the "Input" tab, and "choose" the relevant input device. Unmute the input and adjust volume until the sound meter registers sound.

if you run into problem, please post back with screenshot of the Sound preferences window, Input tab.

---

