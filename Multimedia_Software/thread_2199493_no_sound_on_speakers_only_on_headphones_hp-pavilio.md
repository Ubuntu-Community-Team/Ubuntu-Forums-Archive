---
title: "no sound on speakers only on headphones hp-pavilion-dv6"
date: 2014-01-14
forum: Multimedia Software
---

### Post by gksavina on 2014-01-14
Hello, hear is my audio issue regarding the speakers on my hp-dv6


I've installed ubuntu 12.04 LTS for almost 4 months and everything was running smoothly until one day update manager suggested some upgrades which I did like always and from the next reboot my speakers had no sound. Headphones work like always but the speakers don't. So I tried everything the guide on the sticky here suggested with no result and tried almost everything mentioned on similar threads but also silence. I thought maybe upgrade Ubuntu would solve the problem so I updated to 12.10 (I didn't do a clean install, plus the update didn't solve the prob), then I clean installed 12.04 with the problem still occuring.

I also want to mention that my speakers weren't visible at first on the output tab on the system settings but sometime during the steps of the sticky they appeared. What is strange (for me at least) is that when I play an audio file and have the pavucontrol on, playback looks like there is sound because it seems to move as the song is going louder...
Finally as far as my understanding of computers goes it seemed like some bios issue so I thought to press the shutdown button for 10secs with the battery removed, to restore bios settings or something(?), and just for some seconds I had the triple bup,bup,bup sound when Ubuntu boots and after that silence. 

aplay-l gives
```
**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic_1 [HD-Audio Generic], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```

which means that my default device is the HDMI? while I need it to be the analog for the built in speakers??

---

### Post by gksavina on 2014-01-14
double posting to add something more in this insanity..I plug the headphones just now and by turning the plug in a certain way...sound comes out of the SPEAKERS!!!would it happen if I plugged my finger there???

---

