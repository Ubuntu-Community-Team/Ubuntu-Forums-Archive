---
title: "What's the real wireless problem with 9.10?"
date: 2010-01-06
forum: Networking &amp; Wireless
---

### Post by Joesplace on 2010-01-06
All,

Ubuntu 9.04, LinuxMint 7 and OpenSuse 11.1 worked fine on my Dell wireless system out of the box. When I tried upgrading to LinuxMint 8, Ubuntu 9.10 or OpeneSuse 11.2, wireless quite working. None will even see my wireless cards!

I did notice that each edition upgraded the Network Manager applet. My two Dell desktops and 3 laptops react the same, no wireless connection. I have tried many of the published fixes including wicd but nothing works.

Anybody know the real problem? Whatever it's, I think it's common between all new revisions . . .

Thanks,
Joe

---

### Post by Maheriano on 2010-01-06
Have you tried searching for available hardware drivers for your machine?

---

### Post by Joesplace on 2010-01-06
yep, been down that road too. Tried all the different drivers for each machine but no go . . .

---

### Post by snowpine on 2010-01-06
I'm assuming you have a Broadcom wireless card? (If you're not sure, use the terminal command 'lspci'.) The short answer is that Broadcom does not give most Linux distros legal permission to distribute their proprietary software. 

Fortunately, Broadcom makes the driver freely available: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

I have installed over 20 Linux distros on my Broadcom-equipped Dell Mini, and in all cases, I was able to get the wireless working. Ubuntu was one of the easiest; the Restricted Hardware manager is an easy shortcut (so the Broadcom link above is unnecessary).

---

### Post by Joesplace on 2010-01-06
yep, you are correct - they are all using Broadcom. Guess I'll try again later this afternoon to add the new driver you posted a link to. 

If the Linux community is trying to make it easy to leave Windows behind, this seems like a setback for many people. There a ton of us that have no real programming ability but are really trying to make Linux work and when you just upgrade from one revision to the next and a small thing like wireless quits working - it's major headaches! I had to reinstall Ubuntu 9.04 just to get back online because I made the mistake of upgrading all my computers in one day. Live and learn . . .

Thanks for the help!

---

### Post by snowpine on 2010-01-06
> **Joesplace said:**
> yep, you are correct - they are all using Broadcom. Guess I'll try again later this afternoon to add the new driver you posted a link to. 

Sorry if I was unclear (I just edited my previous post)... that Broadcom link is what I use on other distros; Ubuntu makes it really easy (System->Administration->Hardware Drivers) so you don't have to compile the module yourself. It should only take you a few mouse clicks.

> **Joesplace said:**
> If the Linux community is trying to make it easy to leave Windows behind, this seems like a setback for many people. 

The Linux community cannot force Broadcom to release their closed-source wireless driver under the open-source license. Whether you personally agree or not, most software in the world today is *not* freely redistributable (Linux is the exception rather than the rule).

For what it's worth, your wireless probably won't work out-of-the-box if you installed Windows or Mac OS either. It is not a Linux vs. the world issue.

---

### Post by Joesplace on 2010-01-06
Please don't get me wrong, I love and support Linux altogether!

My point was if we expect others to make the move to Linux, it needs to work from the install or give them a hint how to fix it. 

If the past Linux versions worked on my computers, I would have expected beta testers to know most people with Broadcom drivers would have wireless problems because of a new change and simply say that :)

Anyway, I will keep working on the problem till I get it solved. Happy days, at least I was able to get two computers back up and running on the Ubuntu 9.04 version . . .

Thanks!

---

### Post by usenetz on 2010-01-06
> **snowpine said:**
> Ubuntu makes it really easy (System->Administration->Hardware Drivers) so you don't have to compile the module yourself. It should only take you a few mouse clicks.A few mouse clicks would be wonderful however as a new 'recruit' to Linux (Mint for me, on a MacBook Pro 5,5 using a BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)), I too am going round in circles trying to get Linux to see my wireless network; although it does see my various routers initially, following install of the STA driver via the route you mention, on reboot it no longer connects.

On reboot, I try your 'really easy' method, (System->Administration->Hardware Drivers), but then get this error:
> Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log

jockey.log reads:

> 2010-01-07 01:40:41,467 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x28a4ab8> about HardwareID('modalias', 'pci:v000010DEd00000AA6sv000010DEsd0000CB79bc0Csc03i20')
2010-01-07 01:40:41,467 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x28a4ab8> about HardwareID('modalias', 'acpi:APP0001:smc-mcp:')
2010-01-07 01:40:41,607 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-07 01:40:41,662 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-07 01:40:44,335 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-07 01:40:46,116 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-07 01:40:50,226 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-01-07 01:40:50,226 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2010-01-07 01:40:50,264 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-07 01:40:57,249 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-07 01:40:57,267 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-07 01:40:57,288 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted

I have followed 'guides' in various forums but still no wireless.

I would love to get this sorted before Christmas ;)

john

---

### Post by Joesplace on 2010-01-07
Well, back to the drawing board - I installed the Broadcom driver from: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
and still nothing. I followed the instructions directly with no errors and still no wireless. Any more ideas? I'm done for tonight . . .

---

### Post by usenetz on 2010-01-11
I appear to have found a solution to my problem with the Broadcom STA driver.

> When activating the driver **you should have the Karmic CD in you drive** and **your drive listed as a software source under System/Administration/Software Sources**. Else the driver won't be able to activate
Source: [http://ubuntuforums.org/showthread.php?p=8641470#post8641470](http://ubuntuforums.org/showthread.php?p=8641470#post8641470)

Insert Mint CD in drive | Menu | All Applications | Administration | SOftware Sources | Other Software | Add CD-Rom | Close | Reload (from the pop-up message about out-of date sources)

It works for me using Linux Mint, on a MacBook Pro 5,5 using a BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01))

john

---

### Post by bkratz on 2010-01-11
> **Joesplace said:**
> Well, back to the drawing board - I installed the Broadcom driver from: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
and still nothing. I followed the instructions directly with no errors and still no wireless. Any more ideas? I'm done for tonight . . .

Here is a relatively recent thread regarding a new open source driver replacing b43 for some Broadcom cards. Worth reading at least.

---

