---
title: "[Help] Belkin Wireless G USB Netowrk Adapter (F5D7050UK)"
date: 2006-04-24
forum: Networking &amp; Wireless
---

### Post by splintaraps on 2006-04-24
I need help installing this adapter and connecting to my router with WEP. I got a install CD and everything. I have heard about this program called ndiswrapper.. wat do i actually do with that program..

thanks...

---

### Post by bonefishchris on 2006-04-28
I have the same problem. I wonder if this is any help? :confused: 

[http://ubuntuforums.org/showthread.php?t=81461&highlight=windows+drivers](http://ubuntuforums.org/showthread.php?t=81461&highlight=windows+drivers)

---

### Post by kevjaun on 2006-04-28
hows about this. 

[http://www.linuxant.com/driverloader/](http://www.linuxant.com/driverloader/)

---

### Post by bonefishchris on 2006-05-01
This is how I did it in the end:

[http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux](http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux)

---

### Post by splintaraps on 2006-05-08
I managed to get the belkin f5d7050UK installed...

It says "blkwgu driver present, hardware present"

so then i typed "sudo ndiswrapper -m"
then "sudo ndiswrapper -hotplug"
and again "sudo ndiswrapper -m"
then finally "sudo modprobe ndiswrapper"

I try to go systems > adminstration > Networking
it says its loading but none of the options will appear and just load....

is there a manual way to put some settings??

---

### Post by jpmc on 2006-06-03
I have this adapter and experienced all the problems you have mentioned.  This was in Breezy Badger (5.10).  I had the additional problem of my wireless USB keyboard becoming almost useless whilst ndiswrapper was loaded.

Anyway, I took the plunge with Dapper.  First I tried the live CD and ndiswrapper (I had to download the user space tools in Windows and transfer using a flashdrive).  Things looked more promising - my keyboard didn't lock up, but via dmesg, I saw errors regarding referencing null pointers etc.  Needless to say, I didn't get anywhere.

The solution I found was at [http://zd1211.ath.cx]("http://zd1211.ath.cx").  This provides a linux driver for this USB wireless adaptor.

To be precise about the adapter, it is a a F5D7050uk V.4000 with a USB ID of 050d:705c (found by typing lsusb and looking for a Belkin entry).

On the above site the adapter is listed as not being tested with the rewritten driver (the orignal is provided ZyDAS).  I couldn't get the rewritten driver to even compile (messages about incomplete types). Go with the normal driver (I'm using revision 77, I think).

I installed the linux headers, build essentials, make gcc etc. etc. etc. for Dapper (very nice by the way)

I compiled and installed the firmware as per the instructions on the site, making sure the zd1211b firmware files were also installed (as they aren't by default).  These are installed in lib/firmware/zd1211.  I created /lib/firmware/zd1211b and put the b files in there too for good measure.

Compiled the zd1211b module (to get the b version you need to edit the Makefile and set ZD1211REV_B=1 - currently set to 0.

Installed the module and then loaded via "modprobe zd1211b".  dmesg reports the driver loaded.  

Setting some paramters for wlan0 in /etc/network/interfaces so that it had a static IP, I manually set the essid and key using iwconfig.

Bingo, I'm associated with my access point and typing this now from Dapper using my Belkin F5D7050uk adapter.

Hope this helps - I had spent a long time on this. I haven't got automatic setup on boot yet, but this is darn good start!

Cheers,

Jason.

---

### Post by soapytheclown on 2006-06-05
Helllpppp

sorry an absolute noob on the scene now!

ive got ubuntu 6.06 (amd64 edition if that makes a difference?) and ive got the problem, of, installing the rt73 driver, i used ndiswrapper, and the ndiswrapper front part to it. after a while a WHOLE lot of fiddling around i manged to get to when you type in 

"ndiswrapper -l"

it says 
rt73 driver found, hardware found

so okay drivers appear to be done and even under the menu way (i cant quote now as im in xp as its currently the only way to get online) but through what i assume the nidswrapper front end says the drivers installed.

even though it says its found it all, it wont let me online, or anything

So im this far, but whatever terminal codes to try just dont do a thing.

can someone PLEASE give me some guidance on where to head on this? or what i need to configure? i really need to get online!! :(:(

thanks!

---

