---
title: "Getting a RT2561 wifi device working, kind of"
date: 2009-11-15
forum: Networking &amp; Wireless
---

### Post by slowtrain on 2009-11-15
I recently purchased 3 wifi devices trying to find one that would work with Ubuntu.  After a week of working on a RTL8187 (actually, RTL8187L) and Belkin F5D7050 (actually Belkin F5D7050 v4000), I got nowhere.  Instructions online for how to make these work may work for  different chipset versions than I have:  e.g. RTL8187B, not RTL8187L; and the F5D7050 v3000, not v4000.  (Seriously, someone should put together a far more specific and up to date wifi buying guide for Ubuntu users.)

Anyhow, I then got a CNET CWP-854 PCI card (probably same difference as their USB stick).  I thought this had a chipset that would be plug and play, but once I opened the box I realized I had gotten a different version of the PCI card that uses the RT2561 chipset (more exactly, RT2561ST).  

So, I tried out the card and, miracle of miracles, I was instantly connected to my unprotected wifi router (haven't tried encryption yet).  But, not so fast:  about 2/3rds of the time that I now put my system to sleep or hibernate, it hangs so bad I can't even switch to another terminal to issue a shutdown command as root.  The other 1/3rd of the time, it comes back w/o Internet access and problems accessing anything on the PCI bus.

I've found a way of partially fixing these problems.  Using this method, my system doesn't hang and I can usually suspend and wake a few times before the Internet becomes inaccessible (only way to fix that is to reboot).  The solution is as follows:

Run these lines of code to suspend your machine (you may need to install pm-suspend from synaptic):

sudo ifdown wlan0
sudo modprobe -r rt61pci
sudo pm-suspend

Run these lines of code after you wake your machine up:

sudo modprobe rt61pci
sudo ifup wlan0

I've put these in handy shell scripts that I can run by issuing one line from the terminal.

Hope that helps someone.

Cheers,
Slowtrain

---

