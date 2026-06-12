---
title: "Belkin F5D8053 driver loaded still device not ready"
date: 2010-05-18
forum: Networking &amp; Wireless
---

### Post by rencemc on 2010-05-18
I tried all the threads to load and compile the driver for the Belkin wireless-N F5D8053 (Ralink RT2870 chip) I still cannot get it to come up - the wireless status says device not ready. Here is some of the system info relating to the adapter:




terry@terry-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:bf:53:02:8f  
          inet6 addr: fe80::214:bfff:fe53:28f/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:4 dropped:0 overruns:0 carrier:8
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:79 errors:0 dropped:0 overruns:0 frame:0
          TX packets:79 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9326 (9.3 KB)  TX bytes:9326 (9.3 KB)
---------------------------------------------------------------

terry@terry-desktop:~$ lsusb
Bus 002 Device 004: ID 046d:08b2 Logitech, Inc. QuickCam Pro 4000
Bus 002 Device 003: ID 045e:008c Microsoft Corp. Wireless Intellimouse Explorer 2.0
Bus 002 Device 002: ID 03f0:3c02 Hewlett-Packard PhotoSmart 7350
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 050d:805e Belkin Components 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

----------------------------------------------------------------

terry@terry-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g  Mode:Managed  Access Point: Not-Associated   
          Bit Rate:0 kb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


terry@terry-desktop:~$ lsmod | grep rt28
rt2870sta             628292  0 
terry@terry-desktop:~$ 
----------------------------------------------------------------
lshw

  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:e0:4c:81:92:00
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=802.11b/g

----------------------------------------------------------------

You help is appreciated :)

---

### Post by BoneKracker on 2010-05-18
Show```
ls -Rl /etc/Wireless
```
```
ls -Rl /lib/firmware
```

---

### Post by rencemc on 2010-05-18
deleted

---

### Post by BoneKracker on 2010-05-18
Holy Moses.  :lol:

I should have remembered you're using Ubuntu and instead told you to do:
```
ls -lR /lib/firmware |grep rt2870.bin
```

Anyway, you've apparently got the firmware, so that's not the problem.> -rw-r--r-- 1 root root 4096 2010-04-14 06:30 rt2870.bin

Since you've (presumably) been through the other stuff you've read about in the threads, I'll just cover one thing.  I have the _exact same device_, and this worked for me (although I set it up some six months ago or more, am using another distribution, and this may no longer be necessary and may be unrelated to your issue).

Execute the following as root (that means "use sudo before each command" if you don't have a root account, which I gather you Ubuntuans don't by default):
```
mkdir /etc/Wireless/RT3070STA
ln -s /etc/Wireless/RT2870STA/RT2870STA.dat /etc/Wireless/RT3070STA/RT3070STA.dat
```

_Explanation:_ When I set mine up, I noticed it seemed to be attempting to load the file /etc/Wireless/RT3070STA/RT3070STA.dat.  I assumed this to be an error and a result of the recent merging of the two drivers in the kernel tree.  So I created a "fake" RT3070STA.dat (a symlink) that actually points to the data file for the rt2870.

If it doesn't work, you can just remove it:```
rm -rf /etc/Wireless/RT3070STA
```

Also, while mine worked fine with kernel version 2.6.32, it has now stopped working since I upgraded to kernel version 2.6.33 (I think something else changed in the kernel's wireless architecture and an updated driver from ralink will be needed).

---

### Post by rencemc on 2010-05-19
I know I tried the RT3070STA symbolic link before, but I tried it again just to be sure - still no luck. I've never has this adapter working, so an upgrade didn't cause the issue. Thanks for you help and if you have anymore ideas, I would love to hear them. I will keep reading and plugging away.

---

### Post by BoneKracker on 2010-05-19
Well, before there was a linux driver available in the kernel, I had it working with ndiswrapper, so I imagine that still works, if you're willing to stoop to that.

---

### Post by rencemc on 2010-05-19
After reading other posts, I saw someone had a suggestion to do a tail -f on the var/log/messages & /var/log/syslog. When I did that. I saw that the adapter was looking for a driver for a Realtek RTL8192SU and not a RAlink RT2870. All the time I was trying to accommodate the wrong chipset :( Anyway, I downloaded the Realtek driver. It now seems to find the driver OK, but there is a wpa_supplicant part of it that is failing on compilation - the adapter is still useless. I am now trying to debug that issue.

---

### Post by BoneKracker on 2010-05-19
I thought you said you have a Belkin F5D8053, which is definitely based upon the Ralink Technologies RT2870 chipset.

---

### Post by BoneKracker on 2010-05-23
My apologies.  Apparently, they changed chipsets in the more recent versions of the device.

I noticed one of the to-dos for the kernel's 2.6.34 release was> staging: rtl8192su: add Support for Belkin F5D8053 v6
[http://lwn.net/Articles/386986/](http://lwn.net/Articles/386986/)

So, assuming you have version 6, that is indeed the driver (the version number should be on the back of the device).  Also, I assume you're building rtl8192su from source because you're using an earlier kernel version?

Did you have any luck with your compilation issue?

---

