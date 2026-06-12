---
title: "no sound in 8.10"
date: 2009-03-22
forum: Multimedia Software
---

### Post by supertappy on 2009-03-22
Hi,

I'm new to linux and have just installed 8.10 on an AMD system.

The motherboard is a GA-MA790X-DS4

I'm using the sound off the mother board, not a sound card.

I can't get any sound happening though. It's a dual boot machine, in xp sound is fine.

Does ubuntu support sound on AMD processors?

The same install on my wife's intel laptop and sound works fine.

any suggestions?

---

### Post by penguinguy on 2009-03-23
I'm having the exact same problem with my onboard sound, which XP has no trouble with. Did it simply playing sound stop randomly, or did you upgrade Ubuntu recently?

---

### Post by supertappy on 2009-03-23
I'm a new ubuntu user so this is a new installation. Sound has never worked.

jt

---

### Post by redenex on 2009-03-23
I am not a new ubuntu user, but a new 64 bit user (4 days). and no, the sound have never worked on my 64 bit either! Been running helter skelter to make this work.

---

### Post by Therion on 2009-03-23
For starters, open a Terminal and copy and paste the following into it:```
aplay -l
```
Post the output here, please.

---

### Post by redenex on 2009-03-23
Here is mine:

> root@AbleBlue:/home/teddy# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC268 Digital [ALC268 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
root@AbleBlue:/home/teddy# 


---

### Post by Therion on 2009-03-23
> **redenex said:**
> Here is mine:
Okay, good.  Ubuntu at least recognizes you have an onboard-audio chipset.

Back to the Terminal:```
alsamixer
```
Use your arrow keys to move around.  You'll several channels listed.  Is your "Master" channel "Muted"?  
You can tell that it is if there is an **MM** underneath it instead of a number.

---

### Post by redenex on 2009-03-23
[IMG]http://img11.imageshack.us/img11/9255/screenshotakd.png[/IMG]

[IMG]http://img11.imageshack.us/img11/5543/screenshot1vqr.png[/IMG]

[IMG]http://img11.imageshack.us/img11/3916/screenshot2x.png[/IMG]

I guess it is all set right. I dont see anything muted as yet.

---

### Post by Therion on 2009-03-23
Okay, we've eliminated most of the easy solutions.  See this thread for further assistance: 

[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

---

### Post by redenex on 2009-03-23
Will check it out. But what is surprising is that the sound played for a brief period just now. When I opened a video which my friend send me, flashplayer) I heard sound, but after that it is gone again. Will do some research I believe.

---

### Post by markbuntu on 2009-03-24
Try this first

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

If you still have problems go here


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by supertappy on 2009-03-26
> **Therion said:**
> For starters, open a Terminal and copy and paste the following into it:```
aplay -l
```
Post the output here, please.

here is the result

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC885 Analog [ALC885 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC885 Digital [ALC885 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by supertappy on 2009-10-21
I upgraded to Ubuntu 9.04 and sound now works fine

---

