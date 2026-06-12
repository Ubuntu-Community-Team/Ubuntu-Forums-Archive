---
title: "Dual Monitor Problems with ATI Graphics Card"
date: 2009-07-18
forum: Multimedia Software
---

### Post by checho4 on 2009-07-18
I'm using 64-bit Kubuntu 9.04 on my Dell Inspiron 1501.  I'm trying to get the dual monitor to work, but have no idea where to start.  "Display Settings" shows 2 monitors: VGA-0 and LVDS (see attached picture).  When identifying the outputs, both names show up one on top of the other.  The external monitor just mirrors the laptop monitor.

How would I go about getting a dual monitor setup going?

---

### Post by ShepHeard on 2009-08-01
Have you got anywhere with this? It was easy in Gnome...

---

### Post by gunksta on 2009-08-03
ShepHeard, what graphics card are you using?

---

### Post by markbuntu on 2009-08-03
The only way I got dual monitors to work in KDE was with the Catalyst Control Center that comes with the driver from ati. 

The KDE display manager seems broken for setting up two monitors. There is some bug reports on this at launchpad.

---

### Post by checho4 on 2009-08-03
I haven't gotten anywhere on this yet. I was really hoping not to, but I'll try setting up the ATI Catalyst Control Center and see what I can do with that.

---

### Post by gunksta on 2009-08-04
You can also just edit your xorg file by hand, but using the Catalyst Control Center is possibly easier and certainly will feel safer if you've never tweaked an xorg file manually before.

I assume you are using an ATI card since you are talking about Catalyst. At the risk of sounding pedantic, this will only work if you are running the proprietary driver.

---

### Post by checho4 on 2009-08-04
Gunksta: that was the reason I had said I was really hoping not to. I'll actually try editing the xorg first - I didn't realize that controlled the dual output as well.

---

### Post by ShepHeard on 2009-08-04
Hi,

Yeah - I'm running an ATI too - Radeon Xpress, or something similar.

I saw about editing the xorg file. Fine, if you always use two monitors, but this is for my laptop, and I only use the second monitor when I'm at home. Otherwise it's a real pain having to edit the file each time.

How would one install the proprietary drivers? 

Cheers,

S

---

### Post by checho4 on 2009-08-04
Here's the guide to installing the proprietary fglrx driver.

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Instructions%20for%20Ubuntu%209.04%20%28Jaunty%29](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Instructions%20for%20Ubuntu%209.04%20%28Jaunty%29)

---

### Post by ShepHeard on 2009-08-12
Thanks for the link, but I'm not sure it's much help... It talks about enabling the restricted drivers:

> Enable the accelerated ATI graphics driver in the 'Hardware Drivers' (System->Hardware drivers), then do:

```
sudo dpkg-reconfigure -phigh linux-restricted-modules-`uname -r`
sudo insmod /lib/modules/`uname -r`/volatile/fglrx.ko
```

Log out and log in. 

but I do not see this option. 

Then for the ati drivers, the details are for 8.04. Though I imagine this may work, I am understandably dubious. But, essentailly - are we saying that I should install the ati driversm then install Catalyst Control centre? 

I know this sounds odd, and probably naive, but can't I install the Gnome display controller??

---

### Post by ShepHeard on 2009-08-12
PS: lspci:

01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]

---

### Post by gunksta on 2009-08-12
You can stop wasting your time trying to get the  proprietary driver working with a Radeon Xpress 200M. ATI/AMD dropped support for older cards, such as yours. I happen to have one of these cards. You're going to need to use xrandr to set this up.

Here's one link I found quickly:

[http://www.jejik.com/articles/2008/10/setting_up_dual_monitors_system-wide_with_xrandr_on_debian_lenny/](http://www.jejik.com/articles/2008/10/setting_up_dual_monitors_system-wide_with_xrandr_on_debian_lenny/)

and another discussing how Gnome 2.24 does this, but I don't think it's what you want because I think it is essentially what KDE does, with slightly more intuitive graphics:

[http://library.gnome.org/misc/release-notes/2.24/#rnusers.xrandr](http://library.gnome.org/misc/release-notes/2.24/#rnusers.xrandr)

---

### Post by stancole on 2009-08-31
I have this same issue with an Intel Graphics device.  The problem is that I am new to Linux and do not yet know how to change the xorg.conf to display the dual monitors properly.  I installed the latest intel driver and still the monitors are identifying themselves as the same device.  If anyone can give me some insight that would be awesome.

---

### Post by dru3692 on 2009-09-03
Problems with mine as well. ATI catalyst installed from Hardware Drivers GUI under System menu. ATI catalyst control that I am using right now was recommended from driver identification by Ubuntu. Mostly good but slight problem as you will see from the images attached here. Mind you, I have 5 apps open right now and none on the taskbar.

---

