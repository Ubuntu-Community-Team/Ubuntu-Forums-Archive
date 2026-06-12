---
title: "No Sound"
date: 2007-07-21
forum: Multimedia &amp; Video
---

### Post by coolth3 on 2007-07-21
Hello.

I am new to Linux  , but decided to finally install Ubuntu Feisty Fawn on my laptop.

Everything is working very well, except that I noticed that I have no sound.

Ubuntu detects my sound card, and the sound is not muted either.  After aplay -l  the sound card shows up as:

**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I don't know what else to do.

Any kind of help will be appreciated, thank you for your time.

---

### Post by lisati on 2007-07-21
Sometimes all that is needed is an update to the sound drivers. You might want to start by checking to see if update manager recommends any updates - if it does it will usually show an orange notification on your screen, otherwise you can use "update manager" on the "System"->"administration" menu.

---

### Post by coolth3 on 2007-07-21
I checked the update manager and it informs me that my system is up to date, but still no sound.  Thanks for your help though :)

---

### Post by fredj on 2007-07-22
Open the Alsa mixer (double click on the speaker icon in the system tray). Go to the Edit->Preferences menu
and add all the necessary volume controls and switches for both play and record. Make sure they are 
not muted and that suitable volume levels are set (some experimenting will be necessary here - you can
always remove controls that you don't need later). If this doesn't work open a terminal and type
sudo cat /proc/asound/card0/codec\#*
Then post the output from that here.

---

