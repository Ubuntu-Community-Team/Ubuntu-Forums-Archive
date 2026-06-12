---
title: "Bluetooth Headset in Gutsy"
date: 2007-12-23
forum: Multimedia &amp; Video
---

### Post by gutsy_psu on 2007-12-23
ok so I know there's numerous similar threads, from which i've combined elements, but my problem seems very unique.  I have no problem with the pariing, the device shows up  properly under both skype, and via the volume control (I have a BT headset option for change device).  My problem is I get no sounds when trying to use the headset.  The sound does not come through the system (as it shouldn't)( but it's not reaching my headset either. When I try from the command line test, here is the result:

root@steven-laptop:/home/steven# aplay -B 1000000 -D plughw:Headset /usr/share/sounds/login.wav
aplay: main:545: audio open error: Device or resource busy


I have all the packages installed, and am using the gutsy provided bluetooth analyzer combined with the Bluetooth Headset Manager GUI.  any help greatly appreciated!

---

### Post by gutsy_psu on 2007-12-24
anyone?  bump:confused::confused:

---

### Post by gutsy_psu on 2007-12-24
anyone?

---

### Post by gutsy_psu on 2007-12-25
no one has any ideaS?

---

### Post by gutsy_psu on 2007-12-26
buuump

---

### Post by oneiota on 2007-12-27
I recall similar error messages when trying to set up my bt headset.  I did eventually get it working in Gutsy and I recall that 'gbtsco' was one of the things that got it working.   It came from [http://www.stgraber.org/2007/05/20/gbtsco-already-release-02/](http://www.stgraber.org/2007/05/20/gbtsco-already-release-02/), a link I found in a thread somewhere.
[I]
[Unfortunately, now I've reinstalled Ubuntu and I see I have plenty of audio problems and will have to start from the beginning again.]  [/I]

I didn't keep notes on exactly what I did the first time but I will this time around!

---

