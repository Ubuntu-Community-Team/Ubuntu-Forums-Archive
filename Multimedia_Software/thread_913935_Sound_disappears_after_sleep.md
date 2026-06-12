---
title: "Sound disappears after sleep"
date: 2008-09-08
forum: Multimedia Software
---

### Post by jasuus on 2008-09-08
Hello, im running 8.04 hardy on a AMD 64 5600+. I just installed last week and i am a relative newbie to all this.  

My problem is such: everything is working well with the exception of sound.  I get all sound for you tube, games, environment, etc when i first start up, but then if the machine goes to sleep and i awake it, all sound is lost.  Everything else works fine just without sound. The only way i can figure out to restore sounds is a complete reboot - log out and log back in does not solve the issue. 

Any ideas?

james

---

### Post by Zorael on 2008-09-08
What is the terminal output of the following command?
```
$ aplay -l
```

---

### Post by jasuus on 2008-09-08
jasuus@baylay:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by JohnJackson on 2008-09-16
Same problem here. I wonder if this is an NVidia issue?

> 
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Hardy 64-bit

---

### Post by -moro- on 2008-11-02
Also have this problem in Intrepid x86
aplay -l
**** &#1057;&#1087;&#1080;&#1089;&#1086;&#1082; PLAYBACK &#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074; ****
&#1082;&#1072;&#1088;&#1090;&#1072; 0: Intel [HDA Intel], &#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; 0: ALC268 Analog [ALC268 Analog]
  &#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1072;: 0/1
  &#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; &#8470;0: subdevice #0
&#1082;&#1072;&#1088;&#1090;&#1072; 0: Intel [HDA Intel], &#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; 1: ALC268 Digital [ALC268 Digital]
  &#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1072;: 1/1
  &#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; &#8470;0: subdevice #0

---

### Post by lenu on 2009-01-26
for me, the sound is usually lost after the computer has been turned on for a long time (days?), or, sometimes the sound disappears after i've used amarok 2 simultaneously with firefox/youtube. a complete reboot is the only thing that helps.

[INDENT]~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[/INDENT]

---

### Post by GB_Joe on 2009-09-10
I know this thread is ancient... but I'm getting the same symptoms on 9.04 with an IBM T42 laptop. No one seems to have replied with any clues, so I thought it'd be worth a new shout... I get this output:

**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Would love to sort it out, I use sleep mode a fair bit... although the battery seems to flatten shockingly quickly, but that's another story!

---

### Post by GB_Joe on 2009-09-10
Heh heh heh...

I've just opened my full volume settings panel and found everything else but the Master was turned down to zero AND muted.

](*,)

Still, it seems suspiciously like this must've happened by itself - I wouldn't have done it myself, so whether it was a bug coming out of sleep or not I can't say.

I guess I'll keep an eye on this and post if it happens again, just in case anyone else has the same problem...

---

### Post by viant on 2011-05-30
I have the same problem with ubuntu 11.04
The sounds disappear in flash in chrome after sleep

---

