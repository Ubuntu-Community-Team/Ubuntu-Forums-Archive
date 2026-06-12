---
title: "manual setup of xserver grafic configuration"
date: 2010-12-12
forum: Multimedia Software
---

### Post by der-seemann on 2010-12-12
**Ubuntu @ Powerbook G4 400mhz** 			
 			 			 		   		 		 		Hello,
after weeks of searching the net I still have this open problem...
What's about:

I'm trying to install Ubuntu (or lubuntu) to this old Powerbook [http://en.wikipedia.org/wiki/PowerBo...m_PowerBook_G4]("http://en.wikipedia.org/wiki/PowerBook_G4#Titanium_PowerBook_G4")  with 400mhz PPC CPU.
I got it instslled and can use the terminal, but can't get the xserver running!
The problem is the display is verey sensitiv with correct resulution and  frequency, if it is not OK, it will not show enything (well, some  colors like northern lights :smile: but nothing else )
I can login using the keyboard and hear the logon sound of gnome. but of cause i cant see anything :sad:
I got no external monitor for testing.


Now the big question:
how can i setup the grafic card in the actuel version of ubuntu?
here i found some info, but it's not working anymore with 10.10
[http://wiki.ubuntuusers.de/Archiv/Ap...ok_G4_Titanium]("http://wiki.ubuntuusers.de/Archiv/Apple_Powerbook_G4_Titanium") 
here i found the following datas for the screen:
resolution: 1152x768[INDENT]horizontal
    31-46  vertikal
    50-70 
[/INDENT]Thx for your help!!!
David

---

### Post by tjones00 on 2010-12-12
If you know factory specific resolutions/settings then what you're interested in doing is creating whats called a modeline in your xorg.conf defining possible modes for the monitor/card.

Although it might not be your exact model these links should help.

[http://ubuntuforums.org/showthread.php?p=9357764](http://ubuntuforums.org/showthread.php?p=9357764)

[http://mac.linux.be/content/powerbook-g4-radeon-ly-xorgconf](http://mac.linux.be/content/powerbook-g4-radeon-ly-xorgconf)

Edit: some additional details

I assume you're using the opensource ati driver called "radeon". 

Recent Ubuntu releases no long require an xorg.conf but if you have one it will be used.

To generate an xorg.conf from the command prompt.

```
sudo Xorg -configure
```To edit the new xorg.conf from the command prompt.

```
sudo nano /etc/X11/xorg.conf
```Ctrl+O will save the new settings Ctrl+X will exit nano.

---

