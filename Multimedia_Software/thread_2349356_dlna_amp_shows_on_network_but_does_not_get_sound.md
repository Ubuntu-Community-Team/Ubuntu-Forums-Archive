---
title: "dlna amp shows on network but does not get sound"
date: 2017-01-13
forum: Multimedia Software
---

### Post by spraguejd on 2017-01-13
My amplifier shows the PC.  Ubuntu PC shows the amplifier.  Sound from audio players (VLC, Clementine, Rhythmbox, Banshee)
does not go to amplifier and speakers when selected.  Sound settings shows the amplifier as a choice.  There is nothing esoteric about my hardware or software setup.  I have a Toshiba laptop Satellite, intel Core i7, tons of hard disk storage, Yamaha RX-A1010 amp.  The signal route is from PC by wireless to a router, thence by hardwire to HDMI input on amplifier.  My system is dual boot and I can see and send music in Windows 10.  The windows music file handling has always been terrible for me and I am trying to migrate to Ubuntu because of its clean and spare file handling.  
(Pulseaudio tells me I need to set server mode manually.  How do I do that?)

---

### Post by SeijiSensei on 2017-01-13
I'd try installing pavucontrol from the repositories ("sudo apt-get install pavucontrol").  Then open a terminal on the Ubuntu machine, type pavucontrol, and take a look at how things are configured.  You should be able to select inputs and outputs and control their volumes.  Sometimes Pulse will mute a connection for no good reason.

---

### Post by spraguejd on 2017-01-13
Peter:  I will give this a try.  Thank you.

---

