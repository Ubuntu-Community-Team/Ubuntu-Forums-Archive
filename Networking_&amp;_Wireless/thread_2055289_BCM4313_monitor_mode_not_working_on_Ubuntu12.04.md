---
title: "BCM4313 monitor mode not working on Ubuntu12.04"
date: 2012-09-09
forum: Networking &amp; Wireless
---

### Post by hranmuthu on 2012-09-09
Hi all,

Recently I installed Ubuntu 12.04 on my HP ProBook 6460b (64bit). It has a Broadcom BCM4313 wireless interface (wlan0). It works fine with my Home wireless AP. When I put it into monitor mode

ifconfig wlan0 down
iwconfig wlan0 mode monitor
ifconfig wlan0 up

it goes into monitor mode without any issue. But when I capture the interface for incoming traffic using wireshark nothing comes through. I did the same with my old Dell laptop  (with Dell wireless 1390 WLAN mini card) it worked fine.

2nd problem is when I try to put the interface back to managed mode, entire machine hangs on ifconfig wlan0 up command. Only hard power down and re-start can recover this.

lspci -k

24:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
    Subsystem: Hewlett-Packard Company Device 145c
    Kernel driver in use: brcmsmac
    Kernel modules: wl, bcma, brcmsmac


wl module did not come with the installation. I tried installing it but it does not support monitor mode.

I have two problems. Please help me resolve these.

Thanks,
Harshana

---

### Post by hranmuthu on 2012-09-10
Can someone please help me with this issue ?

---

### Post by mikewhatever on 2012-09-10
First, you have two different drivers installed for the same device, which likely causes conflicts (did you say it hangs?). 
```
 Kernel modules: wl, bcma, brcmsmac
```

Remove the wl driver asap.

Second, as Linux is case sensitive, monitor and Monitor and managed and Managed are not the same.

Hope those tips will solve your problems.

---

### Post by hranmuthu on 2012-09-11
Thank you mike for the reply.

I removed the wl driver. now lspci -k shows

24:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
    Subsystem: Hewlett-Packard Company Device 145c
    Kernel driver in use: brcmsmac
    Kernel modules: bcma, brcmsmac

Which one of the Monitor or monitor and Managed or managed is correct ? For me, both uppercase and lowercase ones are accepted and behavior is same (ie, no packets on monitor mode and getting stuck on ifconfig wlan0 up when in monitor mode.

Please let me know what are my options ?

---

### Post by mikewhatever on 2012-09-11
Alright, let me backtrack on the case sensitive statement. While linux is case sensitive in general, it doesn't seem to matter in this particular case. It's ok to use either monitor/Monitor and managed/Managed.

---

### Post by hranmuthu on 2012-09-12
Solved it
-------------
apt-get install broadcom-sta-dkms

modprobe -r <existing dirver>
modprobe wl


HOW TO USE MONITOR MODE
 --------------------------------------------- 
To enable monitor mode: 
$ echo 1 > /proc/brcm_monitor0  

Enabling monitor mode will create a 'prism0' network interface. Wireshark and other netwokk tools can use this new prism0 interface.  

To disable monitor mode: 
$ echo 0 > /proc/brcm_monitor0


Harshana

---

### Post by mikewhatever on 2012-09-12
Ok, I undestand the second part, but why install the STA driver again?

---

### Post by hranmuthu on 2012-09-14
1. For some reason this is a later version than I installed previously.
2. The way to go monitor mode is not iwconfig mode monitor for this driver.

---

