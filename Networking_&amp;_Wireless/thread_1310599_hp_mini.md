---
title: "hp mini"
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by nathang1392 on 2009-11-01
hey guys, 
 
umm.. i recently installed 9.10 on an hp mini and everything is great, except i have absolutely no wireless. i believe that it uses a broadcom wifi card. i have been all over looking for solutions. if anyone knows a work around that is known to work, help is appreciated.

---

### Post by mbr78 on 2009-11-01
I got wireless working on my HP Mini. I searched the USB stick I used to install 9.10 for "bcmwl-kernel-source". I then right clicked the package and reinstalled it. Then after a reboot my wireless worked.

---

### Post by cen on 2009-11-01
nathang, I have the exact same issue with the exact same netbook. I can tell you the netbook version remix  distro's wireless driver works just fine, but I decided I want the classic desktop look and now I'm stuck as well.

---

### Post by cen on 2009-11-01
> **mbr78 said:**
> I got wireless working on my HP Mini. I searched the USB stick I used to install 9.10 for "bcmwl-kernel-source". I then right clicked the package and reinstalled it. Then after a reboot my wireless worked.

Thanks, I'll try that. :)

---

### Post by siglow on 2009-11-01
im on a netbook hp. i installed netbook remix and the wireless is shot. 
i tried installing bcmwl-kernel-source from the iso i used to install initially with no luck. im going to try to connect via ethernet tomorrow and maybe i can update the drivers that way. frustating

> **cen said:**
> nathang, I have the exact same issue with the exact same netbook. I can tell you the netbook version remix  distro's wireless driver works just fine, but I decided I want the classic desktop look and now I'm stuck as well.

---

### Post by cen on 2009-11-01
Thanks mbr78, worked great! :KS

---

### Post by cen on 2009-11-01
> **siglow said:**
> im on a netbook hp. i installed netbook remix and the wireless is shot. 
i tried installing bcmwl-kernel-source from the iso i used to install initially with no luck. im going to try to connect via ethernet tomorrow and maybe i can update the drivers that way. frustating

siglow, did you make a usb bootable from just an ISO? I tried that and had major issues as well. What I ended up needing to do was just burn the ISO to CD and then use that CD with the USB Startup Disc Creator to make the bootable USB. Worked a treat then. And yes, call me paranoid, but try to have a wired connection if possible as you're installing. It may help.

P.S. I'm also not noticing much difference performance-wise between the two distro versions, so I'm definitely opting for the PC/laptop version. I didn't care for typing a string of code into a terminal each time I wanted to delete files as there's no trashcan to speak of in the netbook remix that I found...

Just right click and empty for me, thanks.

---

### Post by houstonbofh on 2009-11-02
I just installed on an HP Mini 1030NR.  And I was surprised to find that it had no Ethernet port!  But I did have a USB Ethernet adapter, and that worked.  It also would not boot from a thumb drive.  That USB CD-Rom is handy too...  So, steps to success.

1) Boot from external CD and install.
2) Reboot and plug in USB Ethernet.  (Did not work right before reboot)
3) Run update manager, and patch. (The next step failed without this)
4) Reboot and run the "Hardware Drivers" application. (you may need to boot without the USB Ethernet connected)
5) Select the STA driver.
6) Reboot and use normally.

---

### Post by rocklobster01 on 2009-11-03
actually, there IS an ethernet port on the 1030nr.  I have one, and I almost didnt notice it, but it's hidden behind a rubber plug directly in front of the headphone jack.  pull the rubber plug out, and voila!  your ethernet port!!  Thanks for all the help guys, i'm still working on trying to resolve my ethernet/wifi issues...

---

