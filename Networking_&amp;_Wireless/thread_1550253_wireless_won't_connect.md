---
title: "wireless won't connect"
date: 2010-08-10
forum: Networking &amp; Wireless
---

### Post by gweinstein on 2010-08-10
I am trying to salvage (kind of) old hardware: toshiba l25-s119.  The internal wireless adapter is detected, but it won't connect.  I thought it was a hardware problem, so I got a cheap usb adapter, and that one exhibits the same problems.  I thought it had to do with the network manager, so I tried wicd instead; still the same problem.  I thought it had to do with the security settings, so I set my router to unsecured: same problem.  Tried various fixes found around the internet, still no luck.  At a loss.  Here is the output from ifconfig -a:

```
wlan0     Link encap:Ethernet  HWaddr 00:11:f5:b0:43:07  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:196 (196.0 B)
```and here is the output from lshw -C network:

  ```
*-network:1
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 4
       bus info: pci@0000:09:04.0
       logical name: wlan0       version: 01
       serial: 00:11:f5:b0:43:07
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:22 memory:d0200000-d020ffff
```Any help greatly appreciated!

---

### Post by utilitytrack on 2010-08-10
> **gweinstein said:**
> Tried various fixes found around the internet, still no luck.

Hello, these fixes that you tried has led to the fact that the network subsystem can not set the Loopback and Ethernet interfaces. More simple way for you in this case is completely reinstall your Ubuntu (fresh is 10.04) and if problems will be again, ask for help on this forum.

---

### Post by gweinstein on 2010-08-10
utilitytrack: Thanks for your reply.  Actually, ethernet works.  Only wireless doesn't.

---

### Post by utilitytrack on 2010-08-10
> **gweinstein said:**
> Actually, ethernet works.

This is in contradiction with following data:

> **gweinstein said:**
> Here is the output from ifconfig -a:

```
wlan0     Link encap:Ethernet  HWaddr 00:11:f5:b0:43:07  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:196 (196.0 B)
```

Or you specially gave here incomplete data in order to confuse us?

---

### Post by gweinstein on 2010-08-10
I posted the data from the wireless adapter.  I did not post the data from the ethernet adapter since that one works just fine and I did not think it was relevant.  

And no, it was not done intentionally to confuse you.

---

### Post by utilitytrack on 2010-08-10
> **gweinstein said:**
> I posted the data from the wireless adapter.  I did not post the data from the ethernet adapter since that one works just fine and I did not think it was relevant.

It's your mistake. All information that you post on forum and that related to network subsystem must be complete and full.

Ok. Do you use a NetworkManager or some other like Wicd? Completely uninstall it.

Next, please give on forum some diagnostical info:

```
$ lsb_release --all
$ uname -a
$ cat /proc/cmdline
$ lspci -nn | grep -E 'Ethernet|Network'
$ dmesg | grep -E -i 'ath|wlan|wifi|No\ probe\ response'
$ ps -ef | grep -E -i 'supplicant|Netwo|nm-app'
# ifconfig -a
# ls -R /lib/modules/`uname -r`/kernel/drivers/net/wireless/ath/*
# lsmod | grep -E 'ath|cfg80211'
# cat /etc/network/interfaces
# iwconfig
# iwlist scan
# ls -l /etc/modprobe.d/*
# grep -E 'CONFIG_ATH|MAC80211' /boot/config-`uname -r`
# modinfo ath5k | grep -E 'version\:|srcversion' && modinfo ath9k | grep -E 'version\:|srcversion'

```
Also: 1) You are sure that all BIOS options related to network (like "Disable Radio" or "Disable mini-pci") is properly configured? Check it. 2) Your NIC able to work with Other OS? 3) Please say which distros of Linux you tried to install and results.

---

### Post by gweinstein on 2010-08-11
1) LAN is enabled in BIOS.  That's the only option which refers to networking.
2) I am not sure whether adapter currently works with other OS.  I will check with Koppix live CD and post again.
3) See (2).

I should add that the wireless adapter seems to work. In fact, it detects wireless networks (those show in NetworkManager).  It fails when trying to connect.

Thanks in advance for the help.  Here is the info.

```
weinstei@koala:~$ lsb_release --all
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04.1 LTS
Release:	10.04
Codename:	lucid

```

```
weinstei@koala:~$ uname -a
Linux koala 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 06:07:29 UTC 2010 i686 GNU/Linux

```

