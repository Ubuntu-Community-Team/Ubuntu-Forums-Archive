---
title: "Hard Hangs with atl1e and rtl8192ce drivers"
date: 2011-06-10
forum: Networking &amp; Wireless
---

### Post by linuxslate on 2011-06-10
I'm having problems beyond my knowledge with a Toshiba Satellite C655D-S5133.

The system hard hangs at various time **Unless** it is connected to an Ethernet connection.

In particular, it always hard hangs when either:

1.  It associates with a wireless Access Point
2.  I attempt to execute:

sudo modprobe -r atl1e     (hard hang *_before_ even asking for password*  -- Not on module removal)

Other hangs are frequent, and seemingly random activities cause them, but they are bad enough that the system is unusable even when used off-line.

_ With a  wired Ethernet connected the system is stable, and I don't think it has ever crashed._
Even if that Ethernet connection is not up, or has no IP addr.

As long as I am connected to Wired Ethernet, Wireless works fine.  I can associate/disconnect from AP's all day long.

History:
Upon installing 10.04, neither the Wireless or Wired Ethernet were detected.

I built and installed the respective drivers from the Vendor websites:
[http://partner.atheros.com/Drivers.aspx](http://partner.atheros.com/Drivers.aspx)  AR81
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false)

I also have the vendor-provided ATI Radeon Catylist drivers installed.

Furthermore, I cannot get rid of the atl1e Atheros kernel module.

I have deleted at1le.ko from every place in /lib     -- Every installed kernel, everyplace.  A find command shows that at1le.ko is not on the system anyplace.

Yet lsmod still shows atl1e installed, and Wired Ethernet still works.

Like I said, sudo modprobe -r atl1e         crashes the system immediately if ethernet is not connected.  If it is, the modprobe -r command is successful, but atl1e is back upon the next reboot (and so are the crashes).

I want to remove atl1e to see if the system is stable with wireless only.  Wireless only would be acceptable.  I also have a USB Ethernet adapter that I can use as needed.

Please help with this rather strange problem (I think).  I can post lspci,  and what ever else is needed, but I really just need a little help getting atl1e out of my kernel without re-installing.

---

### Post by cjimenez2581 on 2011-07-06
I have exactly same problem, I really want to work linux in my laptop... Please any suggestion?

---

### Post by salemboot on 2011-08-29
I've got an S133.   I've had nothing but problems finding a version of Ubuntu to load on it with moderate support.

11.04 works and the recomended boot parameters follow:

nomodeset rtl8192ce.blacklist=1 

* be prepared to wait about 10-15 minutes for it to boot.

Get it installed, then update from an ethernet connection:

I think the sudo command locks up because it collides with the opensource video driver.  

Make sure to download the correct proprietary driver beforehand for the video card. 


*** The main problem I'm encountering is the driver that ships with the kernel is SLOW!   10mbit internet connection should yield a 1 m/s download.

I get around 64 k/s.  Dang kernel developers messing crap up :)

---

### Post by salemboot on 2011-09-14
Ubuntu 10.04 finally works for me with the S133.
[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2782](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2782)

search for rtl8192CE-VA4


For 2.6.32 get the Linux driver for kernel 2.6.34 (and earlier)

It's been working pretty good for me.


# script
sudo su
tar vxf rtl8192ce_linux_2.6.0005.1116.2010.tar.bz2
cd rtl*
make && make install && modprobe r8192ce_pci





:guitar:
exit

---

