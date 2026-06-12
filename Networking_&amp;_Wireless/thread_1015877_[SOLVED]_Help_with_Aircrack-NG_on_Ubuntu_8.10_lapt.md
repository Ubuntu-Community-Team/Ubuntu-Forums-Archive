---
title: "[SOLVED] Help with Aircrack-NG on Ubuntu 8.10 laptop"
date: 2008-12-19
forum: Networking &amp; Wireless
---

### Post by leartec on 2008-12-19
I have a Dell 1520 laptop that I have installed Ubuntu 8.10. All the drivers that I need to operate the laptop installed automatically during the OS installation, which was awesome! So the laptop works great, but I'm truing to get Aircrack-NG up and running. I found a guide online but being new to Linux I don't understand how to patch my wireless driver to get injection working. I can't find a tar ball to download, only a file of code that I guess I have to save it somehow and compile it. I have no idea how to do this. Here are my specs:
   
Dell 1520 laptop with Ubuntu 8.10

output from commands:
 **cat /proc/version**
* Linux version 2.6.27-9-generic (buildd@rothera) (gcc version     4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Nov 20 21:57:00 UTC 2008*
[B]
lspci[/B]
*0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)*

I have Aircrack-NG installed already. Here's the site I have been trying to use: [http://www.aircrack-ng.org/doku.php?id=tutorial](http://www.aircrack-ng.org/doku.php?id=tutorial)

Any help is great.
Thanks in advance!

---

### Post by leartec on 2008-12-19
**This is a duplicate thread!**

---

### Post by Titan8990 on 2008-12-19
In order to get Broadcom cards to support injection your have to patch/recompile your kernel to use this patch: [http://www.aircrack-ng.org/doku.php?id=broadcom](http://www.aircrack-ng.org/doku.php?id=broadcom)

---

### Post by leartec on 2008-12-19
Thanks for the reply. I've been to the link you listed. This is actually where I have problems. When I click to download the patch, it just displays all the code for the driver. It doesn't actually download a file. So I guess my question is what do I do with that code? How do I get it downloaded? Am I suppose to copy it to a text file and save it with a certain extension or what?

---

### Post by leartec on 2008-12-19
ALSO.... the download says it's for kernel 2.6.20. Will this patch work for kernel 2.6.27?

---

### Post by infernosoft on 2009-08-05
Hi, so this thread says "[SOLVED]" but was it really solved? Were you able to get your BCM4312 to work with aircrack successfully? I'm getting a laptop in a couple of days with that chipset and was wanting to get as much help/input as possible.
 
Thanks.

---

### Post by alSee on 2009-09-16
I have the same wifi card. 
In fact, problem is NOT solved. **Titan8990** advised the patch which is for injection-related troubles. But the main problem is neither bcm43xx nor b43 modules don't recognize the BCM4312 chipset. 
When I blacklisted 'wl' module and tried to load b43/bcm43xx/b43legacy modules via modprobe or by addition one of them to /etc/modules then the appropriate module loaded successfully but the interface didn't appear. Both the 'iwconfig' and 'airmon-ng' reported of no wireless interface.

---