```
weinstei@koala:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=5fb49363-14af-4cc5-a48d-b955c194f0bc ro quiet splash

```

```
weinstei@koala:~$  lspci -nn | grep -E 'Ethernet|Network'
09:02.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
09:04.0 Ethernet controller [0200]: Atheros Communications Inc. AR2413 802.11bg NIC [168c:001a] (rev 01)

```

```
weinstei@koala:~$ dmesg | grep -E -i 'ath|wlan|wifi|No\ probe\ response'
[    1.152301] device-mapper: multipath: version 1.1.0 loaded
[    1.152308] device-mapper: multipath round-robin: version 1.0.0 loaded
[   20.220509] ath5k 0000:09:04.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   20.220668] ath5k 0000:09:04.0: registered as 'phy0'
[   22.218417] ath: EEPROM regdomain: 0x64
[   22.218425] ath: EEPROM indicates we should expect a direct regpair map
[   22.218433] ath: Country alpha2 being used: 00
[   22.218436] ath: Regpair used: 0x64
[   22.308668] ath5k phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
[   22.564480] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

```
weinstei@koala:~$ ps -ef | grep -E -i 'supplicant|Netwo|nm-app'
root       626     1  0 16:02 ?        00:00:03 NetworkManager
root       656     1  0 16:02 ?        00:00:01 /sbin/wpa_supplicant -u -s
root       662   626  0 16:02 ?        00:00:00 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-eth0.pid -lf /var/lib/dhcp3/dhclient-b0e5567f-2276-4fed-b1dc-0fdbb4f0489b-eth0.lease -cf /var/run/nm-dhclient-eth0.conf eth0
weinstei  4127     1  0 18:18 ?        00:00:08 nm-applet --sm-disable
weinstei  4648  4614  0 21:50 pts/0    00:00:00 grep --color=auto -E -i supplicant|Netwo|nm-app

```

```
weinstei@koala:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:c0:9f:f5:40:43  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fef5:4043/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:216881 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49919 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:307219129 (307.2 MB)  TX bytes:4142216 (4.1 MB)
          Interrupt:21 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:11:f5:b0:43:07  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

```
weinstei@koala:~$ ls -R /lib/modules/`uname -r`/kernel/drivers/net/wireless/ath/*
/lib/modules/2.6.32-24-generic/kernel/drivers/net/wireless/ath/ath.ko

/lib/modules/2.6.32-24-generic/kernel/drivers/net/wireless/ath/ar9170:
ar9170usb.ko

/lib/modules/2.6.32-24-generic/kernel/drivers/net/wireless/ath/ath5k:
ath5k.ko

/lib/modules/2.6.32-24-generic/kernel/drivers/net/wireless/ath/ath9k:
ath9k.ko

```

```
weinstei@koala:~$  lsmod | grep -E 'ath|cfg80211'
ath5k                 121792  0 
mac80211              205146  1 ath5k
ath                     7611  1 ath5k
cfg80211              126517  3 ath5k,mac80211,ath
led_class               2864  1 ath5k

```

```
weinstei@koala:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

```

```
weinstei@koala:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

```
weinstei@koala:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1C:10:0D:D6:E7
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"Kelsey"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000034eba7068e2
                    Extra: Last beacon: 11740ms ago
                    IE: Unknown: 00064B656C736579
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD09001018020014000000
          Cell 02 - Address: 00:1F:B3:65:CA:E9
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"EGEA"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000007c2cc356
                    Extra: Last beacon: 11296ms ago
                    IE: Unknown: 000445474541
                    IE: Unknown: 010882848B8C12969824
                    IE: Unknown: 03010A
                    IE: Unknown: 0706555320010B1B
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 3204B048606C
          Cell 03 - Address: 00:1B:2F:09:36:1E
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=15/70  Signal level=-95 dBm  
                    Encryption key:on
                    ESSID:"Matrix"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000029f7ed5181
                    Extra: Last beacon: 11764ms ago
                    IE: Unknown: 00064D6174726978
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0900037F0101001DFF7F
                    IE: Unknown: DD0C00037F020101690002A44000
                    IE: Unknown: DD1A00037F0301000000001B2F09361E021B2F09361E64002C011D08

