---
title: "Checking which wireless driver I am using?"
date: 2011-08-24
forum: Networking &amp; Wireless
---

### Post by 00145217 on 2011-08-24
Hello, I did some search and found that I should use
sudo lshw -C network
and found that 
configuration: broadcast=yes driver=usb driverversion=2.6.38-11-generic-pae firmware=N/A ip=10.134.155.132 link=no multicast=yes wireless=IEEE 802.11bgn
However, I want to use the carl9170 driver since I need some functions in it.
I installed the compat-wireless through the backport repository.
I was wondering if there is a way to switch or force ubuntu to use carl9170?

Thank you

---

### Post by praseodym on 2011-08-24
Hello,

please show the following:

```
lsmod | grep 9170
dmesg | grep 9170
lsusb
```
If "lsmod" shows two drivers, blacklist the ar9170usb via:

```
echo "blacklist ar9170usb" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
and reboot. Since Natty 11.04 both drivers are implemented into the kernel and the "old one" ar9170usb needs to be blacklisted.

---

### Post by 00145217 on 2011-08-25
Thank you for your reply,
I tried 
lsmod | grep 9170
dmesg | grep 9170
both does not give any out put

lsusb gives
```
Bus 002 Device 005: ID 0cf3:7015 Atheros Communications, Inc. 
Bus 002 Device 003: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0461:4d22 Primax Electronics, Ltd 
Bus 001 Device 003: ID 413c:2107 Dell Computer Corp. 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

I was wondering if it is because I blacklisted ar9170usb awhile ago and yesterday remove the blacklisted line and now it does not show up at all.
Does this means that my usb wireless card does not have a driver right now? 

Thank you
Best Regards,

---

### Post by praseodym on 2011-08-25
Try the newer module:

```
sudo modprobe -v carl9170
sudo service network-manager restart
```
Controls:
```
dmesg | grep 9170
iwconfig
sudo iwlist scan
rfkill list
```

---

### Post by 00145217 on 2011-08-26
Again, thank you very much for your reply.
I did what you suggested and 
dmesg | grep 9170
showed me 
```
[165152.609791] usbcore: registered new interface driver carl9170
```

Would it be safe to assume that usb card is using the carl9170 now?
What is weird is that I tried
sudo lshw -C network
and it does not show me my wireless any more only the ethernet interface.

Or lshw -C network does not work with usb?

did iwconfig and
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11bgn  Mode:Monitor  Frequency:2.412 GHz  Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

I'm not sure what 
sudo iwlist scan
do but it give me 
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan1     Interface doesn't support scanning : Network is down
```

rfkill list
give me
```
1: phy1: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

Again thank you very much for your help.  In the means while, I will try out whatever I can to check.

update: I did restart and sudo lshw -C network give me the wireless interface, but the output still give me
configuration: broadcast=yes driver=usb driverversion=2.6.38-11-generic-pae firmware=N/A link=no multicast=yes wireless=IEEE 802.11bgn

The driver still say usb, which I am not sure what it is.

---

### Post by praseodym on 2011-08-26
You may try some different firmware versions for the monitor mode:

[http://www.kernel.org/pub/linux/kernel/people/chr/carl9170/fw/](http://www.kernel.org/pub/linux/kernel/people/chr/carl9170/fw/)

You have to copy the file to /lib/firmware and reboot, respectively

---

### Post by Merlins on 2011-10-04
Hi - I am getting very similar symptoms to the OP on 11.04 i.e. lshw -C network gives:

description: Wireless interface
physical id: 1
bus info: firewire@1
logical name: wlan1
serial: b0:48:7a:87:aa:51
capabilities: ethernet physical wireless
configuration: broadcast=yes driver=usb driverversion=2.6.38-11-generic firmware=N/A ip=192.168.1.5 link=yes multicast=yes wireless=IEEE 802.11bgn

and iwconfig gives:

wlan1     IEEE 802.11bgn  ESSID:"TALKTALK-15ED10"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 04:C0:6F:15:ED:18   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=45/70  Signal level=-65 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:315   Missed beacon:0

Note the Bit Rate=1 Mb/s - the TP-WN822N USB adapter is 300Mb/s.

Why does lshw have driver=usb and firmware=N/A?  Although the adapter is working, I suspect it may not be optimal.  Did Op solve the problem in the end or any other suggestions?

---

### Post by Merlins on 2011-10-13
Just to say that I upgraded to 11.10, and my wireless TP-WN822N adapter is now using the ath9k_htc driver and a variable speed of around 100 Mb/s, so I am happier.  Its also flashing the led, which it never did before.

Andy.

---

