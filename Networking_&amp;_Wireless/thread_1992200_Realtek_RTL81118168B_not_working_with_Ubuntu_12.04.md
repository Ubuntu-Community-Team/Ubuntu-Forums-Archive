---
title: "Realtek RTL8111/8168B not working with Ubuntu 12.04 LTS"
date: 2012-05-31
forum: Networking &amp; Wireless
---

### Post by ChemMeister on 2012-05-31
Hi,

It seems that this widespread problem. I am wondering if there were recent advances.
Basically the Internet through wired connection, is slow, with time intervals where there is no connection at all. This apparently is a problem with Realtek RTL8111/8168B card.
There are two known problems:

1) The driver r8169 does not function properly, and one needs to use r8168 instead. I did that by following the instructions of [http://unixblogger.wordpress.com/2011/10/18/the-pain-of-an-realtek-rtl8111rtl8168-ethernet-card/](http://unixblogger.wordpress.com/2011/10/18/the-pain-of-an-realtek-rtl8111rtl8168-ethernet-card/)

2) Some issues with dual booting Windows 7 and Ubuntu, which apparently is solved by a hard restart (holding the power button down for 30 s, and unplugging the power cord for 3 mins)

I tried both solutions but to no avail.
Any ideas? Thanks in advance

System specifications:

Aurora R3
i7-2600K
16GB RAM
Dual Boot Windows 7/Ubuntu 12.04

---

### Post by ratcheer on 2012-05-31
> **ChemMeister said:**
> 

1) The driver r8169 does not function properly, and one needs to use r8168 instead. I did that by following the instructions of [http://unixblogger.wordpress.com/2011/10/18/the-pain-of-an-realtek-rtl8111rtl8168-ethernet-card/](http://unixblogger.wordpress.com/2011/10/18/the-pain-of-an-realtek-rtl8111rtl8168-ethernet-card/)



Note that Realtek released a new version of r8168, very recently, version 08.31.00.

I install it as follows and it always works on my system:

1) Download the driver and expand it into a new directory. cd to the top directory in the expanded directory.
2) sudo make clean modules
3) sudo make install
4) Verify that new file r8168.ko exists in directory /lib/modules/3.2.0-24-generic/kernel/drivers/net/ethernet/realtek/
5) blacklist r8169
6) Edit /etc/initramfs-tools/modules and add a line with "r8168" on it.
7) sudo depmod -a
8 ) sudo update-initramfs -v -u -k `uname -r`
9) Reboot

Note that on item 8, those are grave accents, not quote marks.

Run "sudo lspci -v" to make sure kernel module r8168 is "in use". If it is, and you still cannot make a connection, something else is wrong. Good luck!

Tim

---

### Post by DrFolger on 2012-05-31
I've had no problems with installing the r8168 drivers from realtek.
the credit for the following goes to another on this forum (can't remember who).


First, change the shell from 'sh' to 'bash' in autorun.sh that comes with it.

then run sudo ./autorun.sh

blacklist r8169 and add r8168 to /etc/modules.

or install the drivers the long way, as others suggest.

Finally when you shutdown and either unplug or use the switch on the PSU then give it a couple minutes and reboot.

---

### Post by ChemMeister on 2012-06-03
> **ratcheer said:**
> Note that Realtek released a new version of r8168, very recently, version 08.31.00.

I install it as follows and it always works on my system:

1) Download the driver and expand it into a new directory. cd to the top directory in the expanded directory.
2) sudo make clean modules
3) sudo make install
4) Verify that new file r8168.ko exists in directory /lib/modules/3.2.0-24-generic/kernel/drivers/net/ethernet/realtek/
5) blacklist r8169
6) Edit /etc/initramfs-tools/modules and add a line with "r8168" on it.
7) sudo depmod -a
8 ) sudo update-initramfs -v -u -k `uname -r`
9) Reboot

Note that on item 8, those are grave accents, not quote marks.

Run "sudo lspci -v" to make sure kernel module r8168 is "in use". If it is, and you still cannot make a connection, something else is wrong. Good luck!

Tim

Thanks, after further testing, i have came to realize that it must be something else. Because I get the same behavior whether I use a wired or wireless connection. Basically the internet connection hangs for 10-15 seconds sometimes even longer with no internet connection. I am not sure what is going on.

---

