---
title: "Install makes ethernet port unusable for all installs."
date: 2010-09-14
forum: Networking &amp; Wireless
---

### Post by Zookalicious on 2010-09-14
Is it even possible for this to happen? I installed Arch Linux a week ago alongside Ubuntu and Windows 7. After doing some work on it (I didn't even touch network modules) I noticed that on the reboot I had no wired connection. At first I wasn't too worried, then I realized, that I had no wired connection *on any of my installs!* I assumed my motherboard was damaged so I got it replaced at the store. I bring it back and do the same thing, only to have the ethernet be disabled at the same time, again, on Arch, Ubuntu, and Windows 7. I mean, what the hell. I followed the beginners guide exactly. I know that this forum isn't really for this problem, but I haven't gotten any answers over at the Arch Linux forums yet, so I figured someone here might know what's going on. Thanks in advance.

---

### Post by Zookalicious on 2010-09-14
I deleted the arch linux partition. Problem still exists.


EDIT: Removing the HDD and running off of a live CD still gets the same results.... I don't know what the hell Arch did, but it's ruined two motherboards now..... I don't think I'll be returning to that distro again...

---

### Post by PRC09 on 2010-09-14
If it is happening on all 3 OS and the board has been replaced maybe check your cableing or router ,modem.Did it ever work?

---

### Post by MaindotC on 2010-09-14
> **Zookalicious said:**
> Is it even possible for this to happen? 

The only way that is possible is if the network interface was operated incorrectly and it was fried by incorrect voltages.  I'm not even sure that would be a problem because you can plug Power Over Ethernet (PoE) connections into the interface and it should auto-sense and shut off unwanted current.  I'd have to consult the IEEE standard on that one to be certain.  You may also want to check the interface to see if the pins have been bent, or that the cable you are using is not damaged.

You need to consult the [Basic Troubleshooting Guide](http://ubuntuforums.org/showthread.php?t=25557) to make sure the network card is enabled in the BIOS, recognized by hardware identification applications like lspci & lshw, and that the proper driver is installed.  These items (except the BIOS) are covered in the guide.

---

### Post by sikander3786 on 2010-09-14
Didn't the storekeeper check the board before replacing it? Did he confirm that the Ethernet port was out of order?

If all the three OS were getting problems and even changing the motherboard didn't help, I am sure it is a cabling issue, network cable running bad or damaged at some point. First of all rule out the cable issue by using a RJ-45 signal meter or might be your BIOS would've got an option to check for the signal strength in cable.

Also if a spare NIC is available, install it and check if it works for you.

---

### Post by Zookalicious on 2010-09-14
It isn't a cabling issue. The same connection works with my other computer with all the same cables amd settings and works fine on this one up until i got to a certain point in the arch linux install. Also after I reinstalled the motherboard, wired Internet worked just fine for a few days. It was during the reinstallation of arch that it went to hell. Thank you all for your quick replies, I'm going to check the basic troubleshooting guide after work today. I still don't see how even windows is affected but maybe there's something in there that helps.

---

### Post by MaindotC on 2010-09-14
The only way windows would be affected is if there is a hardware failure.  The other possibilty is perhaps the access point is rejecting the traffic coming from the device.  If you have more than 1 machine, here's what I would do:  When the network card fails and the connection drops, connect it to another machine.  You won't be able to access the internet but that's not necessary for verifying that the hardware is working properly.  Assign static ip addresses to both machines and see if you can ping them.  If you can, then it's possible there could be a problem with the access point's firmware or possibly the interface to which you're plugging in the cable.  If you can ping the devices, connect it back to your local network and repeat the procedure - ensuring you can replicate the problem.  Let me know if you need help doing that and I look forward to your reply.

---

### Post by Zookalicious on 2010-09-15
Thanks again everyone for your suggestions. I am not sure how installing Arch could result in a hardware failure. (both times I reinstalled arch). How do you assign a static IP to a machine?

---

### Post by MaindotC on 2010-09-15
Here's a [great guide](https://help.ubuntu.com/9.04/serverguide/C/network-configuration.html) that explains static ip's very well.

---

