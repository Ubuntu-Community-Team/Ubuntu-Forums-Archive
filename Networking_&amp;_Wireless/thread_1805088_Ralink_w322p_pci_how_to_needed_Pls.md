---
title: "Ralink w322p pci how to needed Pls"
date: 2011-07-15
forum: Networking &amp; Wireless
---

### Post by raiden82 on 2011-07-15
Hi, first of all thanks for reading..

I had to reinstall my system and now i don;t remember how to install my wifi card w322p, i remember i followed an excellent document on how to install everything without an internet connection but lost the link.
Have the install cd which contains a Linux folder! but can't make sense of it..

the outcome of lspci -nn | grep 0280 is:


04:00.0 Network controller [0280]: Ralink corp. Device [1814:3062]

Thanks for your help!

---

### Post by chili555 on 2011-07-15
Please check here:  [http://ubuntuforums.org/showthread.php?t=1608095](http://ubuntuforums.org/showthread.php?t=1608095)

---

### Post by raiden82 on 2011-07-15
can't install build essentials because i don't have a connection, tried am alternative route to install it from the dvd but doesn't find it.. 
I'm pretty sure i've done it before by installing b43 fwcutter and the firmware but now doesn't work.
btw i'm using 11.4

---

### Post by raiden82 on 2011-07-15
or could you recommend a wifi card that just works under most linux distros? i've lost the best part of 2 days on this, trying everything and doesn't work just when i decided to move 90% of my work on linux..

thanks

---

### Post by chili555 on 2011-07-16
> tried am alternative route to install it from the dvd but doesn't find it.. Meaning that you couldn't find build-essential on the DVD or that Synaptic or apt-get couldn't find and index the DVD?

---

### Post by raiden82 on 2011-07-16
thanks for replying, i was tired to figure that out yesterday probably was a different device name, so added the source to synaptic and the package seem to be already installed.

Followed the instructions and learnt a lot in the process then i try the last 2 commands to load the module and test it but doesn't find anything..

I go to additional drivers in the menu and finds the right one and says it's active.

lspci output shows that probably conflicts with my previous aptempts and don't know what to do about it (right device should be rt3562sta as shown in active drivers):


04:00.0 Network controller: Ralink corp. Device 3062
        Subsystem: Ralink corp. Device 3062
        Flags: bus master, slow devsel, latency 32, IRQ 20
        Memory at fddf0000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: rt2800pci
        Kernel modules: rt3562sta, rt2800pci

many thanks

---

### Post by chili555 on 2011-07-16
You may have not read far enough in the link I gave you; let's fix it:```
sudo su
echo "blacklist rt2800pci" >> /etc/modprobe.d/blacklist.conf
exit
```Now reboot and tell us if there is any improvement.

---

### Post by raiden82 on 2011-07-16
That did the trick, writing now from Linux :-)

Thanks a lot.

---

### Post by chili555 on 2011-07-16
Great news! Would you please use thread tools at the top and Mark Solved?

---

