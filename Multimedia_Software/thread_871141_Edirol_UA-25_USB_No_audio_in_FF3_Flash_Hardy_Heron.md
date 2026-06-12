---
title: "Edirol UA-25 USB No audio in FF3 Flash Hardy Heron ubuntustudio"
date: 2008-07-26
forum: Multimedia Software
---

### Post by ogopogo on 2008-07-26
Okay so I'm totally new to Ubuntu.  A trojan in the windows universe drove me here.  but man is there a lot of fiddling to do ubuntu side.  

I record music and dL'd ubuntustudio.  

I have a edirol UA-25 as my primary audio interface and my board is an PcChips A13g with realtek Audio onboard.  the realtek audio is default and i could get audio from the ua-25 in audacious and audacity playback was fine half duplex mode waws fine recorded etc.

however, in FF3 there was no audio from the Ua-25 so I plugged headphones into my onbaord soundcard and there was audio in FF3 but a constant static and crackle.  

I used the Debian? installer to install flash plugins

After trial and error I set the Sound preferences to ALSA 

Opened Pulse Audio> Volume Control> BTW Pulse only recognized the UA-25 as "USB Audio" device. Under the tabs Input devices and Output devices I right clicked to set all the USB audio devices to default.  

Under the Playback tab AdobeFlash: Flash Animation Right click> move stream >check ALSA PCM on plughw:1 (USB audio) via DMADevice 

And finally after days....FF3 Flash audio!!!!!

---

