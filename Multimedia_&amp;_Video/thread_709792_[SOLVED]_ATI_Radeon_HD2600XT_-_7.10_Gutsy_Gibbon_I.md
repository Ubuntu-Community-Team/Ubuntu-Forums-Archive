---
title: "[SOLVED] ATI Radeon HD2600XT - 7.10 Gutsy Gibbon Install Help"
date: 2008-02-27
forum: Multimedia &amp; Video
---

### Post by sidprak on 2008-02-27
I have a machine with the following specs:
Core 2 Quad Q6600 2.4GHz
4GB DDR2-800 RAM
2x160GB HDD in RAID 0
ATi Radeon HD2600XT Graphics Card PCIexpress

I have managed to install Ubuntu Gutsy onto one of the partitions on my hard drive, and am currently dual booting with XP.
I am experiencing a problem with the graphics card.  It doesn't have a driver installed and I have tried many how to's and guides to get it installed with no success.  I have also used the guide provided by ATi:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

and when I try rebooting my computer after following Method 1, the X server has remained unchanged.  When I try to follow the steps under "Configure the Driver", and run 

```

sudo aticonfig --initial

```

I get the following error:
```
Warning: Could not find configuration file
Please copy configuration file template to /etc/X11
```

When I check the /etc/X11 directory, I find that there is no xorg.conf configuration file.
Can someone please help me get the driver installed?
Thanks!

---

### Post by sidprak on 2008-02-28
I got it working by using envy!
And I had to change my monitor and then change the resolution to 1680x1050 to get that to work.

---

