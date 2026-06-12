---
title: "No Internet with d-link DWA 135 wireless usb adapter"
date: 2013-02-03
forum: Networking &amp; Wireless
---

### Post by tharinduNA on 2013-02-03
[SIZE=3][SIZE=3][SIZE=3]i[/SIZE]m using ubuntu 12.10[SIZE=3] and [/SIZE][/SIZE]i hav [/SIZE][SIZE=3][SIZE=3][COLOR=Magenta]d-link DWA 135[/COLOR] wireless usb adapter.......it detects the network but it do[SIZE=3]esn't con[SIZE=3]ne[SIZE=3]ct to the internet.......[/SIZE][/SIZE][/SIZE][/SIZE]can anyone help me[SIZE=3].......[/SIZE] [/SIZE]

---

### Post by ahallubuntu on 2013-02-03
~

---

### Post by tharinduNA on 2013-02-03
> **ahallubuntu said:**
> I believe this is another one with the Realtek RTL8192CU chipset.

In a terminal type:

```
lsusb
```If you see "RTL8192CU" in one of the lines (with card plugged in), then it is this chipset.  You can download and build the latest driver from Realtek and blacklist the old driver - following these instructions:

[http://ubuntuforums.org/showpost.php?p=12318056&postcount=2](http://ubuntuforums.org/showpost.php?p=12318056&postcount=2)

Don't use those instructions unless you find it is indeed using RTL8192CU - just tell us the output of "lsusb" plus the output of

```
sudo lshw -C network
```


first of all tnxx    	  		 			 			 				 				 					 						 					 					[B]ahallubuntu 
[/B]


exactly that is the chipset.....i'll follow your instructions 

here is the output for lsusb

tharindu@tharindu-OEM:~$ lsusb
Bus 001 Device 004: ID 2001:3309 D-Link Corp. DWA-135 802.11n Wireless N Adapter(rev.A1) [Realtek RTL8192CU]
Bus 002 Device 002: ID 0fce:8161 Sony Ericsson Mobile Communications AB 
Bus 003 Device 002: ID 046d:c505 Logitech, Inc. Cordless Mouse+Keyboard Receiver
Bus 003 Device 004: ID 1c4f:0003 SiGma Micro HID controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub



and the output for 
sudo lshw -C network

tharindu@tharindu-OEM:~$ sudo lshw -C network
[sudo] password for tharindu: 
PCI (sysfs)

---

### Post by tharinduNA on 2013-02-03
[SIZE=4]Bravo [URL="http://ubuntuforums.org/member.php?u=32392"]ahallubuntu!!!
[/URL][SIZE=4]
[SIZE=4]it is working now......thanks alot :KS:KS:KS:KS:KS:KS:KS:KS[/SIZE][/SIZE]
[/SIZE]

---

