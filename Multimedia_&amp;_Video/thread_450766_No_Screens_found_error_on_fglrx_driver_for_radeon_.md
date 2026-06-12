---
title: "No Screens found error on fglrx driver for radeon - No Screens Found"
date: 2007-05-21
forum: Multimedia &amp; Video
---

### Post by scampisi on 2007-05-21
I have a fairly fresh install of feisty that was originally setup with an old Trident 9750 2d video card.  I am trying to replace that card with an ATI Radeon 9200se.  Once I replaced the card and rebooted, the system couldn't load the Xserver and so I ran a dpkg-reconfigure xserver-xorg and chose the ati driver.
This brought my video up and I was able to boot fine.  
I am now wanting to use the fglrx driver instead of the ATI for better graphics and so I ran 
```
sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
```
per the instrutions from a post I read.  This, I believe, installed my fglrx driver.  I then ran
dpkg-reconfigure xserver-xorg again, this time choosing the fglrx driver.

Now when I reboot, my Xserver crashes again.  My error message reads:

No matching device section for instance (BusID PCI:1:0:1) found
(EE) No Devices Detected

Fatal Server Error:  
No screens found.

I am fairly new to ubuntu, but I looked at my xorg.conf and it has my video card setup as BusID PCI:1:0:0.  my log file in var/log/Xorg.0.log shows a PCI:1:0:0 and a PCI:1:0:1.

I reverted back to the ATI driver and it shows the card as BusID PCI:1:0:0.  

I was thinking that this error message was possibly referring to the dual-head portion of my video card.  Once again, the xorg.conf that was configure for the ATI driver had no other reference than the PCI:1:0:0 and it worked fine.  Can someone explain what is happening or what I need to do?
I am not planning on using both "heads" of the video card, but if that is the problem, then I will be glad to set it up, if someone can point me the right direction.

Thanks

---

### Post by scampisi on 2007-05-24
Anybody?  I'll even settle for bad advice at this point . . .

---

### Post by mike4ubuntu on 2007-05-24
No advice, only commiseration.  I had exactly the same experience in the past hour.  I'll post again if I find a solution

---

### Post by mike4ubuntu on 2007-05-24
seems as if fglrx driver just isn't working.  If you change the Driver "fglrx" back to Driver "ati", you can atleast get back to the original drivers so that you can startup x.  I actually did a 

```

sudo dpkg-reconfigure xserver-xorg

```

and that was a pain.  All it did was revert back to original driver anyway.

Still looking for the fglrx solution.

---

### Post by jx2150 on 2007-05-25
Some more commiseration, I have the same problem. The ATI driver will allow Xserver to load, but as soon as you try fglrx, you get that error, no devices found... I have a Radeon 8500 by the way.

-jx

---

### Post by carlo_s on 2007-05-27
Check this link:

[http://www2.ati.com/drivers/linux/linux_8.35.5.html](http://www2.ati.com/drivers/linux/linux_8.35.5.html)

some cards (older that mobility radeon 9500)  are not supported anymore by ATI drivers... :(

---

### Post by grolschie on 2007-06-06
Argggh! I have an 8500DV Radeon and FGLRX used to work under Debian for me. These new drivers under Ubuntu give me same error as all you people. I will never buy another ATI product. I have had nothing but problems with their drivers in Linux and Windows.

Next I downloaded the official driver for the 8500 from ATI's website and ran the installer. Here is the result:

[INDENT][FONT="Courier New"]Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-**8.28.8**.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
 ==================================================
  ATI Technologies Linux Driver Installer/Packager 
 ==================================================
./ati-installer.sh: 165:** Syntax error**: Bad substitution
Removing temporary directory: fglrx-install[/FONT][/INDENT]

Nice!

---

