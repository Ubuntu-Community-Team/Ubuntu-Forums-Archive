---
title: "Ubuntu Driver / Kernel Issue?  E100 EEPROM Corrupted"
date: 2006-02-06
forum: Networking &amp; Wireless
---

### Post by chris4amd on 2006-02-06
Well, after spending a while trying to figure out what's wrong and how to fix it, I figured I would come to the forums.  I figured out what is wrong.

Problem:  My onboard network card on my [laptop]("http://thinkwiki.org/wiki/Category:A21m") doesn't work and doesn't show up in the output of *ifconfig* despite the driver being loaded when I perform an *lsmod*.  

Cause:  When looking through the output of *dmesg* I found out that the e100 driver outputs a message about the network adapter's EEPROM being corrupted.  After thoroughly googling this, I realize that this is a problem that was common, but most distos have updated the e100 driver to fix this problem in newer kernels.

However I can't get my card working during either a Dapper (Flight 3) install or a 5.10 install.  

My questions:[LIST]
[*]Is this problem fixed in later versions of the kernel?
[*]How do I install Ubuntu and get a working e100 card?[/LIST]
Thanks.  

References -

[E100 EEPROM Driver Patch @ Kernel.org]("http://kernel.org/pub/linux/kernel/people/hpa/linux-2.6.13-e100-badeeprom.patch")
[Problem documentation]("http://linux.derkeiler.com/Mailing-Lists/Kernel/2004-04/0833.html")
[Problem documentation 2]("http://www.ussg.iu.edu/hypermail/linux/kernel/0502.0/0082.html")

PS - This seemed like it might have had something to do with ACPI support, so I tried installing with *acpi=off* and *noapic* too, with no luck.
PSS - I have [added a bug]("https://launchpad.net/distros/ubuntu/+bug/30666") to the new bugtracker.

---

### Post by wsantoso on 2007-03-28
I am having the same problem. Did you manage to find the solution or workaround? Thanks.

---

### Post by Meserias on 2008-02-09
I set the network first with  RTL-8139D ..... all things are working perfectly NO problems at all. Then I just move the Ethernet cable in to "82557/8/9 Ethernet Pro 100" and I have a very slow internet connection and I'am not satisfied with this
Using: Ubuntu 7.10 (Gusty) :confused:

**Info about Intel PRO100 Card:**
Card: 82557/8/9 Ethernet Pro 100
driver=e100
capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
Driver: driverversion=3.5.17-k4-NAPI :confused:

I don't use gnome-network-manager.
All IP configurations are written in ***interfaces*** file.
[B]
It's there any solution to use this Intel Pro100 card witch I tell you for sure it's working [COLOR="Red"]perfectly[/COLOR] in Windows XP/2000 ?![/B] #-o

---

