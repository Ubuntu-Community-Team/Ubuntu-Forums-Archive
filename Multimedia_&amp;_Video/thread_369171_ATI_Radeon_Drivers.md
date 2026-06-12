---
title: "ATI Radeon Drivers"
date: 2007-02-24
forum: Multimedia &amp; Video
---

### Post by Zeek00 on 2007-02-24
I'm trying to install Beryl again. I just rebuilt my machine. I know that the ATI drivers supplied by ATI are crap and I remember last time installing Beryl that there were drivers shipped with Ubuntu. I've had a look around the forum and can't find the post with the steps for installing them.

If anyone can give me a hand with a place to get the step by step of editing the xorg.conf file it would be greatly appreciated. 

Thanks,
Zeek

---

### Post by pljones on 2007-02-24
[How to install Beryl on Ubuntu/Edgy with XGL](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL)
[How to install ATI Proprietry drivers](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) (use the repo route)

I've had no luck ever getting Beryl to work.  I don't need more eyecandy, so I've given up.  If Feisty ships with it working, great!

---

### Post by Zeek00 on 2007-02-24
Thanks, 

I found out later that I had saved the URL somewhere in a text file when I rebuilt my computer. But thanks anyways. Do appreciate it.

---

### Post by dbott67 on 2007-02-24
This is how I setup the ATI drivers:

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

This is how I configured Beryl on my laptop (Dell 6400, with ATI Radeon x1400, Edgy 6.10, Broadcom wireless, etc.)

[http://www.ubuntuforums.org/showthread.php?t=274915](http://www.ubuntuforums.org/showthread.php?t=274915)

Keep in mind that one of the more recent updates to Beryl in the last few days has caused a "white" screen (apparently .14 is okay --- check the Beryl forums for more details).
[http://forum.beryl-project.org/viewtopic.php?f=36&t=4046](http://forum.beryl-project.org/viewtopic.php?f=36&t=4046)


-Dave

---

### Post by fsando on 2007-02-24
> **Zeek00 said:**
> I'm trying to install Beryl again. I just rebuilt my machine. I know that the ATI drivers supplied by ATI are crap and I remember last time installing Beryl that there were drivers shipped with Ubuntu. I've had a look around the forum and can't find the post with the steps for installing them.

If anyone can give me a hand with a place to get the step by step of editing the xorg.conf file it would be greatly appreciated. 

Thanks,
Zeek
Just installed feisty - used earlier advice to install ati-drivers:
```
sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install xorg-driver-fglrx
sudo apt-get depmod -a
sudo aticonfig force --initial
sudo aticonfig --overlay-type=Xv
```
And then edit /etc/X11/xorg.conf
```
Section "Extensions"
	Option "Composite" "Disable"
EndSection
```
Then a reboot

---

