---
title: "netgear wirless adapter installed but no internet"
date: 2013-06-06
forum: Networking &amp; Wireless
---

### Post by asan42 on 2013-06-06
[COLOR=#000000]*i am able to see the wireless WNA3100 USB adapter and says it is connected to my wireless router. It will even connect to sites for about 90 seconds then it just times out constantly. Can restart and surf before it times out. I do use WPA2 encryption but it seems to still cause issues even if open network.*[/COLOR]

[COLOR=#000000]*any suggestions? running 12.04    i keep on getting a "network service discovery disabled" msg.*[/COLOR]

---

### Post by asan42 on 2013-06-06
asan@minepc:~$ lsusb
Bus 001 Device 002: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]
Bus 002 Device 004: ID 0781:5561 SanDisk Corp. 
Bus 005 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 005 Device 003: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
asan@minepc:~$ ndiswrapper -l
bcmwlhigh5 : driver installed
	device (0846:9011) present
asan@minepc:~$ modprobe ndiswrapper
asan@minepc:~$ /desktop# ndiswrapper -e bcmwlhigh5
bash: /desktop#: No such file or directory
asan@minepc:~$ dmesg | grep ndis
[   14.334313] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[   15.743295] ndiswrapper: driver bcmwlhigh5 (Netgear,05/05/2009, 5.10.79.30) loaded
[   15.998441] usbcore: registered new interface driver ndiswrapper
asan@minepc:~$ arch
x86_64
asan@minepc:~$ iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11g  ESSID:"belkin.991"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 08:86:3B:D4:19:91   
          Bit Rate=117 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:67/100  Signal level:-53 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:40  Invalid misc:28310   Missed beacon:0


asan@minepc:~$ 


any ideas?

---

### Post by 00101010 on 2013-07-12
Call it primitive or simple but I'm new to ubuntu and don't know many technical fixes. What I do know is that my WNA3100 used to freeze up whenever the system first started and wouldn't provide any internet connection until I unplugged it and plugged it back in. Then it would continue to connect to a router without timing out or connection without using the internet.

---

### Post by paul19 on 2013-08-12
I have exactly the same issue. This i already postet in an other thread: 

[COLOR=#000000]Hey there. I also have a [/COLOR][COLOR=#417394]WNA3100[/COLOR][COLOR=#000000] and I got it working with ndiswrapper and the driver [/COLOR][COLOR=#333333][FONT=Lucida Grande]bcmwlhigh5.inf[/FONT][/COLOR][COLOR=#000000]. I have to say i am using linux mint but i think it should be the same.[/COLOR]

[COLOR=#000000]Then I got a new router (Technicolor TC7200) which replaced the very old one from my provider and now i have troubles with the connection (with Windows 8 dualboot I have no issues - works like a charm):[/COLOR]

[COLOR=#000000]When I download with full speed or try to open multiple websites at the same time then the connection is interrupted after 1 minute. I can not surf anymore, no more website is available and all downloads are down to 0 kBit/s. But the manager shows it is connected.[/COLOR]
[COLOR=#000000]I have tried to [/COLOR][COLOR=#333333][FONT=Lucida Grande]limit the up and downstream with:[/FONT][/COLOR]

[COLOR=#000000]Code:
sudo apt-get install trickle
sudo -s trickle -u 5000 -d 5000 apt-get update[/COLOR]
[COLOR=#000000]but still the same issue. I must say that i only installed ndiswrapper and then immediately the driver. No more editing apart from editing the up- and downstream with tickle.[/COLOR]

[COLOR=#000000]Anyone knows a solution?[/COLOR]

---

### Post by kurt18947 on 2013-08-12
Given the amount of posts about that particular adapter, my solution would be a replacement, I'm afraid.  There are too many other better/easier choices out there.  For me, if there is no native linux support at all and NDISwrapper is the only way, that adapter has no place for me.  Of course if you view it as a learning experience, carry on.

---

