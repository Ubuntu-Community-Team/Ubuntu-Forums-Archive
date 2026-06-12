---
title: "UBUNTU can't find my Network"
date: 2010-08-05
forum: Networking &amp; Wireless
---

### Post by swmason on 2010-08-05
If anyone can help:

I have a new Toshiba Satellite L645-54038.  I just ditched Windows 7 and installed UBUNTU 10.04.

When I start Ubuntu network manager can see both of my neighbor's networks but not my own.

I'm confident my network is not the problem, because I currently have 3 other devices that have no problem connecting (2 Macs and 1 xubuntu).  In fact my laptop had no problems connecting to my network with Windows 7.  My router is a cisco linksys WRT54G2 V1.  

My toshiba network card is a Realtek 8172 (rev. 10).  

Thanks in advance for you help.

---

### Post by wcm994 on 2010-08-31
I have an identical problem.  I've got a Toshiba Satellite L645-S4030 (are you sure your '5' isn't an 'S'?) also running Ubuntu 10.04 (although I've also tried 9.10).  Not sure about yours but my ethernet is also not working.  Here's my return from *'lshw -C Network'*

```
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 10
       serial: 20:7c:8f:0d:91:28
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xSE driverversion=0014.0115.2010 firmware=62 latency=0 multicast=yes wireless=802.11bg
       resources: irq:16 ioport:7000(size=256) memory:f3100000-f3103fff
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR8152 v1.1 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:08:00.0
       version: c1
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:f3000000-f303ffff ioport:6000(size=128)
```

I've heard that the Atheros hardware is somewhat lacking in support.  Could anyone point in a direction towards working drivers for installation?

Thanks in advance for any help (also random Win-doh's bashing is always welcome and, in fact, encouraged).

---

### Post by varunendra on 2010-09-02
swmason,

Please post the outputs of the following:
```
lshw -C network
``````
ifconfig -a
``````
iwconfig
``````
cat /etc/samba/smb.conf | grep workgroup
```Also, run the last command on your xubuntu machine and see which workgroup it belongs to (workgroup=***<what??>***)



@wcm994,
For sake of convenience (also, your problem is a bit different), I'd suggest you to start a new thread and post its link here to follow.

For now, I guess a driver for AR8152 is not yet modulated into kernel, so you must use **Proprietary drivers** for the card. See if it is listed under **System>Administration>Hardware Drivers**. You may have to enable all repositories in **System>Administration>Software Sources**.
Otherwise have a look [here]("https://lists.ubuntu.com/archives/kernel-team/2010-February/008808.html").

If you need further help, please start a new thread as I suggested above.

<snip>

---

### Post by wcm994 on 2010-09-02
Ok, sorry for the delay in response.  The problem has been solved.  As it was suggested above I had to get a different ethernet driver from Atheros.  Once I installed that and got the wired connection working I downloaded and installed all the latest updates.  Then after a restart the wireless now works just fine as well.  Thanks for the quick responses on the problem.  Here are a couple of the sites/threads I when to to assist in getting it solved:

[http://ubuntuforums.org/showthread.php?t=1505697]("http://ubuntuforums.org/showthread.php?t=1505697")

[http://ftp.nluug.nl/pub/os/Linux/system/kernel/people/mcgrof/ethernet/]("http://ftp.nluug.nl/pub/os/Linux/system/kernel/people/mcgrof/ethernet/")

Hope that helps others.



Regards,
-Another Satisfied Customer (though 'customer' would imply that I actually paid for this stuff!:p)

---

