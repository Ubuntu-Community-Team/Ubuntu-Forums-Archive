---
title: "RNX-ESYN1 rt3070 chipset (install) on Ubuntu 9.10"
date: 2010-03-07
forum: Networking &amp; Wireless
---

### Post by zenek89 on 2010-03-07
Hi! I'm running **ubuntu 9.10** and I'm trying to get my **RNX-ESYN1 **with **rt3070** chipset to work. I've tried to download and install the newest drivers from ralink's page and when I type "**lsusb**" in a terminal I get this "**Bus 001 Device 002: ID 148f:3070 Ralink Technology, Corp**." so that means if it's plugged in and should work. In the network manager it shows only my PCI broadcom card, but not my USB stick. When I type in the "**iwconfig" **command I get the **"ra0"** but not in the network manager.

ra0       RT2870 Wireless  ESSID:""  Nickname:""
          Mode:Auto  Frequency=2.412 GHz  
          Link Quality=10/100  Signal level:0 dBm  Noise level:-143 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I blacklisted these two:

blacklist rt2800usb
blacklist rt2870sta

and still nothing changed, I got it to work once, but I reinstalled my system and can't get it to work again. I don't know if I'm doing something wrong. Last time I did it, both of my wifi adapters were showing up in the network manager at once and were working great. I need my ***Ralink ***to use with the aircrack which doesn't work with my broadcom.
Please help me..

---

### Post by chili555 on 2010-03-07
> I blacklisted these two:

blacklist rt2800usb
blacklist rt2870staYou are on the right track. With the device inserted, please do:```
sudo modprobe rt3070sta
```Now does it work? If not, please post:```
dmesg | grep -e rt2 -e rt3
```If so, please do:```
sudo su
echo rt3070sta >> /etc/modules
```Let us know.

---

### Post by zenek89 on 2010-03-07
I still didn't get it to work, there weren't any errors with your commands, they all went thru without problem but it still didn't help me, I don't see any difference.

[ATTACH]149329[/ATTACH]

there are shown networks detected by PCI broadcom only. Any guess on what to do?

---

### Post by chili555 on 2010-03-07
You mean that there was no output from:```
dmesg | grep -e rt2 -e rt3
```I would love to do some diagnostics.

---

### Post by zenek89 on 2010-03-07
root@zenus-laptop:~# **dmesg | grep -e rt2 -e rt3**
[   12.997443] usbcore: registered new interface driver rt2870
[ 2509.274188] <==== rt28xx_init, Status=0


that's all what showed up after a command. Idk if I did it correctly, I just copied and pasted.

By the way, when I tried to put **RALINK **in monitor mode using **airodump-ng ra0 ,** it didn't detect any networks

---

### Post by chili555 on 2010-03-07
> there are shown networks detected by PCI broadcom only.What?? Are you trying to get two wireless cards going ar once? I very highly doubt Network Manager will allow that.

---

### Post by zenek89 on 2010-03-07
> I very highly doubt Network Manager will allow that.     last time I tried to run two wireless cards at once, it worked with Network Manager. It was showing networks visible by **broadcom **and **ralink **separately on one list. 

By the way, even when **broadcom** is off, **ralink **doesn't show up in **network manager** and doesn't work with **aircrack-ng** either

---

### Post by chili555 on 2010-03-07
May I see:```
cat /etc/modules
lsmod | grep rt
```Thanks.

---

### Post by zenek89 on 2010-03-07
```
root@zenus-laptop:~# cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc
rt3070sta

root@zenus-laptop:~# lsmod | grep rt
rt3070sta             558560  1 
parport                40528  2 ppdev,lp
root@zenus-laptop:~# 


```

thank you

---

### Post by chili555 on 2010-03-07
Please let me see:```
iwconfig
```Thanks.

---

### Post by zenek89 on 2010-03-07
[HTML]lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11abgn  ESSID:"Jumpstart-P1-a273c4"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:19:5B:51:FF:3D   
          Bit Rate=36 Mb/s   Tx-Power:32 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received
          
ra0       RT2870 Wireless  ESSID:""  Nickname:"RT2870STA"
          Mode:Monitor  Frequency=2.432 GHz  Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[/HTML]

