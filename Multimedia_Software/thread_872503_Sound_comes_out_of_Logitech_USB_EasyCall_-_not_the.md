---
title: "Sound comes out of Logitech USB EasyCall - not the Soundcard!"
date: 2008-07-28
forum: Multimedia Software
---

### Post by sputnikkk on 2008-07-28
Sound card is a SBLive! PCI

I can get the test sounds out of the silly Logitech Easy Call Desktop Voip speaker phone thingie - not out of the soundcard and speaker set connected to it.

How to make Alsa play nice and use the Sound Card v. USB sound hardware of logitech?

What outputs would you all like to see?

linux newb here ...

much appreciated in advance.

---

### Post by nikgare on 2008-07-28
Have a look in **System->Prefences->Multimedia Systsems Selector** and see if you can change the outputs

---

### Post by zwaardmeester on 2008-07-28
Or: System->Preferences->Sound and change "Default Mixer Track" to the creative card. And put the "Sound Playback" things to Alsa or Multichannel. Good luck!

---

### Post by sputnikkk on 2008-07-28
Thanks guys/gals ...

Tried all that - redid the settings everywhich way  - did the ol reboot in between several modifications to the settings, and still - I get test signal ONLY when they they are set to the Pulse Audio Server - which is the new over riding sound server for Hardy 8.04 ???

I'd like to use system software that takes advantage of the soundcards hardware and capabilities vs. Pulse Audio server software.

Any more thoughts?

---

### Post by erikthedrink on 2009-09-08
I've got logitech usb speakers too.  In Xubuntu, go to Applications, then Accessories, then Terminal.  In Terminal, type

[FONT=Georgia][SIZE=4]asoundconf set-default-card 1[/SIZE][/FONT]

Then close and re-open your browser (Mozilla Firefox) or restart your system.
:P
Note, if you unplug your usb speakers, your laptop speakers will take over.  In order to re-establish contact with the usb speakers, you will need to (plug them back in) restart the system. If this doesn't work, try substituting "2" for the "1"

---

