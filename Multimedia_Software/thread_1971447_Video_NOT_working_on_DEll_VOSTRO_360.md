---
title: "Video NOT working on DEll VOSTRO 360"
date: 2012-05-02
forum: Multimedia Software
---

### Post by jchiarelli on 2012-05-02
Hi There.

I have a DELL VOSTRO 360 all in one system.

I have installed a new install of Ubunto 12.04.

After the install the screen went blank after the initial GRUB boot.

No text before the xserver starting.

So I edited /etc/default/grub and changed

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to

GRUB_CMDLINE_LINUX_DEFAULT="quiet nomodeset"

Upon doing this, now it comes up but with resolution of 1280x1024 laptop.

The processor is a Intel® Core™ i3-2100 CPU @ 3.10GHz × 4 
and the graphics state VESA: Intel®Sandybridge Desktop Graphic

 lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)


Any help would be appreciated. Ive searched but the one or two posts have no solution.

---

### Post by Matt_Fussell on 2012-06-15
We had a few machines ordered late last year of this configuration, and the issue is the optimus video setup on linux, which is a mess at the moment.  Since these machines are effectively laptops adapted to be desktops, they got the 'economy' treatment with regards to parts.

Keep watching and googling for solutions to this issue, but don't be surprised if you're living in Windows for a while.

---

### Post by srinet2 on 2012-07-19
go to the following link 
hope it will help 
[www.grputland.com/2012/05/](www.grputland.com/2012/05/)**linux**-on-**dell**-**vostro**-**360**-use.html

---

