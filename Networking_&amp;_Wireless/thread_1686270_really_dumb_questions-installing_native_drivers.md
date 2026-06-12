---
title: "really dumb questions-installing native drivers"
date: 2011-02-12
forum: Networking &amp; Wireless
---

### Post by newbiejosh on 2011-02-12
Just made the jump to Ubuntu, and until this install I considered myself very tech savvy.  Now not so much!  Built my new desktop, loaded Ubuntu 64 bit no problem.  But I'm having a terrible time figuring out how to load the native driver for my realtek wireless adapter.  I successfully un-tarred the file, and used the terminal to run the make command by using cd command to navigate to the file.  It returned a wall of text, and in my mind looked to work.  Next I go to run "./clean" in the same file location in the terminal and it returns
"ERROR: Module r8192s_usb does not exist in /proc/modules
ERROR: Module ieee80211_rsl does not exist in /proc/modules
ERROR: Module ieee80211_crypt_ccmp does not exist in /proc/modules
ERROR: Module ieee80211_crypt_tkip does not exist in /proc/modules
ERROR: Module ieee80211_crypt_wep does not exist in /proc/modules
ERROR: Module ieee80211_crypt does not exist in /proc/modules

Not completely sure if this is an issue, I try moving to the next step of instructions issuing the command "insmod 8712u.ko" in the terminal same file location and get the error message
insmod: error inserting '8712u.ko': -1 Operation not permitted

Im sure this is an easy fix.  I've tried running "sudo insmod 8712u.ko" from both that file directory, and from my home file directory.  My guess is I'm missing a step or need to be typing these commands in a different file directory in the terminal.

Thanks for your help!

---

### Post by newbiejosh on 2011-02-12
Okay,

After patrolling the forums I believe I have successfully installed the driver for my device (0bda:8172).  I was able to follow these commands:
sudo su
make
make install
exit
sudo reboot

My driver file now shows the 8712u.ko file, so it would appear that is has installed.  However when I issue the command:
josh@josh-desktop:~$ ifconfig wlan0 up
I get the error:
wlan0: ERROR while getting interface flags: No such device

ifconfig reports:
eth0      Link encap:Ethernet  HWaddr 00:25:22:86:80:da  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::225:22ff:fe86:80da/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1264 errors:0 dropped:0 overruns:0 frame:0
          TX packets:818 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1506637 (1.5 MB)  TX bytes:115722 (115.7 KB)
          Interrupt:42 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)
issuing lsusb shows:
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 046d:c31c Logitech, Inc. 
Bus 003 Device 002: ID 046d:c045 Logitech, Inc. Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191S WLAN Adapter
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

My wired connection is active, but right clicking on the networking icon doesn't show an "enable wireless" that i've seen talked about in the help forums.  I feel like I'm so close to getting this running!  Any help is much appreciated!

---

