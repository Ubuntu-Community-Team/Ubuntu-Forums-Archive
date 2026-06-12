---
title: "WIFI trouble / Atheros / Packard Bell laptop"
date: 2009-04-12
forum: Networking &amp; Wireless
---

### Post by forumaccount on 2009-04-12
Hi,
I've been having real trouble to get my wireless working. I'm a little ashamed to tell this, but i actualy got ubuntu a few weeks after christmas. I tried long and hard to get my wireless working back then with no luck. I left it for a while out of frustration and have came back to it for another attempt.
Once again i cannot get it to work..
I've followed many threads, read up on lots, and spent so much time again.
It's getting me so frustrated again and i dont know what to do anymore.

Pleaseplease could someone walk me through and help me get my wireless up and running.
I saw this thread [http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)
So i will post some of the outputs from the commands it gives.

**_lspci_**

00:06.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)

**_iwconfig_**

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.


All the others give long outputs and i'm not sure if it's info that you need. Do let me know if you need more and i will get it for you.
I'm going to do a clean install of Ubuntu 8.10 and run the updates.
One last thing. I have ubuntu installed onto an external USB hard drive. Does this affect anything?

Thanks

---

### Post by forumaccount on 2009-04-13
I'm still in desperate need for help.
I've done a clean install of ubuntu 8.10 and ran the updates now i just hope someone here can help me.
I can use a wired connection whilst i try get the wireless working, because i know that i'll have download stuff.
From what i know i need the madwifi-ng drivers

Here's a few of the last threads i followed to try get it working with no success.

[http://ubuntuforums.org/showpost.php?p=5711824&postcount=6](http://ubuntuforums.org/showpost.php?p=5711824&postcount=6)
This seemed to go well till the step where you put 'make install'
I'm sure it went wrong there because the output didnt seem right.

[http://ubuntuforums.org/showthread.php?p=6929399#post6929399](http://ubuntuforums.org/showthread.php?p=6929399#post6929399)
All steps ran fine but wireless stil didnt work

[http://ubuntuforums.org/showthread.php?t=105437](http://ubuntuforums.org/showthread.php?t=105437)
Again didnt work.

---

### Post by forumaccount on 2009-04-13
Please someone help?
I've been trying again and just cant do it : /

---

### Post by mark.roeling on 2009-04-19
Hi,

Browse your dmesg log. Does it say anything about ath_hal, ath_pci or something like that? On my laptop it's around 11 seconds in the log.

M.

---

### Post by gedesby on 2009-04-19
hey there try ndiswrapper and the xp driver

---

### Post by NoJock on 2009-04-20
Good day Forumaccount: Sorry your having problems with wifi and Hp laptop! Have the same problem with mine. Gave up on the 8.10 distro and move to 9.04 bata and it atleast works some what, it drops off the network but will recover and using the ath5k_pci most of the time it only connects a 1mb/s it does seem to work ok just not reliable. Hopping in the final release it will just work as most of the Ubuntu distros seem to just work!!

---