```

```
weinstei@koala:~$ grep -E 'CONFIG_ATH|MAC80211' /boot/config-`uname -r`
CONFIG_MAC80211=m
CONFIG_MAC80211_RC_MINSTREL=y
# CONFIG_MAC80211_RC_DEFAULT_PID is not set
CONFIG_MAC80211_RC_DEFAULT_MINSTREL=y
CONFIG_MAC80211_RC_DEFAULT="minstrel"
CONFIG_MAC80211_MESH=y
CONFIG_MAC80211_LEDS=y
CONFIG_MAC80211_DEBUGFS=y
# CONFIG_MAC80211_DEBUG_MENU is not set
CONFIG_MAC80211_HWSIM=m
CONFIG_ATH_COMMON=m
CONFIG_ATH5K=m
# CONFIG_ATH5K_DEBUG is not set
CONFIG_ATH9K=m
CONFIG_ATH9K_DEBUG=y

```

```
weinstei@koala:~$ modinfo ath5k | grep -E 'version\:|srcversion' && modinfo ath9k | grep -E 'version\:|srcversion'
version:        0.6.0 (EXPERIMENTAL)
srcversion:     A16C39E4FEDD01B0BABE06E
srcversion:     2F7AB8CABC2203ED7E7A220

```

---

### Post by gweinstein on 2010-08-12
**Update:** 

[LIST]
[*]Knoppix was a dudd.
[*]Lubuntu 10.04 gave better results.
[*]On the Live CD, the wireless seems to connect OK, and the  connection seems stable (currently installing on the HD).  
[*]Ping works flawlessly.  So does Lynx.  
[*]However, the graphical browser (Chromium, in the Lubuntu case) stalls after a page or so.  Happens also with Pidgin.  Didn't try other network apps.
[/LIST]

**Update:**

Lubuntu now on HD.  Wireless adapter connects to network: ping works, wget works; "apt-get install" stalls (waiting for headers).

---

### Post by utilitytrack on 2010-08-13
Very good. Please mark this thread as solved.

---

### Post by gweinstein on 2010-08-13
What do you mean solved?  apt-get stalls, chromium stalls at the second page or so.  Does not seem solved to me.  Incidentally, I have the AR2413 chipset which seems to report a lot of problems on this forum, see e.g. [http://ubuntuforums.org/showthread.php?t=1466833&highlight=ar2413+slow](http://ubuntuforums.org/showthread.php?t=1466833&highlight=ar2413+slow),

---

### Post by utilitytrack on 2010-08-13
Oh, sorry me. You are right.

Please try following:
```
# iwconfig wlan0 rate 11M
```

And test. 

PS 
On wich system do you work now?

---

### Post by gweinstein on 2010-08-13
No luck.  Same behavior.  First page loads, sometimes a page from another site would also load, but it stalls second page or so.

---

### Post by bkratz on 2010-08-13
> **gweinstein said:**
> No luck.  Same behavior.  First page loads, sometimes a page from another site would also load, but it stalls second page or so.

Not really familiar with Lubuntu, but you might want to look at modifying the MTU value ( just look up, may not even apply)
There was a thread about that this morning--will try to find.



This was the thread
[http://ubuntuforums.org/showthread.php?t=1552116&highlight=MTU](http://ubuntuforums.org/showthread.php?t=1552116&highlight=MTU)
He/She was specifically referring to Google, but I remember lowering mine to 1492 for reliability a long time ago.

---

### Post by jostle on 2010-08-15
I have had what seems to be a similar problem that has now resolved itself.
I am not sure exactly what fixed the problem but I will describe the steps that I took in case it is of any help in your situation.

The symptoms were :
1. The wireless interface was working and able to see all the access points within range
2. Trying to connect to my wireless router got past the authentication phase but failed to acquire an IP address from the router's DHCP server.

The steps I took, after a number of attempts to change network settings and restart networking (even a couple of reboots) :
1. Reboot into Windoze to test whether the problem was actually the router. The wireless network connected fine.
2. Reboot into the previous version of Linux 2.6.32-23. The wireless network connected fine. So it looked like a problem with 2.6.32-24.
3. Reboot into 2.6.32-24 to verify that the problem was in that version. The wireless  network connected fine!

As I said I have no idea which, if any, of these actions fixed the problem. I have a sneaking suspicion that the cause was actually something to do with the update to kernel 2.6.32-24 as it did happen sometime after that update.

Anyway, I hope this may throw some more light on your issue.

Have Fun.

---

