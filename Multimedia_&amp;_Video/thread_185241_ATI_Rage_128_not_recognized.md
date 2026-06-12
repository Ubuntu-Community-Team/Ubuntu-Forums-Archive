---
title: "ATI Rage 128 not recognized"
date: 2006-05-31
forum: Multimedia &amp; Video
---

### Post by GreenLight on 2006-05-31
I have installed three of the pre-release versions, and none of them could set up X for me. Is this a known issue with an ATI Rage 128?

---

### Post by t[h]inker on 2006-05-31
Hm, I have the same graphics adapter as You and never had a problem (trying pre-releases as live CD)...

What can it be? Maybe a motherboard issue or something?

---

### Post by GreenLight on 2006-05-31
[QUOTE='t[h]inker']Hm, I have the same graphics adapter as You and never had a problem (trying pre-releases as live CD)...

What can it be? Maybe a motherboard issue or something?[/QUOTE]
Could you post your xorg.conf file? Maybe if I hand-code one, I can get it to work.

---

### Post by t[h]inker on 2006-05-31
What does your xorg.conf looks like? Please, post it here, so anybody can check it and give you a hint.

(I would be glad to post my, but I'm not on my Ubuntu box for now :( )

---

### Post by GreenLight on 2006-05-31
[QUOTE='t[h]inker']What does your xorg.conf looks like? Please, post it here, so anybody can check it and give you a hint.

(I would be glad to post my, but I'm not on my Ubuntu box for now :( )[/QUOTE]
The config file was basically empty. I wiped the box with a Mandriva 2006 install, to see if there was some problem with my computer. Mandriva is working perfectly, as did Fedora Core 5.

---

### Post by Sputnik_RU on 2006-05-31
I also have an "ATI Rage 128" and no problems. Did you try to reconfigure your x.org configuration?

sudo dpkg -reconfigure xserver-xorg

---

### Post by GreenLight on 2006-05-31
[QUOTE=Sputnik_RU]I also have an "ATI Rage 128" and no problems. Did you try to reconfigure your x.org configuration?

sudo dpkg -reconfigure xserver-xorg[/QUOTE]
I will try this if I have any problems with the release version. Thanks!

---

### Post by t[h]inker on 2006-05-31
[QUOTE=Sputnik_RU]I also have an "ATI Rage 128" and no problems. Did you try to reconfigure your x.org configuration?

sudo dpkg -reconfigure xserver-xorg[/QUOTE]

Well, it could help, but I'm pretty sure that's *dpkg-reconfigure*, NOT *dpkg[COLOR="Red"]**_**[/COLOR]-reconfigure*. Simply ommit the space character. :D

---

### Post by GreenLight on 2006-06-02
I had two major issues that cause Dapper to have severe problems.
My computer is a Dell PowerEdge SC420, standard except for the addition of two PCI cards:
1) Promise UltraATA 100 IDE card
2) ATI Rage 128 card
First major issue, Dapper WILL NOT install properly if there are any drives connected to the Promise card. It must be writing boot information to one of these drives, no matter what I tel lthe installer (I want to boot off of the built-in SATA controller).
Second, Dapper apparently finds the integrated Intel graphics chip, even though it is turned off in the BIOS, and tries to initialize the ATI card as though it were the Intel card. I had to fiddle with the xorg.conf file for a long time to get things to work correctly.

---

