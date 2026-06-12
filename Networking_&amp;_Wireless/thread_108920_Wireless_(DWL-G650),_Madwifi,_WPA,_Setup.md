---
title: "Wireless (DWL-G650), Madwifi, WPA, Setup"
date: 2005-12-27
forum: Networking &amp; Wireless
---

### Post by Ellarco on 2005-12-27
Hi. Im new to Kubuntu and stuck trying to get my wireless running. Ive been trying for days and have had to admit I need some help. The specs. are: Dell Inspiron 5150 with Dlink DWL-G650 (Rev.B) (PCMCIA). Breezy. I didnt install any drivers. Was trying to avoid using ndiswrapper since Madwifi comes with Breezy (right?) and is supposed to work with my card. During installation the network interface was detected but couldnt be configured properly. Initially I managed to get it working without encryption. I then tried to get WPA going with WPA-Supplicant which hasnt been a success. I cant even get back to the open network anymore! Id like to tell every step I took but even if I could remember it would be too big a post. Instead Ill dump the output from various commands and pray someone spots the problem. See below. The router/card work. I have it setup on my windows partition. Finally, I need to do it all via CLI due to that annoying bug with the "Administrator Mode" button in the GUI. Thanks for the help ... am loosing it here. El. ----- ```
 root@elmo-ii:~# cat /etc/network/interfaces # This file describes the network interfaces available on your system # and how to activate them. For more information, see interfaces(5). # The loopback network interface auto lo iface lo inet loopback address 127.0.0.1 netmask 255.0.0.0 # The wireless network interface auto ath0 allow-hotplug ath0 iface ath0 inet dhcp # The ethernet network interface iface eth0 inet dhcp # This is a list of hotpluggable network interfaces. # They will be activated automatically by the hotplug subsystem. mapping hotplug script grep map eth0 
``` ---- ```
 root@elmo-ii:~# iwconfig lo no wireless extensions. eth0 no wireless extensions. ath0 IEEE 802.11 ESSID:"" Mode:Managed Frequency:2.412 GHz Access Point: 00:0F:CC:3E:7D:00 Bit Rate:1 Mb/s Tx-Power:18 dBm Sensitivity=0/3 Retry:off RTS thr:off Fragment thr:off Encryption key:off Power Management:off Link Quality=0/94 Signal level=-95 dBm Noise level=-95 dBm Rx invalid nwid:338 Rx invalid crypt:0 Rx invalid frag:0 Tx excessive retries:0 Invalid misc:0 Missed beacon:0 sit0 no wireless extensions. 
``` Youll note the missing SSID in the output of iwconfig ... I set it, but a couple of seconds later it resets?? ---- ```
 root@elmo-ii:~# ifconfig ath0 Link encap:Ethernet HWaddr 00:0D:88:A2:2C:9A inet6 addr: fe80::20d:88ff:fea2:2c9a/64 Scope:Link UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1 RX packets:0 errors:24310 dropped:0 overruns:0 frame:24310 TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:200 RX bytes:0 (0.0 b) TX bytes:0 (0.0 b) Interrupt:16 Memory:f8c00000-f8c10000 eth0 Link encap:Ethernet HWaddr 00:0F:1F:1A:D1:BD inet6 addr: fe80::20f:1fff:fe1a:d1bd/64 Scope:Link UP BROADCAST MULTICAST MTU:1500 Metric:1 RX packets:0 errors:0 dropped:0 overruns:0 frame:0 TX packets:1 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:1000 RX bytes:0 (0.0 b) TX bytes:346 (346.0 b) Interrupt:17 lo Link encap:Local Loopback inet6 addr: ::1/128 Scope:Host UP LOOPBACK RUNNING MTU:16436 Metric:1 RX packets:37 errors:0 dropped:0 overruns:0 frame:0 TX packets:37 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:0 RX bytes:3094 (3.0 KiB) TX bytes:3094 (3.0 KiB) sit0 Link encap:IPv6-in-IPv4 inet6 addr: ::127.0.0.1/96 Scope:Unknown UP RUNNING NOARP MTU:1480 Metric:1 RX packets:0 errors:0 dropped:0 overruns:0 frame:0 TX packets:0 errors:4 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:0 RX bytes:0 (0.0 b) TX bytes:0 (0.0 b) 
``` ---- ```
 root@elmo-ii:~# iwlist ath0 scanning ath0 Scan completed : Cell 01 - Address: 00:0F:CC:3E:7D:00 ESSID:"instant" Mode:Master Frequency:2.442 GHz (Channel 7) Quality=41/94 Signal level=-54 dBm Noise level=-95 dBm Encryption key:off Bit Rate:1 Mb/s Bit Rate:2 Mb/s Bit Rate:5 Mb/s Bit Rate:6 Mb/s Bit Rate:9 Mb/s Bit Rate:11 Mb/s Bit Rate:12 Mb/s Bit Rate:18 Mb/s Bit Rate:22 Mb/s Bit Rate:24 Mb/s Bit Rate:36 Mb/s Bit Rate:48 Mb/s Bit Rate:54 Mb/s Extra:bcn_int=100 
``` ---- ```
 root@elmo-ii:~# dhclient ath0 There is already a pid file /var/run/dhclient.pid with pid 0 Internet Systems Consortium DHCP Client V3.0.2 Copyright 2004 Internet Systems Consortium. All rights reserved. For info, please visit http://www.isc.org/products/DHCP sit0: unknown hardware address type 776 sit0: unknown hardware address type 776 Listening on LPF/ath0/00:0d:88:a2:2c:9a Sending on LPF/ath0/00:0d:88:a2:2c:9a Sending on Socket/fallback DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7 DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 14 DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 12 DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 14 DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10 DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4 No DHCPOFFERS received. No working leases in persistent database - sleeping. 
``` ----

