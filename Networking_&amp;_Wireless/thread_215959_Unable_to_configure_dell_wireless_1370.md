---
title: "Unable to configure dell wireless 1370"
date: 2006-07-14
forum: Networking &amp; Wireless
---

### Post by will103 on 2006-07-14
Hi, I am having some problems with getting my wireless card to work. 

I am using the following card: dell wireless 1370 WLAN Mini-PCI Card

on a Dell Inspiron 1300 running Dapper.

I have looked around the Ubuntu forums and followed the instructions laid out in the following link-


[http://ubuntuforums.org/showthread.php?t=120383](http://ubuntuforums.org/showthread.php?t=120383)


Unfortunately this hasn't worked for me and I was looking for some pointers on what to try next.

Here is my shell output from the installation process outlined in the above link:-

sudo /usr/sbin/ndiswrapper -i /usr/local/wlan_1370/DRIVER/bcmwl5.inf
bcmwl5 is already installed. Use -e to remove it

root:~# /usr/sbin/ndiswrapper -l
Installed ndis drivers:
bcmwl5          driver present, hardware present

root:~# /usr/sbin/ndiswrapper -m
modprobe config already contains alias directive

root:~# /sbin/depmod -a
root:~# modprobe ndiswrapper
root:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"default"  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Encryption key:BA00-3000-00   Security mode:open
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

root:~# dmesg | grep ndiswrapper
[17179594.580000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
root:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:22:A0:F4:F5
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:372 (372.0 b)  TX bytes:372 (372.0 b)

root:~# modprobe ndiswrapper
root:~# ndiswrapper -m
modprobe config already contains alias directive

When I try to activate the card and connect I get the following error:

SIOCGIFFLAGS error: No such device

Any help would be great. Thankyou in advance.

Will103

---

### Post by Jagot on 2006-07-15
I have the same card and same laptop.  This is how I get it working:

```
sudo ndiswrapper -i ~/Desktop/bcmwl5/bcmwl5.inf
sudo modprobe ndiswrapper
sudo ndiswrapper -m

echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo rmmod bcm43xx
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
```

Then it's a matter of activating and filling in network settings.

The post you followed was for 5.10.  The problem with Dapper is that it comes supplied with drivers for Broadcom chipsets, but it doesn't seem to work for some of them.  That is why you need the blacklisting stuff - because the drivers built into Dapper need to be told not to take over, and to let ndiswrapper handle the drivers.

---

