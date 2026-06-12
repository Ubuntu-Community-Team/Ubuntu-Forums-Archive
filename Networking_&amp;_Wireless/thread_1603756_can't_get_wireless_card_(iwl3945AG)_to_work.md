---
title: "can't get wireless card (iwl3945AG) to work"
date: 2010-10-23
forum: Networking &amp; Wireless
---

### Post by truffles_by_proxy on 2010-10-23
Hi,
At some point on the 10.04 my wireless card (Intel 3945) got "deactivated". The upgrade to the 10.10 did not help. But reading the forum I was able to blacklist the dell_laptop module. It still does not work -I don't know why- but now the card is active again, it just keeps being "disconnected". Below are some output of commands you may be interested to look at:
```
melissa@truffle:~$ sudo lshw -c network
[sudo] password for melissa: 
  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wlan0
       version: 02
       serial: 00:1c:bf:61:8f:81
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=2.6.35-22-generic firmware=15.32.2.9 ip=192.168.1.4 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:42 memory:efdff000-efdfffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:a5:7d:96
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.0.13 latency=64 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:17 memory:ef9fe000-ef9fffff
melissa@truffle:~$ ^C
```then:
```
melissa@truffle:~$ sudo ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1d:09:a5:7d:96  
          inet adr:192.168.0.13  Bcast:192.168.0.255  Masque:255.255.255.0
          adr inet6: fe80::21d:9ff:fea5:7d96/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:2150 erreurs:0 :0 overruns:0 frame:0
          TX packets:2156 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:2017781 (2.0 MB) Octets transmis:412315 (412.3 KB)
          Interruption:17 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:12 erreurs:0 :0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:720 (720.0 B) Octets transmis:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1c:bf:61:8f:81  
          inet adr:192.168.1.4  Bcast:192.168.1.255  Masque:255.255.255.0
          BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)

melissa@truffle:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"freeboxLADD"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:394F-F9FE-B9
          Power Management:off
          
melissa@truffle:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

melissa@truffle:~$ 
```When trying to "activate" the wlan interface again I get a message which makes me think the driver is not there:
```
melissa@truffle:~$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: Aucun périphérique de ce type

```Yet:
```
  GNU nano 2.2.4            Fichier : /etc/modules                              

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

#lp
#iwlcore
iwl3945





```and the dell_laptop module is properly blacklisted. Also:
```
melissa@truffle:~$ sudo rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
melissa@truffle:~$ 

```But I cannot really understand what's the exact meaning of this:
```
melissa@truffle:~$ dmesg | grep iwl
[   11.622114] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   11.622120] iwl3945: Copyright(c) 2003-2010 Intel Corporation
[   11.622219] iwl3945 0000:0b:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.622234] iwl3945 0000:0b:00.0: setting latency timer to 64
[   11.688059] iwl3945 0000:0b:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   11.688066] iwl3945 0000:0b:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   11.688226] iwl3945 0000:0b:00.0: irq 42 for MSI/MSI-X
[   11.724338] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   11.827274] iwl3945 0000:0b:00.0: loaded firmware version 15.32.2.9
[   11.827456] iwl3945 0000:0b:00.0: Radio disabled by HW RF Kill switch
[   11.857826] iwl3945 0000:0b:00.0: Radio disabled by HW RF Kill switch
[   11.857908] iwl3945 0000:0b:00.0: Radio disabled by HW RF Kill switch
[   12.482711] iwl3945 0000:0b:00.0: Radio disabled by HW RF Kill switch
[   12.510768] iwl3945 0000:0b:00.0: Radio disabled by HW RF Kill switch
[   12.825965] iwl3945 0000:0b:00.0: Radio disabled by HW RF Kill switch
[   12.836369] iwl3945 0000:0b:00.0: Radio disabled by HW RF Kill switch
[   12.836467] iwl3945 0000:0b:00.0: Radio disabled by HW RF Kill switch
[   55.956416] iwl3945 0000:0b:00.0: Radio disabled by HW RF Kill switch
[  723.885297] iwl3945 0000:0b:00.0: Radio disabled by HW RF Kill switch
melissa@truffle:~$ 

```Any idea?

thanks!

---

### Post by utilitytrack on 2010-10-23
Try unload a iwl3945 module and load it again manually. Which are PC/laptop you use? Also provide here [B]$ uname -a
[/B]
> SIOCSIFFLAGS: Aucun périphérique de ce type

Please on time of testing set locale of given bash session to standard C locale (English):
```
$ export LC_MESSAGES=C LANG=C LANGUAGE=C
```

---

### Post by truffles_by_proxy on 2010-10-23
> **utilitytrack said:**
> Try unload a iwl3945 module and load it again manually. Which are PC/laptop you use? Also provide here [B]$ uname -a
[/B]


