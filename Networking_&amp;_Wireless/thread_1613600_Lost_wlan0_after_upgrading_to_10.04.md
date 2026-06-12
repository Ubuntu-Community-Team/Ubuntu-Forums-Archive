---
title: "Lost wlan0 after upgrading to 10.04"
date: 2010-11-04
forum: Networking &amp; Wireless
---

### Post by SB9784 on 2010-11-04
I recently upgraded to ubuntu 10.04 after not using linux on my PC for a few months. After the upgrade, everything worked fine except my wireless card no longer works. It seems to have disappeared from my available interfaces. Here's the output from lspci:
```

$ lspci | grep Wireless
04:00.0 Network controller: RaLink RT3092 Wireless 802.11n 2T/2R PCIe

```...and iwconfig:
```

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```I've been through posts about similar problems that did fixes using things like blacklist and modprobe, but none of these worked. I've searched the RaLink webpages for more up to date linux drivers but found nothing that worked - I downloaded the RT3090_LinuxSTA_V2.3.1.6 driver and followed the instructions to try and build it, but this didn't work. Does anyone have any ideas?

---

### Post by -jrosco- on 2010-11-04
Hi,

Check the file /etc/network/interfaces has the wlan0 interface configured. If not add the wireless info to this file.

Check this out for more detail
[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

JC

---

### Post by SB9784 on 2010-11-04
I was a little confused by that article - I tried to figure out which parts were relevant to me and ended up adding two extra lines to the end /etc/network/interfaces, so it now looks like this:
```

auto lo
iface lo inet loopback
auto wlan0
iface wlan0 inet dhcp


```(Since I don't use WEP encryption I figured the other lines were pointless - besides I'll worry about getting the interface back before getting encryption working!)

I couldn't figure out how to actually get these changes picked up, so I restarted my PC. This still hasn't changed anything though: 
```

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


```...so wlan0 still doesn't exist meaning I can't start it up.

---

### Post by -jrosco- on 2010-11-04
Ok well it maybe a driver you need post the output of ```
lsmod
```>  couldn't figure out how to actually get these changes picked up, so I restarted my PCWhen you change something to do with the network run ```
/etc/init.d/networking restart
``` This will change the settings on the interface you configured.

I do know that ubuntu has a default module for wireless cards, but since yours is a ralink you may need to download the module for that particular card. Run ```
apt-cache search ralink
```This will show the current packages available thought Ubuntu repos. 

If you see your wireless card run ```
apt-get install package-name
``` this will install the package and hopefully automatically configure and pickup your wireless card

Note: Linux is very fussy about what wireless cards can be used look at [http://www.linuxquestions.org/hcl/index.php](http://www.linuxquestions.org/hcl/index.php) and see if anyone else has used the same wireless card as yours, there maybe some good info there about your card.

JC

---

### Post by Narendran95 on 2010-11-04
I know... When I installed Lucid Lynx, I had the same trouble. But then using eth0 connectionm I upgraded it again to Meverick Meerkat. It seems to be working GR8 now! I luv ubuntu...

---

### Post by Narendran95 on 2010-11-04
Hey and one more thing... Even though my iNet connection is working, it gets cut after sometime and i have to use eth0 again. How do I fix this?

---

### Post by SB9784 on 2010-11-04
Here's the output of lsmod (I've just included the bits I thought might be relevant):
```

$ lsmod | grep rt.*sta
rt2870sta             525366  0 

```I searched for packages and got the following:
```

$ sudo apt-cache search ralink
rt2400-source - source for rt2400 wireless network driver
rt2500-source - source for rt2500 wireless network driver
rt2570-source - source for rt2570 wireless network driver
rt73-common - RT73(RT2571W) Wireless Lan Linux Driver - common files
rt73-source - RT73(RT2571W) Wireless Lan Linux Driver - kernel module sources
rt3090-dkms - Support for the Ralink RT3090PCIe network card

```I took a guess and installed the last one in the list - I got a message back saying it was already installed though (that might have been by me - I had this problem after another upgrade a few months ago - I never managed to fix it then either, it just mysteriously fixed itself after another upgrade a month or so later).
> 
Note: Linux is very fussy about what wireless cards can be used look at [http://www.linuxquestions.org/hcl/index.php](http://www.linuxquestions.org/hcl/index.php) and see if anyone else has used the same wireless card as yours, there maybe some good info there about your card.
There aren't any matches for the RT3092 specifically, but there was an article on the 3060 at [http://www.linuxquestions.org/hcl/showproduct.php/product/4488/cat/all](http://www.linuxquestions.org/hcl/showproduct.php/product/4488/cat/all) which referenced some instructions for installing the rt2860 drivers. I followed these instructions but for the RT3090 drivers I found on [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)[]("http://www.ralinktech.com/support.php?s=2"). After compiling the drivers and running make install, I tried to do a modprobe:
```

# modprobe rt3090sta
FATAL: Error inserting rt3090sta (/lib/modules/2.6.32-25-generic/updates/dkms/rt3090sta.ko): Invalid module format

```I ran an lsmod to see what the current state of the system was, and got the following:
```

# lsmod | grep rt.*sta
rt2870sta             525366  0 

```so do I somehow need to get rid of this rt2870sta first?

---

### Post by bkratz on 2010-11-04
You might want to read through this thread

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1573370](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1573370)

---

### Post by SB9784 on 2010-11-04
Hi guys,

Thanks for all of your fast responses - I need to go away now so I'll have a look at this again tomorrow. I seem to remember seeing the above mentioned thread before though, and I didn't have any more luck with it - but I'll have a proper look at it tomorrow and let you know.

---

### Post by -jrosco- on 2010-11-05
When you get a chance run ```
modprobe rt3090sta
``` again and post output of ```
dmesg | tail
```I have seen this problem before and have some old docs on it. If you run dmesg I could have a look to see if its the same problem.

JC

---

### Post by cracker89 on 2010-11-05
did u see the output of ```
sudo rfkill list
``` ?? 
might be useful..

---

### Post by SB9784 on 2010-11-09
> **-jrosco- said:**
> When you get a chance run ```
modprobe rt3090sta
``` again and post output of ```
dmesg | tail
```I have seen this problem before and have some old docs on it. If you run dmesg I could have a look to see if its the same problem.

JC

Hi all - sorry for the delayed response, I haven't had access to my computer for a while. Here's the output for some of the commands you mentioned:

```


$ sudo modprobe rt3090sta
FATAL: Error inserting rt3090sta (/lib/modules/2.6.32-25-generic/updates/dkms/rt3090sta.ko): Invalid module format
$ sudo dmesg | tail
[   27.402418] CPU3 attaching sched-domain:
[   27.402420]  domain 0: span 1,3 level SIBLING
[   27.402421]   groups: 3 (cpu_power = 589) 1 (cpu_power = 589)
[   27.402424]   domain 1: span 0-3 level MC
[   27.402425]    groups: 1,3 (cpu_power = 1178) 0,2 (cpu_power = 1178)
[   28.383263] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   48.483636] FAT: invalid media value (0x2f)
[   48.483643] VFS: Can't find a valid FAT filesystem on dev sdb1.
[  163.664747] rt3090sta: disagrees about version of symbol module_layout
[  171.610277] rt3090sta: disagrees about version of symbol module_layout

```
------------
> **-cracker89- said:**
> 
did u see the output of
```

sudo rfkill list

```
?? 
might be useful..


This command produced no output.

---

### Post by cracker89 on 2010-11-11
Ok. have you tried checkin if u need drivers? if u can connect the system upto a net connection, then go to System>Admn>Hardware Drivers. See if it prompts you?

---

