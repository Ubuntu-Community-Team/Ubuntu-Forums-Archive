---
title: "Atheros AR5001 Wifi on Ubuntu"
date: 2011-03-02
forum: Networking &amp; Wireless
---

### Post by kmullins on 2011-03-02
Hey,

I just spent the last 2 days searching far and wide for a solution to why my WIFI Card wasn't being enabled on Ubuntu 10.10.

The computer is an HP G60 but this may apply to other systems as well.

In summary:

After making things hard on myself, I realized there was something weird going on with this error message:

```
hidden@hidden:/lib/modules# sudo ifconfig wlan0 up
SIOCSIFFLAGS: Operation not possible due to RF-kill
```

So following a related (but non-Ubuntu) Blog posting I found, I installed and ran rfkill. It worked like a charm!

```
hidden@hidden:/lib/modules# apt-get install rfkill
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.35-22 linux-headers-2.6.35-22-generic
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  rfkill
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 7,806B of archives.
After this operation, 65.5kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ maverick/universe rfkill i386 0.4-1 [7,806B]
Fetched 7,806B in 0s (16.5kB/s) 
Selecting previously deselected package rfkill.
(Reading database ... 146003 files and directories currently installed.)
Unpacking rfkill (from .../archives/rfkill_0.4-1_i386.deb) ...
Processing triggers for man-db ...
Setting up rfkill (0.4-1) ...
```

```
hidden@hidden:/lib/modules# rfkill unblock all
```

```
hidden@hidden:/lib/modules# rfkill list
0: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

```
hidden@hidden:/lib/modules# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
```

I hope this helps someone else!

---

### Post by chinoto on 2011-04-04
It said mine was soft blocked, so I tried unblocking it, didn't seem to work so I disabled and re-enabled my wireless through NetworkManager (which I have done countless time before, but to no avail), and it worked! My question is how or why did it get soft blocked in the first palce?

Bits from lshw for search engines so other people can find this:
```
Compaq Presario CQ60 Notebook PC
AR5001 Wireless Network Adapter
Atheros Communications Inc.
pci@0000:07:00.0
00:24:2c:53:ad:6c
ath5k
```

---

### Post by shokalabutcha on 2011-06-14
Hi,

I had a worse problem. Whenever I did "rfkill unblock all", my wireless would go from 
Soft blocked: Yes
Hard blocked: No

to 

Soft blocked: No
Hard blocked: Yes

Tantalizing, isn't it? In the end, I created the following script as a (barely acceptable) solution:

sudo rmmod -f ath5k
sudo rfkill unblock all
sudo odprobe ath5k

I hope this script helps someone. If anybody knows how to make this permenant, that will be much appreciated.

I am using a Natty Narwhal, (Ubuntu 11.04) running on Fujitsu Siemens Amilo PA3515 with an Atheros AR5001 wireless module.

Hope this helps,
Shoka

---

### Post by elnetotaca on 2011-07-05
yes, you just open terminal then;

gksu gedit /etc/modprobe.d/ndiswrapper

add;

sudo rmmod -f ath5k; sudo rfkill unblock all; sudo modprobe ath5k
save, close it, then reboot.
cheers

---

