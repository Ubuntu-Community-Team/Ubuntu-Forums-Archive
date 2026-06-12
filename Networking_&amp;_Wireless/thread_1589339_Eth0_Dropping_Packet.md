---
title: "Eth0 Dropping Packet"
date: 2010-10-06
forum: Networking &amp; Wireless
---

### Post by zizebra on 2010-10-06
I have installed the server version of Ubuntu10.04.1 and I am battling to get network to communicate. Eth0 responds to ping messages during startup. As soon as it gets to the login screen, eth0 starts dropping packets. I have checked the firewall but there is nothing to suggest that it is configured to drop packets. What have i missed

---

### Post by Sergius14 on 2010-10-06
Check for speed and duplex. Also you can force it on both sides.

If it keeps in that way, you should try a Kernel Upgrade (or Downgrade if you have the latest release).

BTW, do you have Iptables (or another FW) enabled? if it yes, include the configuration aswell.

---

### Post by zizebra on 2010-10-07
Hi
 
 This is fresh install. Nothing has been configured except for Ip Address and gateway and dns address. I have installed Ubuntu 10.04.1 , ubuntu 10, and the RC 10.10. Please note all these are running on Microsoft Hyper-V VM. The oldest release where everything is working is Ububtu 9.10 Server
 
Ubuntu 9.10 -  Network is fine during install and after installation
Ubuntu 10.0 - Network is working during installation but not after installation. (No Dropped Packets)
Ubuntu 10.04.1 Network Available during install but fails thereafter (Shows Dropped Packets)
Ubuntu 10.10RC Network Available during install but fails thereafter (Shows Dropped Packets)
 
Iptable has not been configured in all the installations

---

### Post by BakaNeko59 on 2010-10-14
I'm experiencing the same problem with a fresh install of 10.10 and Hyper-V. Have you figured it out yet? I'm getting ready to go back to 9.10 if I can't get it working.
 
In fact, after a couple of reboots eth0 no longer even shows up in ifconfig. I get the error no such device if I ifup eth0, and lspci shows a DECchip21140 Ethernet controller as available, but obviously not being used.
 
I found this post [http://ubuntuforums.org/showpost.php?p=9754770&postcount=7](http://ubuntuforums.org/showpost.php?p=9754770&postcount=7) that may help you, but it hasn't helped me...
 
UPDATE - Solution found!
 
By using a combination of the information in the above post and this article [http://www.panterlo.com/2010/10/10/ubuntu-10-10-and-hyper-v-r2/](http://www.panterlo.com/2010/10/10/ubuntu-10-10-and-hyper-v-r2/) I was able to get my networking going.  I needed to delete the legacy network adapter from the virtual machine (I had originally installed legacy before building, then added a "normal" one after it was built.)  Then I needed to make sure everything addressed the "normal" one as "seth0" rather than "eth0".  Apparently the comment in the panterlo post about switching back from seth to eth was incorrect.  I also made sure my network adapter had a static MAC address in the Hyper-V settings so that it wouldn't change and create a new entry in the config file.
 
In any event, I now have a working 10.10 server running on Hyper-V with the normal (non-legacy) network adapter.  At least until my next update :)

---

### Post by panterlo on 2010-10-18
I am the author of the article referenced. Please make sure you install adjtimex package and remove ntpdate. And lastly, really make sure the checkbox for synchronize guest with host is checked in the virtual machine settings.

Also compile the hv_* drivers into the initramfs.

Without this unexpected things can happen, one is dropped ethX connectivity etc.

Regards,

Jens

---

