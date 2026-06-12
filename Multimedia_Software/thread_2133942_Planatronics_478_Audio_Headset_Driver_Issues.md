---
title: "Planatronics 478 Audio Headset Driver Issues"
date: 2013-04-09
forum: Multimedia Software
---

### Post by ITintern on 2013-04-09
Hey everyone, 

I am currently trying to find a way to integrate lubuntu into the call center that my department works for. I have been trying to install Planatronic 478 headsets into the test computer that is running lubuntu. The USB port recognizes that a Planatronics headset is plugged in, but the computer acts as if it is not there, playing sound through the internal speakers rather than the headset. 

Personally, I think this may be a driver issue, but I am open to other suggestions. How can I manually install the driver for my headset?

---

### Post by Yellow Pasque on 2013-04-09
You have to tell your programs to output to that device (it won't switch automatically). Some useful commands are given below. The example below assumes the headset is 1,0
```
aplay -l
alsamixer
aplay -D hw:1,0 /usr/share/sounds/alsa/Front_Left.wav
```

---