lo <---- unknown
eth0 <---- ethernet
eth2 <----broadcom
ra0 <----ralink

---

### Post by chili555 on 2010-03-07
> ra0       RT2870 Wireless  ESSID:""  Nickname:"RT2870STA"
          Mode:[COLOR="Red"]Monitor[/COLOR]In order to do your airmon-ng stuff, your card needs to be in monitor mode. However, then, it is not a valid interface for Network Manager to use to connect to the internet. When you are done with monitoring, do:```
sudo iwconfig ra0 mode managed
```

---

### Post by zenek89 on 2010-03-07
[FONT=monospace]a monitor mode (airodump-ng) using **Ralink** finds only 2 networks in 5 minutes, while **NM** using **broadcom** shows about 16 in 1 minute, after monitoring I switched the mode for **Ralink**, and I got it as **AUTO**

[HTML]ra0       RT2870 Wireless  ESSID:""  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.457 GHz  Bit Rate=1 Mb/s  
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[/HTML]

**NM** still doesn't show **Ralink** even with **broadcom off**

[/FONT]

---

### Post by zenek89 on 2010-03-07
I'm running out of ideas, do U think that if I was trying to install two different versions of drivers could matter? I didn't remove old before installing new.. in a directory **/etc/wireless/** I have two folders **"RT2870STA" & "RT3070STA" **where both contain **RT2870STA.dat**

---

### Post by chili555 on 2010-03-07
Please try:```
cd /etc/Wireless/RT3070STA
sudo cp RT2870STA.dat RT3070STA.dat
sudo rmmod -f rt3070sta
sudo modprobe rt3070sta
```Does the performance change?

The only other thing you might try is to blacklist rt3070sta, remove rt2870sta from blacklist and explicitly load rt2870sta in */etc/modules*. In other words, reverse which driver we are using. Both support your device.> chili@LAPTOP60:~$ modinfo rt3070sta | grep 3070
filename:       /lib/modules/2.6.31-20-generic/kernel/drivers/staging/rt3070/rt3070sta.ko
alias:          usb:v07B8p3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v[COLOR="Blue"]148F[/COLOR]p[COLOR="Blue"]3070[/COLOR]d*dc*dsc*dp*ic*isc*ip*
chili@LAPTOP60:~$ modinfo rt2870sta | grep 3070
alias:          usb:v07B8p3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v[COLOR="Blue"]148F[/COLOR]p[COLOR="Blue"]3070[/COLOR]d*dc*dsc*dp*ic*isc*ip*I'm just about out of ideas, too.

---

### Post by zenek89 on 2010-03-07
> The only other thing you might try is to blacklist rt3070sta, remove rt2870sta from blacklist and explicitly load rt2870sta in */etc/modules*. In other words, reverse which driver we are using. Both support your device.     You mean to switch in blacklist, and something else, or just switch them?

according to this:

```
root@zenus-laptop:~# cd /etc/Wireless/RT3070STA
root@zenus-laptop:/etc/Wireless/RT3070STA# sudo cp RT2870STA.dat RT3070STA.dat
root@zenus-laptop:/etc/Wireless/RT3070STA# sudo rmmod -f rt3070sta
_**ERROR: Removing 'rt3070sta': Resource temporarily unavailable**_
root@zenus-laptop:/etc/Wireless/RT3070STA# sudo modprobe rt3070sta
root@zenus-laptop:/etc/Wireless/RT3070STA# 

```
I got an error.. (does it matter?), I didn't get any better performance anyway...

do You think if reinstalling a whole system could help? this way I would get it fresh without all mess... I could do it even now, but I was working a lot on my broadcom

---

### Post by zenek89 on 2010-03-07
I've blacklisted rt3070sta instead of rt2870sta and switched rt3070sta to rt2870sta in /etc/modules.

and it helped right after restart !! I got both wireless adapters running at once, only one thing that worries me now is **Ralink's **performance, **Broadcom **works fine.

---

### Post by zenek89 on 2010-03-07
RNX-EASYN1 rt3070 running on rt2870sta

---

