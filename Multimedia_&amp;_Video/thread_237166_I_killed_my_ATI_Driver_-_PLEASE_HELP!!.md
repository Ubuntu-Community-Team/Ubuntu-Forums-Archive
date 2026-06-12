---
title: "I killed my ATI Driver - PLEASE HELP!!"
date: 2006-08-15
forum: Multimedia &amp; Video
---

### Post by Jou Moer on 2006-08-15
I have a 500 mhz amd k6/2 processor and 448 meg ram and one of the Radeon cards as listed [here.]("http://doc.gwos.org/index.php/Open_source_radeon")  My machine is very sluggish and even XP ran better on this setup.

To cut a long story short, I found out that my processor is doing all the work instead of the graphics card and that's why my machine runs so slow.

I followed the advice on how to correct the driver by  changing the driver from 'ATI' to 'radeon' but unfortunately I changed the BusID as well as per the instruction (how I understood it in any case)

```
# Section "Device" 
Identifier "your card " 
Driver "radeon" 
BusID "PCI:1:0:0" 
EndSection
```

The problem is that now I cannot boot up so now I get the blue screen sayn that the X server has failed.

I can now only logon with the command line.

I know what the problem is.  I need to correct the /etc/X11/xorg.conf file as my BusID is actually "PCI:0:12:0" and not PCI:1:0:0

How do I do it?

I have also tried to reinstall this driver using 
```
sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
```

However I cannot download as the server times out...

any help in layman's terms (I'm a bit slow OK) greatly appreciated....

---

### Post by mordi on 2006-08-15
you can use vi or nano to edit your xorg.conf in /etc/X11. for example you can try sudo nano /etc/X11/xorg.conf or sudo vi /etc/X11/xorg.conf and change the bus id

---

### Post by Jou Moer on 2006-08-15
mordi, you are the**DADDY!**

I did the 'sudo nano /etc/X11/xorg.conf' manoeuvre, corrected the BusID and was able to logon properly and see my desktop in all its glory again!

I owe you a pint... \\:D/  :beer:

Anyway, I'm back to square one again as my machine still have a poor performance and the processor running full blast all the time :(

---

