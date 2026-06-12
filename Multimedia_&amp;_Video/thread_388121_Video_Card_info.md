---
title: "Video Card info?"
date: 2007-03-19
forum: Multimedia &amp; Video
---

### Post by Spectre5 on 2007-03-19
Is there any easy way to find out what video card I have installed..(without taking off my cover).  I am looking for something similar to dxdiag in Windows.  I am running xubuntu 6.10.

I know it is an integrated chipset (SiS), something pretty bad as it is pretty old.  The output of lspci does not mention anything about a video card/driver.

I want to get updated drivers from SiS because I have weird display problems when linux starts up and shuts down...or when I go into a virtual terminal (it goes all crazy!).

Thanks,

Scott

---

### Post by kostkon on 2007-03-19
Try reading your xorg.conf file: 

```
gedit /etc/X11/xorg.conf
```

maybe there you can find the name of the card as given by the vendor. Plus you will find which driver is used. Then you can ask for help at the forum here to solve you problem without having to install an new driver but maybe change the one that is used now.

or maybe your dmesg log or the Xorg.0.log

```
gedit /var/log/dmesg
gedit /var/log/Xorg.0.log
```

maybe you'll find something there. Try to find in *dmesg* log where the system finds the graphics card in the log text, and see what the system recognizes about the card. Or the same in the *Xorg* log.

But since that *lspci* didn't give you anything I doubt that you'll find the name of the card in these files, but you never know. Try it.

I hope I helped you somehow...

good luck

---

### Post by Spectre5 on 2007-03-19
-Deleted-

---

### Post by Spectre5 on 2007-03-19
hmmmmm.....maybe it isn't a SiS card...though I thought that is what it was before....though it has been awhile since I looked...

Here is what I get from the xorg.conf file...(other two confirmed the same things)

```

Section "Device"
   Identifier          "Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller]"
   Driver              "i810"
   BusID              "PCI:0:1:0"
EndSection

```

---

### Post by joshzam on 2008-01-05
Yes, command line is the way to go, but if you're a GUI guy, just check out System > Preferences > Hardware Information.

---

