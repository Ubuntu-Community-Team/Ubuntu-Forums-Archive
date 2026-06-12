---
title: "Resolution: Intel 915 with Acer 23&quot;"
date: 2010-03-09
forum: Multimedia Software
---

### Post by 61811 on 2010-03-09
[LIST]
[*]I have a Dell Dimension 4700 desktop that uses Intel's 82915G Express Chipset. 
[*]I don't have a dedicated graphics card.
[*]Bought a new Acer H235H monitor whose recommended resolution is 1920x1080.
[*]Existing settings on Ubuntu 8.04 provide 1280x1024 as the best aspect.
[*]However, that leaves two wide dark bands on either side of the screen.
[*]The monitor's WIDE MODE setting is set at ASPECT.
[*]If that setting is changed to FULL, the entire screen gets covered by the display, but the image looks stretched.
[/LIST]

Questions:
[LIST]
[*]Can something be changed in Ubuntu's setup to overcome this? How?
[*]Will installing a graphics card help? Or, will Ubuntu still need tweaking? (Prefer this method if nothing needs to be tweaked in Ubuntu.)
[/LIST]

Thank you.

---

### Post by 61811 on 2010-03-10
Well, discovered xorg.conf.

Resides under File System in folder etc/X11.

It had my older CRT monitor call-outs with obviously lower resolution settings.

Ran command *sudo dpkg-reconfigure xserver-xorg* in Terminal. 

Had to answer quite a few questions about the keyboard, but nothing else (in my case). Everything else was automatically detected and set. Even the native resolution was automatically chosen - didn't have to go to Screen Resolution under System>Preferences.

For the newly modified xorg.conf file to take effect you need to Log Out and log back again.

Simple, painless, like magic!!

---

