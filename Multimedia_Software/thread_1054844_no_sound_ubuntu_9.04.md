---
title: "no sound ubuntu 9.04"
date: 2009-01-30
forum: Multimedia Software
---

### Post by jlo-linux on 2009-01-30
the output volume is 0.

then when you click the output tab on sound preferences no device found something like that?? 

but when i play music it is playing but no sound.

help me pls.. noob:(

---

### Post by c/Kr3t on 2009-03-28
ah ha ha, i am godly.

here's the fix chums.

firstly, go to system > admin > system testing
if that crashes, do this


```
sudo nano /etc/checkbox.d/checkbox.ini
```

And add
blacklist = backend_manager

to [checkbox/plugins]

then run the system testing again and go through all the test.
*be sure to click the test button, especially on the sound portion*
if all goes well it should set your sound to what works

then go to your pulse audio applet (if you don't have that, go to add/remove applications, sound&video, find all the pulse audio things and install those.)--see 1 

once in the applet go to 'volume control'  in the 'playback tab click on the little arrow pointing down next to the shield looking thing. then hover 'move stream' and choose one of those options. the second one worked for me, it could be different for everyone. then go to the 'output devices' tab, find your device and clicky on the little arrow that points down and select 'default'.

cheers fellas

1-once you have pulse audio things installed, go to applications > sound & video > pulse audio device chooser.  then in your tray, click on the pulse aduio applet and choose volume control, make sure everything is turned up, especially in the 'output devices' tab. close that and choose 'configure local sound server' and in the network access tab check the first 3 boxes. close and finally go to 'preferences' and check the very last box. close and you're done.

---

