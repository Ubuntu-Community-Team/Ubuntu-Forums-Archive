---
title: "LinkSys WMP54GS"
date: 2005-12-30
forum: Networking &amp; Wireless
---

### Post by mauroj on 2005-12-30
I'm getting Ubuntu going on a home-built dual Opteron box.
I installed a LinkSys WMP54GS Wireless PCI card (My broadband router is LinkSys, as are all existing network cards in various computers around the house - that was the reason for choosing this particular card).

I loaded ndiswrapper and user utilities, grabbed  the Windows driver for this card, and ran:

#sudo ndiswrapper -i wmp54gs.inf

This worked, and I have a /etc/ndiswrapper/wmp54gs directory with several .conf files.

My question is this. I do not seem to have a device name associated with the wireless card. "ifconfig -a" shows eth0 (the wired Gbit interface), lo (loopback), and sit0 (I don't know what this is).

What's my next step to get a device name and complete getting the wireless interface plumbed and enabled?

Thanks very much.
/jim

---

### Post by Lambert on 2005-12-30
Go to this link and go 1/3 of the way down the page where it says this.

```

ndiswrapper -i filename.inf
```

continue following the instructions from that point on.

Also just to make sure. Do you have the .inf file in a directory on your drive and do you also have the .sys or .bin in the same directory (.bin may not be there but there should be a .sys file)

---

### Post by mauroj on 2005-12-30
Thanks - I did do those steps, and "ndiswrapper -l" reports driver present and hardware present.

I followed that with the "modprobe ndiswrapper", which also worked.

However, "ifconfig -a" does not show a device (aside from the three that I listed in the original post, which does not include the wireless device).

I pulled the driver from the CD that came with the LinkSys card. I loaded the driver files (.sys and .inf files) into a directory in my home.

Still scratching my head...

Thanks much.
/jim

---

### Post by Lambert on 2005-12-31
Drivers from the cd do not always work.

remove the drivers you used

sudo modprobe -r ndiswrapper
sudo ndiswrapper -e [I]nameofdriverminusthe.infpart

[/I]then follow these instructions to get a different driver.

> 
**Important: Do NOT use drivers on your CD. They may work, but you may experience kernel crashes etc., if the driver on your CD has not been tested.**
Instead, you need to download appropriate Windows XP driver for your card from the Wiki entry [List]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List"). To identify the driver that you need, first identify the card you have with 'lspci' and note the first column such as 0000:00:0c.0 and then find out the PCI ID of the card that with 'lspci -n' corresponding to the first column of 'lspci' output.
 The PCI ID is third column or fourth in some distributions and of the form '104c:8400'. Now you need to get the Windows driver for this chipset. In the [List]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List"), find out an entry for the same PCI ID and download the driver corresponding to it. Unpack the Windows driver with unzip/cabextract/unshield tools and find the INF file (.INF or .inf extension) and the SYS file (.SYS or .sys extension). 
 If there are multiple INF/SYS files, you may look in the [List]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List") if there are any hints about which of them should be used. Make sure the INF file, SYS file and any BIN files for example, TI drivers use BIN firmware files are all in one directory. Now use 'ndiswrapper' tool to install the driver with

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)

---

