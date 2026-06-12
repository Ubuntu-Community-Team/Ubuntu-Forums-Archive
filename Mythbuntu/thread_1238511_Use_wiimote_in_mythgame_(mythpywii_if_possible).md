---
title: "Use wiimote in mythgame (mythpywii if possible)"
date: 2009-08-12
forum: Mythbuntu
---

### Post by geekyhawkes on 2009-08-12
Is it possible to use my wiimote under mythgame / mame applications?  

I have been looking through the community help file here;

[https://help.ubuntu.com/community/MythGame](https://help.ubuntu.com/community/MythGame)

but it only covers mame with lirc and no mention of wiimote.  

I am currently using mythpywii, but if it is not possible this way could i use some other wiimote pairing to get the wiimote working with mame games?

THanks.

---

### Post by geekyhawkes on 2009-08-15
Does anyone have experiance try this, or could someone give me a steer in to how i might try and get it working?

---

### Post by doudar on 2010-01-03
In case you still haven't discovered the answer, [https://help.ubuntu.com/community/CWiiD](https://help.ubuntu.com/community/CWiiD) should help. The only downside I can see so far is that you at least would have to remap some buttons and mythpywii wouldn't be able to be run at the same time.

---

### Post by DaCrayZeeOne on 2010-01-04
As Doudar says you can use CWiiD - one way (which would involve you getting your hands dirty in code) would be to modify MythPyWii so that it disables itself when you press a particular combo and instead boots CWiiD - then do the same for CWiiD.

I wonder if MythGame is controllable over the MythFrontend telnet socket? [http://www.mythtv.org/wiki/Telnet_socket](http://www.mythtv.org/wiki/Telnet_socket) If it is then you could simply get MythPyWii to change it's keybindings when it enters MythGame and revert them when you exit... That would be cool!

I don't use MythGame so I'm not any real help here I'm afraid.

Good luck!

Benjie.

---

### Post by anthortic on 2010-05-04
I use xe emulator with mythgame, and in xe's settings i changed the keyboard mapping to match the global shortcut keys that mythpywii is associated to. But it did not work :( any advice on this angle???

obviously the frontend is loaded while the emulator runs, so i figured it would be alright.

---

