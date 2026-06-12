---
title: "Lost wireless after update manager ran"
date: 2009-07-16
forum: Networking &amp; Wireless
---

### Post by gadgetman1 on 2009-07-16
After yesterday update manager completed, I have totally lost my wireless and can't get it back. It am using 9.04 version. It has been working ok under 9.04, although disconnecting sometimes. But I ran the update manager yesterday and it took my wireless.
My hardware is Latitude D-800 with Broadcom 4306.
I have uninstalled fwcutter and reinstalled it, but wireless doesn't show on Hardware driver list that I can activate. Tried install ndiswrapper, but it keeps give me erreor and can't find the hardware. Any quick easy solution appreciated. Also if you know a link for working ndiswrapper for Broadware 4306.

Appreciated
Ada

---

### Post by superprash2003 on 2009-07-17
try this [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by abarrow on 2009-07-17
I had the same thing happen on my Dell Inspiron 1525.  The regular kernel wl driver was working great, but after the update, it wasn't loading on startup.  

It does load with "modprobe wl" and works after a 15 seconds or so.

I've tried this so far, not necessarily in this order:
1. Installed fwcutter
2. Installed linux-restricted-drivers.  It was interesting that this package didn't get re-installed after the most recent kernel update.
3. Added "wl" to /etc/modules list
4. Ran depmod -a
5. Checked to make sure that the driver is enabled in the Hardware Drivers app.

I used ndiswrapper in the past, but I would really rather use the kernel driver if possible, as it appears to be quicker, and clearly works fine even now.  The only issue is that it isn't loading on startup.

Any ideas?

---

### Post by martinbaselier on 2009-07-17
add it to /etc/modules. 
Make sure to use the exact name of the module.

---

### Post by abarrow on 2009-07-17
As stated above, I did add wl to /etc/modules.  It still doesn't work for some weird reason.  Not really seeing anything in /var/log/messages either.

---

### Post by martinbaselier on 2009-07-17
I read over it, I'm sorry. Could you post the output of **lsmod | grep wl**, after loading the module?

And also the output of 
**cat /etc/modules**

If you add it to the list, it should normally work. Strange.
There is a workaround: you could add a line with **modprobe wl** to /etc/rc.local, before **exit 0**.

---

### Post by abarrow on 2009-07-17
'sokay, my wife complains that I don't read all my emails through!  ;)

Neither dmesg or lsmod has anything in them about the wl driver immediately after reboot.  After modprobe wl, I get this at the bottom of dmesg:
> 
[  256.741484] wl: module license 'MIXED/Proprietary' taints kernel.
[  256.748351] wl 0000:0b:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  256.748371] wl 0000:0b:00.0: setting latency timer to 64
[  256.989928] ieee80211_crypt: registered algorithm 'TKIP'
[  256.991475] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.91.9
[  267.188067] eth1: no IPv6 routers present


and lsmod | grep wl looks like this:
> 
wl                   1281236  0 
ieee80211_crypt        13444  2 ieee80211_crypt_tkip,wl


I quadruple-checked /etc/modules, and the "wl" line is definitely there.  I tried putting it at the bottom and the top, and neither seems to load the wl driver.

Curiouser and curiouser!

---

### Post by abarrow on 2009-07-17
Oh, and another check of /etc/modules:  
The other two modules in that list get loaded fine!
> 
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

wl
lp
sbp2
root@andy-laptop:/proc# lsmod | grep sbp
sbp2                   30476  0 
ieee1394               94660  2 sbp2,ohci1394
root@andy-laptop:/proc# lsmod | grep lp
lp                     17156  0 
parport                42220  2 ppdev,lp


---

### Post by martinbaselier on 2009-07-17
It could be, that the module is blacklisted.
Since blacklisted modules won't be loaded while booting, but you can load them with modprobe. 
to find out check if this shows anything:
```

find /etc/modprobe.d/* -exec cat {} \; | grep wl

```
if it shows a line with blacklist wl, you know the cause.
you could also check /etc/modprobe.conf (if it exists)

Another thing I could think of is: there might be a double file. I don't know if this will really have effect, but it doesn't hurt to check. 

First update the search database:
**sudo updatedb**
then search:
**locate wl.ko**

---

### Post by abarrow on 2009-07-17
Great idea on checking blacklist, but unfortunately (fortunately?) it's not there.  Cool "find" command, by the way!  Also it looks like the module only appears once.

I'm going to put "modprobe wl" in my rc.local file for the moment.  Not crazy about that, but it's less of a hassle than having to install the driver every time I turn on my laptop.

Thanks so much for the help and ideas!

---

### Post by gadgetman1 on 2009-07-19
R E S O L V E D
Hi All you wonderful people that tried to help me. Thank you very much and happy to report that martinbaselier hit it right on the nail. I am still trying to find out why the update manager created a blacklist.conf file which did not exist before. So the solution:
I tried to comment out the line for  4306 wireless card, but still the wireless did not work. So I just removed the blacklist.conf file and wireless device showed up and started working again. Thanks again martinbaselier.

---