Please on time of testing set locale of given bash session to standard C locale (English):
```
$ export LC_MESSAGES=C LANG=C LANGUAGE=C
```


So I did unload and load the iwl3945 but it didn't do anything. 
As for the message indeed it's in french, it just says "no device found". And that sounds really weird to me. 
Here's the output of uname -a:
```
Linux truffle 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:36:48 UTC 2010 i686 GNU/Linux

```

---

### Post by utilitytrack on 2010-10-24
What PC/laptop you use? Post here when you have the troubles:

```
$ rfkill list
$ dmesg | grep -i -E '80211|KHz|iwl|phy|wlan|kill'
```

And how you manage wireless connections: through NM/Wicd or manually?

---

### Post by truffles_by_proxy on 2010-10-25
> **utilitytrack said:**
> What PC/laptop you use? Post here when you have the troubles:

```
$ rfkill list
$ dmesg | grep -i -E '80211|KHz|iwl|phy|wlan|kill'
```And how you manage wireless connections: through NM/Wicd or manually?

Here's the output of the commands:
```
melissa@truffle:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
melissa@truffle:~$ dmesg | grep -i -E '80211|KHz|iwl|phy|wlan|kill'
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] modified physical RAM map:
[    0.004937] CPU: Physical Processor ID: 0
[   11.565392] cfg80211: Calling CRDA to update world regulatory domain
[   11.742736] cfg80211: World regulatory domain updated:
[   11.742744]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.742747]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   11.742750]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   11.742753]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.742756]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.930991] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   11.930996] iwl3945: Copyright(c) 2003-2010 Intel Corporation
[   11.931095] iwl3945 0000:0b:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.931111] iwl3945 0000:0b:00.0: setting latency timer to 64
[   12.060903] iwl3945 0000:0b:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   12.060909] iwl3945 0000:0b:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   12.061085] iwl3945 0000:0b:00.0: irq 42 for MSI/MSI-X
[   12.132847] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   12.435905] iwl3945 0000:0b:00.0: loaded firmware version 15.32.2.9
[   12.436117] iwl3945 0000:0b:00.0: Radio disabled by HW RF Kill switch
[   12.448860] iwl3945 0000:0b:00.0: Radio disabled by HW RF Kill switch
[   12.457696] iwl3945 0000:0b:00.0: Radio disabled by HW RF Kill switch
[   12.457898] iwl3945 0000:0b:00.0: Radio disabled by HW RF Kill switch
[   12.461341] iwl3945 0000:0b:00.0: Radio disabled by HW RF Kill switch
[   13.019015] iwl3945 0000:0b:00.0: Radio disabled by HW RF Kill switch
[   13.026442] iwl3945 0000:0b:00.0: Radio disabled by HW RF Kill switch
[   13.026518] iwl3945 0000:0b:00.0: Radio disabled by HW RF Kill switch
[ 2621.116276] b44 ssb0:0: eth0: powering down PHY
[ 2622.475847] iwl3945 0000:0b:00.0: restoring config space at offset 0xf (was 0x100, writing 0x104)
[ 2622.475915] iwl3945 0000:0b:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xefdff000)
[ 2622.475929] iwl3945 0000:0b:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 2622.475949] iwl3945 0000:0b:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100506)
[ 2624.040432] iwl3945 0000:0b:00.0: Radio disabled by HW RF Kill switch
[ 2624.048452] iwl3945 0000:0b:00.0: Radio disabled by HW RF Kill switch
melissa@truffle:~$ 

```

I do use a Dell Inspiron 6400, and I use Network Manager.

---

### Post by NertSkull on 2010-10-25
recently I've come across wicd,

its another wireless network manager (but not network-manager).

I totally uninstalled network manager and installed wicd instead (its in the repositories) and I couldn't be happier.

I was unable to get a static WPA IP address to work after weeks of trying.  wicd got it set up and running in about 5 minutes.

it may do nothing for you, but something you may want to look into.

---

### Post by utilitytrack on 2010-10-25
> **truffles_by_proxy said:**
> ```
[ 2624.048452] iwl3945 0000:0b:00.0: Radio disabled by HW RF Kill switch

```

Look in here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/523143]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/523143")

---

### Post by truffles_by_proxy on 2010-10-27
> **utilitytrack said:**
> Look in here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/523143](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/523143)


thanks!!! it now works, and yes, it's all about 1)blacklisting the dell kernel module 2) finding the actual button on the laptop that switches the wifi on and off....

---

### Post by utilitytrack on 2010-10-27
Please mark this thread as solved by using the "Thread Tools" menu.

---

