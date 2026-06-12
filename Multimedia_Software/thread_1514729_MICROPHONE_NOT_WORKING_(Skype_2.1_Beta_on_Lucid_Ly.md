---
title: "MICROPHONE NOT WORKING (Skype 2.1 Beta on Lucid Lynx 10.04 32Bit)"
date: 2010-06-21
forum: Multimedia Software
---

### Post by gehe05 on 2010-06-21
Hey people,

I am a new user but have tried my way around Ubuntu a couple of times by reading forums, etc. 

I recently upgraded to Lucid Lynx 10.04 Desktop Edition on my Gateway Noteboook EC1803u. It runs Intel Core 2 Solo and has the Intel G45 chipset.

I was pondering on skype and I noticed that everything worked except my audio inputs. Upon reading various sites, I got it to work in my sound recorder. I tried killing Pulse Audio and making ALSA my default audio driver but that horribly failed with the sound output remaining the same when changed. 

I also see that my microphone works perfectly well with the GNOME-Sound recorder.

The sound card is a Realtek ALC269.

I'm in serious need of help as I have University Skype interviews in the coming week and need to overcome this issue. 

Thanks :)

---

### Post by Bucky Ball on 2010-06-21
Applications->Sound and Video->Pulse Audio Device Chooser. Click the icon in the taskbar and 'Volume control'. 

Open Skype and run a test call. When the playback streams appear in the playback streams window, right click on the mic and 'Move Stream ..,' Move it to the right device.

This fix took me forever to figure out.

---

### Post by resthavener on 2010-06-24
Hi - worked for me after much research
1. Install (maybe) and run padevchooser from sound and video menu
2. Find it in top tray (good gotcha - bonus for newb confusion team)
3.left click and select volume control
4. Select recording
5. Make skype test call
6.  Skype should show up in padevchooser (click on it) and there is a box bottom right to choose your mike.  Set to internal card in my case which wasn't much use for my usb mike (despite this being default device). Miracle cure and saves me buying my wife windows (where, o geeks, these * things just work)

---

