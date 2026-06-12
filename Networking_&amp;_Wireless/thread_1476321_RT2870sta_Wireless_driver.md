---
title: "RT2870sta Wireless driver"
date: 2010-05-07
forum: Networking &amp; Wireless
---

### Post by Rich113 on 2010-05-07
HI,

I recently upgraded to 10.04 and had problems connecting to my wireless network via my DWA-140 adapter. 

After searching online, I eventually found the problem was the result of the RT2870sta driver that comes with Ubuntu not having WPA support enabled by default. ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/543836](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/543836)).

I followed the steps provided via the above link, to download the RALink driver, edit the config.mk file to enable WPA support, and then compile the driver. I was eventually able to get the wireless to connect. 

However, the problem I have now is that every time the system is rebooted, Ubuntu reverts back to the original RT2870sta driver that does not work. I know this by looking at the output of lsmod..

[I]$ lsmod | grep rt2870
rt2870sta             461811  1 [/I]

To get wireless working again, I have to unload the driver and load the new custom driver in:

*<unplug dongle>*
[I]$ modprobe -r rt2870sta
$ ~/RT2870_LinuxSTA_V2.3.0.0/os/linux/insmod rt2870sta.ko[/I]
*<plug dongle back in>*

At which point, the new driver is reported and wireless will work again.

[I]$ lsmod | grep rt2870
rt2870sta             561972  1[/I]

How do I fix this so that the correct driver is loaded on boot, without me having to carry out these manual steps each time?

Thanks.

---

### Post by chili555 on 2010-05-07
When you compiled, did you do *sudo make install*? It will substitute the compiled version for the built-in.

---

### Post by Rich113 on 2010-05-07
Hi,  Yes I did. The action I took were as follows:

 [I]~$ tar xjf RT2870_LinuxSTA_V2.3.0.0.tar.bz2 
~$ cd RT2870_LinuxSTA_V2.3.0.0 
~/RT2870_LinuxSTA_V2.3.0.0$ nano os/linux/config.mk 
 ~/RT2870_LinuxSTA_V2.3.0.0$ make 
~/RT2870_LinuxSTA_V2.3.0.0$ sudo make install  
[/I]
There were no errors reported during compilation. Output below  

[I]~/RT2870_LinuxSTA_V2.3.0.0$ sudo make install
make -C /home/rich/RT2870_LinuxSTA_V2.3.0.0/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/rich/RT2870_LinuxSTA_V2.3.0.0/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /home/rich/RT2870_LinuxSTA_V2.3.0.0/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/2.6.32-22-generic/kernel/drivers/net/wireless/
install -m 644 -c rt2870sta.ko /lib/modules/2.6.32-22-generic/kernel/drive/net/wireless/
/sbin/depmod -a 2.6.32-22-generic
make[1]: Leaving directory `/home/rich/RT2870_LinuxSTA_V2.3.0.0/os/linux'[/I]

However, when I insert the dongle, lsmod indicates the old driver is loaded and I have to go through the process of manually unloading the old driver and then insmod rt2870sta.ko to get wireless working.

I thought it may have been because the original driver was loaded at the time, but I repeated the same actions with the dongle unplugged and the rt2870sta driver unloaded, with the same outcome.

---

### Post by chili555 on 2010-05-07
> lsmod indicates the old driver is loaded Huh?

The old driver is named rt2870sta and the new driver is named rt2870sta. How does lsmod tell you it's the old one and not the new one?> install -m 644 -c rt2870sta.ko /lib/modules/2.6.32-22-generic/[COLOR="Red"]kernel/drivers/net/wireless/[/COLOR]When you do:```
modinfo rt2870sta
```does it say the module is kernel/drivers/net/wireless/ or, as in my system, kernel/drivers/[COLOR="Red"]staging/rt2870[/COLOR]/ ? If your modinfo says *net*, then that's the one that's loading. If it says *staging*, then the old one is indeed loading and we must tweak your installation.

---

### Post by Rich113 on 2010-05-08
> How does lsmod tell you it's the old one and not the new one?Because lsmod indicates the size of the driver..

[I]old driver:
$ lsmod | grep rt2870
rt2870sta 461811 1

new driver:[/I] [I]
$ lsmod | grep rt2870
rt2870sta 561972 1[/I]

> When you do: modinfo rt2870sta does it say the module is kernel/drivers/net/wireless/ or, as in my system, kernel/drivers/staging/rt2870/ ? After boot up modinfo rt2870sta reports:

[I]~$ modinfo rt2870sta
filename:       /lib/modules/2.6.32-22-generic/kernel/drivers/staging/rt2870/rt2870sta.ko
alias:          rt3070sta
version:        2.0.1.0[/I]

So I then located the /net/wireless entry in MakeFile and amended it to point to /staging/rt2870. After running sudo make install, the correct driver now loads on boot.

Many thanks for your help.

---

### Post by pasqm on 2010-05-09
Hi I tried to follow your tutorial.
It worked :)
But I did not find how where to replace /net/wireless by /staging/rt2870 in the makefile

Can you help me ?

Regards
Marc

---

### Post by pasqm on 2010-05-09
I' ve found the answer by myself
In the makefile, search
LINUX_SRC_MODULE = /lib/modules/$(shell uname -r)/kernel/drivers/net/wireless/
and replace by
LINUX_SRC_MODULE = /lib/modules/$(shell uname -r)/kernel/drivers/staging/rt2870/

save and
sudo make install
reboot
it works

Marc

---

