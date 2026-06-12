---
title: "PVR 150 Remote Issues"
date: 2008-01-24
forum: Mythbuntu
---

### Post by snowsubi on 2008-01-24
Hi community. I will first apologize for being a noob and having to ask questions. I finally committed to removing windows from my life and its great! I have a homebrew pvr that I have been working on and have an issue with the PVR 150 remote that came with it. Its the Hauppauge remote with the 4 colored buttons on the bottom. My setup is a p4 2.8ghz, 120 gb HDD, 1gb DDR, Nvidia card and PVR 150 capture card. I have Mythbuntu working great and can view and record tv. The remote is having some issues though. Mainly a lot of the buttons simply don't do anything and the channel up and down acts as jump back and forth on the live recording of tv. It is quite annoying and I would like to have that work properly, as well as use all the buttons of the remote if possible. From what i have been learning about Ubuntu, a lot of this stuff is possible so hope you can all help me out. Again, I am very new and have been able to get mythbuntu installed but am by no means competent.

---

### Post by haggiscanvas on 2008-01-28
Hey hope you have some better luck...

There are plenty of places to get a lircrc file out there.  It is one of the files lirc uses to interpret the commands sent from the remote to the computer.  Here is a link to one I have borrowed from before...
[http://wilsonet.com/mythtv/lircrc-haupgrey-g3.txt]("http://wilsonet.com/mythtv/lircrc-haupgrey-g3.txt")

Also you might want to look here for more info...

[https://help.ubuntu.com/community/InstallLirc/Gutsy]("https://help.ubuntu.com/community/InstallLirc/Gutsy")

Another place to look...

[https://help.ubuntu.com/community/InstallLirc/Feisty]("https://help.ubuntu.com/community/InstallLirc/Feisty")

It took me some time to get it going myself, I hope all goes well with your endeavor.

---

### Post by stdPikachu on 2008-01-28
Rolling your own remote config is pretty easy if you feel up to it, I've done a sample on creating your own [here](http://ubuntuforums.org/showthread.php?t=678835). You can create your own lircd.conf or use a provided one and edit the .lircrc file to suit your needs.

---

