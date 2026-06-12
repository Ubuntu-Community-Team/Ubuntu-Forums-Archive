---
title: "M-AUdio Oxygen 8 v2 midi keyboard installation (LMMS and otherwise) HALP!"
date: 2010-10-22
forum: Multimedia Software
---

### Post by kennethfrank on 2010-10-22
Hey all,

I'm very new to the Linux OS stuff and I'm trying to get my M-Audio Oxyen 8 to work on Ubuntu, specifically for LMMS. 

The keyboard is connected via USB and I installed the MidiSport driver which claims to be compatible with Oxygen. Still the keyboard doesn't show up in the Ubuntu Sound Preferences Input menu.
 
In LMMS I enable MINI input in the default presets, open the input settings nothing comes up. I try to set the MIDI input settings but they won't save to anything other than "DUMMY (No MIDI output).

Essentially Ubuntu doesn't seem to recognize the keyboard at all WHYYYY :< Any help would be greatly appreciated!

Thanks,
Kenny

---

### Post by kennethfrank on 2010-10-23
bump :<

---

### Post by cchhrriiss121212 on 2010-10-23
Do you see it when you put lsusb into a terminal window?

---

### Post by kennethfrank on 2010-10-23
yeah it shows up there, so that's something i guess?

---

### Post by cchhrriiss121212 on 2010-10-24
[http://ricardocabello.com/blog/post/533](http://ricardocabello.com/blog/post/533)

---

### Post by kennethfrank on 2010-10-24
i keep getting a broken pipe error message... this shouldn't be this difficult :[ !

---

### Post by cchhrriiss121212 on 2010-10-24
Did you just copy and paste the command from that link? I read it again and one step that is not made clear is that you need to specify the correct bus, depending on your lsusb output. 

So because his lsusb output shows: Bus **005** Device **005**: ID 0763:1014 Midiman

He uses this command: sudo fxload -D /dev/bus/usb/**005**/**005** -s /usr/share/usb/maudio/MidiSportLoader.ihx -I /usr/share/usb/maudio/MidiSportKS.ihx

Bold text is mine to show what you need to change.

---

### Post by kennethfrank on 2010-10-24
yeah, i tried putting the right bus/device numbers based on the lsusb info but it gives me that 'broken pipe' error message :[ thanks for trying to help, it might be a lost cause.

---

### Post by cchhrriiss121212 on 2010-10-25
Try using a different port, and also unplug any other devices that use USB. Then try fxload again without the -s command like this:
sudo fxload -D /dev/bus/usb/**005**/**005** -I /usr/share/usb/maudio/MidiSportKS.ihx

---

### Post by Jonatello on 2011-06-24
i found this thread while googling "m-audio oxygen ubuntu lmms"...i too have an oxygen-8 and trying to get it to work. 

i tried the above advice, mine shows up 007, but when i follow these instructions (which i also found on a couple other pages), i get the following message:



No such file or directory : /dev/bus/usb/007/007



...i'm using 11.04...maybe this method is outdated?

---

### Post by 33Nicolas on 2013-04-09
ditto here!

---

### Post by wildmanne39 on 2013-04-09
Thread closed. Please do not post in old threads.

---

