---
title: "PCI-G31 - Railink RT61 Chipset disconnected"
date: 2011-03-02
forum: Networking &amp; Wireless
---

### Post by atomicben on 2011-03-02
I bought  the ASUS PCI-G31 - with Railink RT61 Chipset because I hear  that it is well supported by Ubuntu after 2.6.24 and with aircrack-ng  but I'm struggling to get ubuntu to do anything with it but tell me it's  disconnected.  I'm curently running kernel  2.6.32-29-generic (I tried  going back to 2.6.32-28-generic too but nothing is different)

I installed the card - it's listed in Network Manager but says  disconnected.  Nothing i do changes that.  I've tried > iwconfig  wlan2 power off as some have suggested - no change.

my lsmod tells me that the rt61pci modules are running.

my lspci id's the card just fine.

I've installed the latest greatest compat-wireless package - no change.

I've tried getting the latest drivers from railink but i get errors when trying to complile.

I've tried the enhanced legacy drivers provided by serialmoney and i get errors when i'm trying to compile.

dmesg | grep rt61 has a bunch of input/output errors but I'm not at my  linuxbox right now or I'd paste them.  I'll do that when I get home if  required.

So now I'm just banging my head against the wall.  Every site I find seems to indicate that this card is very well supported.

Can anyone help with the disconnected problem?
Is anyone using this care with Lucid or Maverick? And what did you have to do?
SHould I be using the compat-wireless rt61pci or the speedmonkey rt61.ko  (which I can't compile because I can rarely get anything to compile -  compatwireless compiled for me though - YAY)

Yes I have the latest build-essentials and my header files.

I should also add that all this modprobe, lsmod, rmmod, lspci, lshw, dmesg, grep stuff is new to me as I'm a ubuntu n00b.  All of the things I've tried have come from a lot of forum searching not my linux knowlege so I do need some spoon feeding.

---

### Post by atomicben on 2011-03-02
ignore post # 2 (this one)

---

### Post by atomicben on 2011-03-03
update:

I decided to wipe my system and install maverick.  I was installing from a USB start up disk.  

Maverick install would freeze during that start up process with this card installed.  It would get to that weird fancy purple/pink looking screen that is just before the login screen and freeze.  Not a hard freeze - the mouse would move and the caps lock worked but it wouldn't recover.  Once I removed the card the install worked well.  

There is good news though.  The reason I bought the pci-g31 is because I couldn't get my DWL-G510 (Atheros Chipset: ath5k) working either.  Well, I slapped that bad boy in during the maverick install and it was detected and installed!  I was floored!

the g510 is still causing some issues because I can connect to my wireless network but after a few hours i noticed that the connection speed was 1mb/s.  i don't know how/why it slowed down to that because I also have a wired connection so I didn't notice it chugging but I'm going to try and fight that battle instead of trying this pci-g31.

This thread can be closed.

---