---

### Post by Lambert on 2005-12-27
remove the allow-hotplug line and the auto ath0 line

under map eth0 add map ath0

then run these commands

sudo /etc/init.d/network stop && sudo /etc/init.d/network start

sudo /etc/init.d/pcmcia stop && sudo /etc/init.d/pcmcia start

Now can you connect again with out encryption? if not consider rebooting.

Post back if it doesn't work

Once you get it working follow this howto on wpa
[https://wiki.ubuntu.com/WPAHowto](https://wiki.ubuntu.com/WPAHowto)

---

### Post by Ellarco on 2005-12-27
Thanks. I did as you said. Had to reboot and run dhclient before it worked but it did.

Now I have unsecured access again, although it is obscenely slow. About 1/10 the speed of a dial-up I would guess. Any ideas?

I also welcome help with wpa-supplicant ...

And regarding the hot-plug bit you told me to remove. As part of one of the many wpa-supp guides I followed I downloaded and installed ifplugd ... somehow hot-plug related I think. Anything I should do about this?

Thanks again.

---

### Post by Lambert on 2005-12-27
ifplugd is not necessary. remove that to see if it improves your performance. ubuntu comes with hotplugging support which is what the map ath0 line I gave you accomplishes

My situation doesn't warrant use of wpa, I use wep and have no problems. So I can't offer much help here. Some day just to play I want to give wpa a try to see the process and document my results.

with your card I 've seen a couple posts that use the wiki instructions I linked to in my last post to get wpa working with no problems.

---

### Post by Ellarco on 2005-12-27
Will do. Is

```

dpkg -r ifplugd

```

the way to go about this ... it wont leave nothing left behind?

---

### Post by Lambert on 2005-12-27
dpkg --purge package.deb

-r removes it but leaves behind config files if you want to reinstall later so you have same settings. --purge removes the same items but also the config files.

---

### Post by Ellarco on 2005-12-27
Ah ... One more piece of info accumulated. Just several million pieces more to go and Ill be able to use this thing.

:)

---

### Post by firecat53 on 2005-12-27
I've made several posts in the past regarding Madwifi and WPA. I use the DWL-G630 quite happily with that combination. Try searching on my previous posts....you should find my /etc/network/interfaces and wpa_supplicant.conf along with some instructions for compiling from source (which unfortunately seems to work sometimes when the stock drivers won't).

Good luck,
Scott

---

