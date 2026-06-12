---
title: "Could someone give recommendations for wifi usb sticks / PCI cards that work"
date: 2009-11-15
forum: Networking &amp; Wireless
---

### Post by slowtrain on 2009-11-15
I've tried three wifi cards / usb sticks in recent weeks.  Each on the surface should have worked, but then I found out that the device, which I saw recommended on these forums or the community documentation, actually comes with more than one chipset, and I always happened to get the wrong chipset.  Or, I got the right chipset in terms of serial number, but not the right version.  So, for example, people have gotten the RTL8187 to work, but that appears to be true for version 3000, not the version 4000 that I got.

So, can someone give me a specific recommendation for a wifi device that works plug 'n play in Ubuntu?  Specifics would be very helpful--e.g., not just the chipset, but chipset and version.  Also, is the device actually currently available, and where can I buy it (preferably a vendor that gives specific information on chipset and version....).

Cheers!

---

### Post by RedSingularity on 2009-11-15
A Wifi that worked out of the box for me was the WMP54G.  Great for linux wireless!!

---

### Post by slowtrain on 2009-11-15
Thanks Red!  Did you get this WMP54G recently?  Some particular online store?  Do you know what chipset is in your WMP54G?

Looking up WMP54G on the manufacturer's website, I can find no mention of what chipset they use.  That may well mean that they use different chipsets at different times, as convenient for them.  (Not a problem for Windows, because no matter what chipset, they'll always bundle the hardware w/ a driver that works for Windows.  But this is a problem for Ubuntu.)  Seller's websites and review websites generally don't say anything about which chipset is involved (and, even if they do, typically not the version).  

So, given my luck lately, I expect that if I get a WMP54G, I'll find out after the fact that I got some version w/ either a chipset or a version of a chipset that won't work w/ Ubuntu.  Then, I can waste another few work days trying to get it to work w/ instructions on the forums and then spend money mailing the device back.

I did find an online post that indicates the WMP54G (or some version of it) contains a RT256x/RT266x RaLink chipset.  Ubuntu community docs (link below) recommend the Ralink RT2500, but whether this also extends to the RT256x is not indicated.  Nor do I have any idea where anyone could currently get a RT2500.  The documentation does say that there is no system support for the Ralink RT2570.

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

This kind of goes to show the problems presented by trying to get wifi to work on Ubuntu.  

So, back to the million dollar challenge:  can anyone recommend something specific that we know will work with Ubuntu?

---

### Post by RedSingularity on 2009-11-15
To answer your question, it comes with the RaLink RT2561/RT61 chipset.

---

### Post by slowtrain on 2009-11-15
Thanks Red!  One of the devices I tried shows up as a RaLink RT2561/RT61 in lspci.  I can connect to the Internet with it.  But it has a tiny drawback on my system:  2/3rds of the time I suspend or hibernate with this pci card active, my system hangs so bad I can't switch to another terminal to shutdown properly.  The other 1/3rd of the time the system sleeps and then wakes in one piece but there is no way to get it to connect to the Internet again (yeah, I tried ifup wlan0).  In another thread, I describe a workaround that detaches the PCI card before I suspend, which prevents the system hang.  But, at least some of the time it comes back w/o the possibility of reconnecting to the Internet.

So, why is this working for you, but not me?  A few possibilities.  1) If I look at the chip itself, it is described as a RT2561ST.  So, if you have a different version of the chip, maybe Ubuntu works w/o problems for that version, but not mine.  2) Maybe you installed a special driver?  I'm just using what came w/ the system (the rt61pci module associates itself with the hardware). or 3) I'm running a 64 bit system and using an AMD64 chip.  Sounds like you may be as well, however.

---

### Post by slowtrain on 2009-11-15
Incidentally, RedSingularity, did you get security working with your device?  WEP or WPA (1/2)?  I tried WPA2, but got the "no private ioctls" error.  As I understand it, that means that Ubuntu has no way to use the WPA2 encryption / decryption built into the chip.  The wpa_supplicant software is a work around, but without hardware acceleration, I wonder how bad a hit I'd be taking on connection speed.  For now, I'm continuing to run my home network w/o encryption (but with a non-broadcast SSID and MAC address filtering).  Hope I'm not taking some huge risk.  I think most of what I want to be private usually is encrypted by another application.

---

### Post by RedSingularity on 2009-11-15
I have got it to run under WEP and WPA encryption standards.

---

### Post by slowtrain on 2009-11-16
Was that WPA2 encryption that you got to work or WPA?  Did you use wpa_supplicant or something else?  Are you running a 64-bit version of Ubuntu?

Thanks!

---

### Post by RedSingularity on 2009-11-16
It was WAP.  I did not use WPA supplicant at all.  I am not sure i have even heard of it.  I have used the default network manager and WICD.  And yes i am running 64 bit.  

PS:  If you want i will run a test with WPA2 mode.

---

### Post by slowtrain on 2009-11-18
Hi Red:  I wouldn't want you to go out of your way, but there may be an incentive to do so--I believe it's with WPA2 (AES encryption) that connections are not only more secure but the data transfer rates generally go up.  Though, that might be only w/ hardware acceleration.  So, if you're up for experimenting, I'd certainly be interested in hearing whether WPA2 works w/ this chipset on Ubuntu.

One thing you said, however, gives me pause.  You said you use wicd and network manager.  I haven't installed wicd because when I do, the Synaptic tells me I have to uninstall Network Manager.  Are you really using both?  Would you recommend WICD over network manager?

Thanks!

---

### Post by RedSingularity on 2009-11-19
Well i tried WPA2 on this chipset and it works fine.

As for WICD, i always recommend it to people with network problems.  It is very easy to use.  More-so than the default network manager in my opinion.  You are correct though, you will need to remove network manager to use WICD.

---

### Post by slowtrain on 2009-11-19
Thanks Red, I'll have to give WICD a try!  Maybe I can get it to the point that I don't have to worry about either a) the wifi card hanging my system or b) the wifi card on wake from sleep refusing to access the internet no matter what I do.  I'm spending way too much time babysitting this card.

---

### Post by slowtrain on 2009-11-24
Hi again!  Good news:  While wicd doesn't solve all my problems, it does solve the most serious.

As long as I shut down the wlan interface (disconnect in wicd and then issue a command line shutdown for wlan0) and use modprobe to remove the driver for this PCI card, I can suspend and hibernate and then, using modproble to reinstall the driver, wicd automatically reconnects to my wifi router.  Without wicd, restarting wlan0 directly from command line or restarting networking altogether, I would be able to restart 2-3 times (after 2-3 suspends) and then would be utterly unable to reconnect to my wifi router.  I'd then have to reboot my machine, which was a serious pain.

I still do need to go through the steps of shutting off wlan and removing the driver.  Without those steps, my PCI bus goes bad on waking up and I can not only not access the wifi router, but the CD drive as well.  And, at times, the computer hangs.

Haven't tried WPA(2) yet w/ wicd.  It may work, but I imagine it has to slow down the connection.  Am wondering if there's anything wrong with using a hidden network and MAC address filtering for security alone?  Does this leave me vulnerable to a local man in the middle attach?

Thanks again for suggesting wicd!

---

### Post by RedSingularity on 2009-11-24
Happy to hear it solved some of your problems :)

---

