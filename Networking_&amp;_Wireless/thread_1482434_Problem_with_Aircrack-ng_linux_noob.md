---
title: "Problem with Aircrack-ng linux noob"
date: 2010-05-13
forum: Networking &amp; Wireless
---

### Post by AlwaysSunny on 2010-05-13
This is my first post, so first off I'd to say thank you for all the guides, howto's and tutorials that have got me to this point, I only started using linux around 5 days ago and have tried and tried to use all the resources available on forums and google to fix this problem, but nothing has worked...  I'm hoping someone with better knowledge than this humble begginer can help or at least give me a general nudge... I like to work things out for myself most of the time but I've hit a brick wall.
Firstly,  some info...
 
 
 
I'm trying to use the aircrack-ng suite
here is the output of lspci -nn  (for my wireless card)
 
```
03:00.0 Network controller [0280]: Broadcom Corporation BCM4328 802.11a/b/g/n [14e4:4328] (rev 03)
```
 
here is my current ifconfig for my wireless card eth1
 
```
eth1      Link encap:Ethernet  HWaddr 00:21:00:0e:5a:64  
          inet addr:192.168.0.188  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::221:ff:fe0e:5a64/64 Scope:Link
          UP BROADCAST RUNNING  MTU:1500  Metric:1
          RX packets:72252 errors:1 dropped:0 overruns:0 frame:113935
          TX packets:49464 errors:61 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:94750718 (94.7 MB)  TX bytes:5288781 (5.2 MB)
          Interrupt:16
```
 
and iwconfig...
 
```
eth1      IEEE 802.11abgn  ESSID:"dlink"  
          Mode:Managed  Channel:157  Access Point: 00:11:95:CC:D5:0D   
          Bit Rate=11 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Managementmode:All packets received
          Link Quality=1/5  Signal level=-80 dBm  Noise level=-93 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:66  Invalid misc:0   Missed beacon:0
```

I'm using Ubuntu 10.4   2.6.32-21
 
I installed these drivers for my wireless card, and I can connect to my wireless network
and use the internet. 
```
http://www.broadcom.com/support/802.11/linux_sta.php
```

Ok... so I hope that is enough info about the card and whats running it right now...
Here is the problem...
I cannot seem to  get airodump-ng to work....  here's the output of airmon-ng start eth1 #
r```
oot@boomshackalacka:~# airmon-ng start eth1

Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!
PID Name
825 avahi-daemon
826 avahi-daemon
838 NetworkManager
906 wpa_supplicant
31761 dhclient
Process with PID 31761 (dhclient) is running on interface eth1

Interface Chipset  Driver
eth1  Unknown   wl (monitor mode enabled)

```

strangley, I see it didn't create a seperate monitoring device which I have read about, usually mon0... ??
Anyways, it says eth1 is in monitoring mode... please note it is not recognizing the chipset...
so I go to use airodump-ng eth1...
```
root@boomshackalacka:~# airodump-ng eth1
ioctl(SIOCSIWMODE) failed: Invalid argument
ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211,
ARPHRD_IEEE80211_FULL or ARPHRD_IEEE80211_PRISM instead.  Make
sure RFMON is enabled: run 'airmon-ng start eth1 <#>'
Sysfs injection support was not found either.

```

This is where I hit the brick wall... 
Here's what I think.. I'm probably wrong but I see so many people posting saying 'what do I do', well here's what I think and hopefully you guys can tell me if I'm right or wrong.
 
 
1. I've installed the sta driver, rather than the b43 driver, the sta driver is the problem
2. the sta driver needs to be patched to support packet injection?
3. My card, based on the lspci output, is not compatible with aircrack
4. I just need to install a different driver, maybe the b43, bcm43xx, or b43 legacy (and injection patch the new driver install?)
Any comments, suggestions or general nudges in the right direction are very much appreciated
 
 
Thanks 
AlwaysSunny

---

### Post by Zvenne on 2010-05-22
Bump! I have the same problem as TS and I really want it solved. Please help us, anyone!

---

### Post by purelinuxuser on 2010-05-22
Ignore this post, it was a duplicate.

---

### Post by purelinuxuser on 2010-05-22
AlwaysSunny - Sorry, but your wireless card does **not** support aircrack-ng, as your driver options do not support Monitor mode.

[LIST]
[*]b43/b43legacy do not support your wireless card (it's in the works, so wait for further updates and progress):popcorn:
[*]Broadcom's STA wireless only supports Managed/Ad-hoc mode
[*]Ndiswrapper only supports Managed/Ad-hoc mode
[/LIST]
Zvenne - Do you have the exact same wireless card as AlwaysSunny?  If not, post the output of
```
lspci
```
```
iwconfig
```
```
lshw -c network
```
and I'll see if I can help you.  Also, this is a week-old thread, you probably should have started a new one. ;)

---