### Post by vak on 2012-07-15
In my case, ubuntu fails to boot in 50% attempts. I thought it is a driver issue and installed r8168. This has enabled 1G/s ethernet (wow!), but the spontaneous hangups during the system start are still the case :(

This is a tail of dead boot dmesg:
```

[   17.904991] r8168: eth0: link down
[   17.905912] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.907060] ADDRCONF(NETDEV_UP): eth0: link is not ready

```
and nothing more in this dmesg file.

This is a part of a healthy dmesg:
```

[   17.904991] r8168: eth0: link down
[   17.905912] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.907060] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.636068] r8168: eth0: link up
[   20.637217] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   20.896671] r8168: eth0: link up
```

Hints, anyone ?

---

### Post by davidjgclark on 2012-07-15
Hi,

I had a similar problem with Ubuntu 10 and 11. In both instances I gave  up trying after several days trying to fix the same problem and just  went back to Windows (I'm not an advanced user and I just use my laptop  for simple things - Internet, videos, word processing - and troubleshooting problems for hours on end doesn't reward me, I just want a working computer). However, this aging computer has since forced me to rethink and I'm now running 12.04. The same problem is there. 

I didn't know whether to include it on this message or to make a new  thread because my specs say that I have a slightly different model of  on-board Ethernet/Wireless. Official specs state it as being:

Realtek RTL8102E (Onboard)
LiteOn WN6302L Wireless LAN

Wired works fine but there's nowhere convenient enough to sit close  enough to my router. Wireless seems to work fine initially. It'll  connect without a problem but will just stop working after between 10 and 20 Mb of data is downloaded (trying to get VLC for example). The only way I can get the wireless working again is from a restart. 

I've tried the 8111/8168 replacement on numerous occasions on versions 10, 11 and now 12 to no avail. Any ideas?

---

### Post by staten on 2012-10-03
> **ratcheer said:**
> Note that Realtek released a new version of r8168, very recently, version 08.31.00.

I install it as follows and it always works on my system:

1) Download the driver and expand it into a new directory. cd to the top directory in the expanded directory.
2) sudo make clean modules
3) sudo make install
4) Verify that new file r8168.ko exists in directory /lib/modules/3.2.0-24-generic/kernel/drivers/net/ethernet/realtek/
5) blacklist r8169
6) Edit /etc/initramfs-tools/modules and add a line with "r8168" on it.
7) sudo depmod -a
8 ) sudo update-initramfs -v -u -k `uname -r`
9) Reboot

Note that on item 8, those are grave accents, not quote marks.

Run "sudo lspci -v" to make sure kernel module r8168 is "in use". If it is, and you still cannot make a connection, something else is wrong. Good luck!

Tim

This worked perfectly for me, but only after I replaced the cat5 patch cord from the computer to the wall in my office, and the cat5 patch cord from the wall to the router in the computer room.  Apparently, this nic only works with cat5e cables...Wierd!

---

### Post by DustWolf on 2012-12-13
Hello,

Some additional hints I had to follow trough to get it working with me:

* Follow instrunctions by ratcheer, but DO read the README file in the driver, specifically you might want to know this:

> 	You can check whether the driver is loaded by using following commands.

		# lsmod | grep r8168
		# ifconfig -a

	If there is a device name, ethX, shown on the monitor, the linux 
	driver is loaded. Then, you can use the following command to activate 
	the ethX.

		# ifconfig ethX up

* "Oh, and if you are annoyed that now your network interface is eth1 instead of eth0 as it used to be, remove the two lines from /etc/udev/rules.d/70-persistent-net.rules that end with NAME=”eth0&#8243; and NAME=”eth1&#8243;." 

(credit: [http://www.twm-kd.com/linux/realtek-rtl81688111e-and-ubuntu-linux/](http://www.twm-kd.com/linux/realtek-rtl81688111e-and-ubuntu-linux/) )

* Add r8168 to /etc/modules to make network available on boot, I think this is necesary if you use mounted network locations in /etc/fstab...

LP,
Jure

---

### Post by Leo_Zhao on 2013-09-29
thanks very much, it really works for me, thank you for saving my days!

---

### Post by tucq on 2014-06-30
> **ratcheer said:**
> Note that Realtek released a new version of r8168, very recently, version 08.31.00.

I install it as follows and it always works on my system:

1) Download the driver and expand it into a new directory. cd to the top directory in the expanded directory.
2) sudo make clean modules
3) sudo make install
4) Verify that new file r8168.ko exists in directory /lib/modules/3.2.0-24-generic/kernel/drivers/net/ethernet/realtek/
5) blacklist r8169
6) Edit /etc/initramfs-tools/modules and add a line with "r8168" on it.
7) sudo depmod -a
8 ) sudo update-initramfs -v -u -k `uname -r`
9) Reboot

Note that on item 8, those are grave accents, not quote marks.

Run "sudo lspci -v" to make sure kernel module r8168 is "in use". If it is, and you still cannot make a connection, something else is wrong. Good luck!

Tim

This worked for me. I logged in and just wanna say a big thanks to you. Best regards

---

