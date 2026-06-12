---
title: "anyone successful installing fglrx for ati on edgy?"
date: 2006-10-27
forum: Multimedia &amp; Video
---

### Post by bionnaki on 2006-10-27
I am running edgy and have a raedon 9600 card that worked great with fglrx. I always followed these instructions before:

> 
sudo apt-get install xorg-driver-fglrx
sudo apt-get install fglrx-control
sudo nano /etc/X11/xorg.conf


and then replace "ati" with "fglrx" under devices.

Now, using edgy, I have tried this method and receive this when I run *fglrxinfo* after reboot:

> 
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)


Anyone know what I should do next? I am at a loss.

here is the output of **dmesg | grep fglrx**

> [17179596.560000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[17179596.564000] [fglrx] Maximum main memory to use for locked dma buffers: 929 MBytes.
[17179596.564000] [fglrx] module loaded - fglrx 8.28.8 [Aug 17 2006] on minor 0


and the /var/log/Xorg.0.log is attached to this thread as log.txt

I greatly appreciate your help.

---

### Post by bionnaki on 2006-10-27
the log.txt can be found here: removed

---

### Post by yummy on 2006-10-27
Hello,

The fact is that edgy is aiglx compatible. Hence this cause such issue with ATI GPU.
SO for now to use fglrx you have to edit the xorg.conf to add at the end :
Section "Extensions"
	Option "Composite" "disable"
EndSection

Then restart X.

PS: so if you want to use compiz/beryl this will be done thru Xgl and not aiglx for ati cards.

Regards, yummy.

---

### Post by bionnaki on 2006-10-27
worked perfectly.
that was easy. thanks.

---

### Post by atlas95 on 2006-10-27
I have install it and it works BUT tty 1, 2, 3 don't work, i don't see terminal (black screen) but a multicolor screen :/

Could you help me please?

my graphic card is an ati express X1600 and I have install beryl and xgl too :)

Thanks :)

---

### Post by RudolfMDLT on 2006-10-28
Yummy, Thanks! I got the driver loaded but my fps is down from 2000 in Dapper to 245 in Edgy? The gears in glxgears spin better than when I was using mesa but has a higher fps?

Could you please expand on why we need to add 

Section "Extensions"
Option "Composite" "disable"
EndSection

to the end and why the GPU is not compatible? SOrry, I'm a bit of a noob but I really would like to understand what has changed in Edgy from Dapper concerning the display system?

Thank you!

Rudolf

---

### Post by medeshago on 2006-10-29
It doesn't works for me. When i add:
Section "Extensions"
Option "Composite" "disable"
EndSection
to xorg.conf, X won't start. It says that it couldn't find a screen...

---

### Post by Blixter on 2006-10-29
I found this guide and it's working for me:

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

---

### Post by staib on 2006-10-29
Yep - and it's just worked for me too :KS

---

### Post by pony-tail on 2006-10-29
For me it "worked" (if you can call disabling half of the cards function working ) on one machine (32bit 9800XT-AGP) but not another (64bit X850XT-pe PCI-E ).
Either way - no XGL , Compiz or Beryl because no compositing !
Breaking one thing to fix another is not a fix !

---

### Post by abahgat on 2006-10-30
I'm afraid we'll have to wait until Ati will be able to support the composite extension with their proprietary drivers.
Even with composite enabled, I didn't have DRI support, and therefore I couldn't run XGL, Compiz or Beryl anyway.

The only other option, is to find a different workaround, but I didn't manage to find anything else, so far...

---

### Post by traneHead on 2006-10-30
Just want to add that the instructions at [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)
fixed it for me on a IBM ThinkPad (Lenovo) T60.
Thanks a bunch to the author(s)!!

---

