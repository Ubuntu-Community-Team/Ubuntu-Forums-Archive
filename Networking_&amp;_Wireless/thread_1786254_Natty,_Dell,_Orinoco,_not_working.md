---
title: "Natty, Dell, Orinoco, not working"
date: 2011-06-19
forum: Networking &amp; Wireless
---

### Post by mrule on 2011-06-19
I recently did a clean install of Ubuntu 11.04 on an older laptop. Wireless networks are detected, but I cannot connect. Debug info is a perplexing mix of success and failure. The wireless is set up with MAC filtering and no encryption ( not my setup, I know thats bad ), and the laptop connects fine in Windows. Attempting to force the use of a static IP did nothing.

1.1) Machine Brand and Model (PC/Laptop):
Dell Inspiron 6000 or 9000 ( markings missing ) laptop

1.2) physical wireless card :
[Front]
"orinoco wireless networks"
[Back]
A??? Systems PC24E-H-FC
S???????????4444218
T/N: 2AM ???????????
MAC address: ## ## ## ## ## ##
Encryption:WEP
FCC ID: ??????????
Canada IC: ??????????
[R]01NYD?1257
[T]D99- 1057JP
[2.4DS4]

2 ) Wireless Brand, Model and Wireless Chipset:
( card not detected )
```
~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
03:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
~$ lsusb
Bus 005 Device 003: ID 0d62:2106 Darfon Electronics Corp. 
Bus 005 Device 002: ID 045e:0745 Microsoft Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
~$ lspci -nn | grep 'Wireless Brand'
```

3 ) check interface:
```
~$ ifconfig
eth0      Link encap:Ethernet  HWaddr ##:##:##:##:##:##  
          inet addr:192.168.1.109  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2002:4400:d5be:0:214:22ff:fee5:47dc/64 Scope:Global
          inet6 addr: fe80::214:22ff:fee5:47dc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4576 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2192 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3910433 (3.9 MB)  TX bytes:303414 (303.4 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4348 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4348 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:346888 (346.8 KB)  TX bytes:346888 (346.8 KB)

~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

~$ lsmod
Module                  Size  Used by
orinoco_cs             12898  0 
orinoco                69899  1 orinoco_cs
cfg80211              156212  1 orinoco
pcmcia                 39671  1 orinoco_cs
pcmcia_rsrc            18292  1 yenta_socket
pcmcia_core            21505  4 orinoco_cs,pcmcia,yenta_socket,pcmcia_rsrc

```

5 ) Kernel boot messages
```
[    0.000000] Linux version 2.6.38-8-generic (buildd@vernadsky) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 (Ubuntu 2.6.38-8.42-generic 2.6.38.2)

[   20.032211] yenta_cardbus 0000:03:01.0: CardBus bridge found [1028:0188]
[   20.171782] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   20.196894] yenta_cardbus 0000:03:01.0: ISA IRQ mask 0x0cb8, PCI irq 19
[   20.196902] yenta_cardbus 0000:03:01.0: Socket status: 30000410
[   20.196908] pci_bus 0000:03: Raising subordinate bus# of parent bus (#03) from #04 to #07
[   20.196925] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge window: [mem 0xdfd00000-0xdfdfffff]
[   20.196931] pcmcia_socket pcmcia_socket0: cs: memory probe 0xdfd00000-0xdfdfffff: excluding 0xdfd00000-0xdfd0ffff 0xdfdf0000-0xdfdfffff
[   20.196955] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge window: [mem 0x40000000-0x43ffffff pref]

[   21.116086] pcmcia_socket pcmcia_socket0: pccard: PCMCIA card inserted into slot 0
[   21.245845] pcmcia 0.0: pcmcia: registering new device pcmcia0.0 (IRQ: 3)
[   22.329078] orinoco 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[   22.426262] orinoco_cs 0.0: Hardware identity 0001:0001:0004:0002
[   22.426397] orinoco_cs 0.0: Station identity  001f:0001:0007:001c
[   22.426402] orinoco_cs 0.0: Firmware determined as Lucent/Agere 7.28
[   22.792906] orinoco_cs 0.0: Hardware identity 0001:0001:0004:0002
[   22.793041] orinoco_cs 0.0: Station identity  001f:0002:0009:0030
[   22.793047] orinoco_cs 0.0: Firmware determined as Lucent/Agere 9.48
[   22.793051] orinoco_cs 0.0: Ad-hoc demo mode supported
[   22.793055] orinoco_cs 0.0: IEEE standard IBSS ad-hoc mode supported
[   22.793059] orinoco_cs 0.0: WEP supported, 104-bit key
[   22.793062] orinoco_cs 0.0: WPA-PSK supported
[   22.916203] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   22.916211] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   22.916296] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   22.916301] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   23.025889] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  599.360678] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1570.003677] pcmcia_socket pcmcia_socket0: pccard: card ejected from slot 0
[ 1570.003984] hermes @ 00010100: Card removed while issuing command 0x0002.
[ 1570.003988] eth1: Error -19 disabling MAC port

[ 1618.096041] pcmcia_socket pcmcia_socket0: pccard: PCMCIA card inserted into slot 0
[ 1618.096449] pcmcia 0.0: pcmcia: registering new device pcmcia0.0 (IRQ: 3)
[ 1618.177448] orinoco_cs 0.0: Hardware identity 0001:0001:0004:0002
[ 1618.177582] orinoco_cs 0.0: Station identity  001f:0001:0007:001c
[ 1618.177588] orinoco_cs 0.0: Firmware determined as Lucent/Agere 7.28
[ 1618.303171] orinoco_cs 0.0: Hardware identity 0001:0001:0004:0002
[ 1618.303306] orinoco_cs 0.0: Station identity  001f:0002:0009:0030
[ 1618.303312] orinoco_cs 0.0: Firmware determined as Lucent/Agere 9.48
[ 1618.303316] orinoco_cs 0.0: Ad-hoc demo mode supported
[ 1618.303320] orinoco_cs 0.0: IEEE standard IBSS ad-hoc mode supported
[ 1618.303324] orinoco_cs 0.0: WEP supported, 104-bit key
[ 1618.303327] orinoco_cs 0.0: WPA-PSK supported
[ 1618.313275] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 1618.313284] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1618.313371] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 1618.313376] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1618.353778] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 1629.680150] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1686.669782] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2478.136121] pcmcia_socket pcmcia_socket0: pccard: card ejected from slot 0
[ 2478.136431] hermes @ 00010100: Card removed while issuing command 0x0002.
[ 2478.136435] eth1: Error -19 disabling MAC port

[ 3261.056078] pcmcia_socket pcmcia_socket0: pccard: PCMCIA card inserted into slot 0
[ 3261.056489] pcmcia 0.0: pcmcia: registering new device pcmcia0.0 (IRQ: 3)
[ 3261.137499] orinoco_cs 0.0: Hardware identity 0001:0001:0004:0002
[ 3261.137633] orinoco_cs 0.0: Station identity  001f:0001:0007:001c
[ 3261.137639] orinoco_cs 0.0: Firmware determined as Lucent/Agere 7.28
[ 3261.265489] orinoco_cs 0.0: Hardware identity 0001:0001:0004:0002
[ 3261.265624] orinoco_cs 0.0: Station identity  001f:0002:0009:0030
[ 3261.265630] orinoco_cs 0.0: Firmware determined as Lucent/Agere 9.48
[ 3261.265634] orinoco_cs 0.0: Ad-hoc demo mode supported
[ 3261.265638] orinoco_cs 0.0: IEEE standard IBSS ad-hoc mode supported
[ 3261.265642] orinoco_cs 0.0: WEP supported, 104-bit key
[ 3261.265645] orinoco_cs 0.0: WPA-PSK supported
[ 3261.280329] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 3261.280337] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 3261.280425] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 3261.280525] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 3261.327547] ADDRCONF(NETDEV_UP): eth1: link is not ready

```

6 ) Network configuration
```
~$ sudo lshw -C network
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: ##:##:##:##:##:##
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco_cs driverversion=2.6.38-8-generic firmware=Lucent/Agere 9.48 ip=192.168.1.209 link=no multicast=yes wireless=IEEE 802.11b
```

7 ) Scan for networks:
```
~$ iwlist scan
lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.
eth1      No scan results
```

8 ) Ubuntu Version:
```
~$ lsb_release -d
Description:	Ubuntu 11.04
```

9 ) Kernel/architecture (including 32 vs. 64 bit):
```
~$ uname -mr
2.6.38-8-generic i686
```

10 ) Restarting the network:
```
~$ uname -mr
2.6.38-8-generic i686
~$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                                                                                                        SIOCDELRT: No such process
```

---

### Post by mrule on 2011-06-19
Can someone confirm whether [this]("http://ubuntuforums.org/showpost.php?p=5148420&postcount=107") is the safe and correct solution for this in 11.04 ?

---

### Post by chili555 on 2011-06-19
I doubt that the proposed fix you linked, dated three years ago, is still valid. I suspect you have conflicting drivers loaded, but we'll need to confirm it. Please run and post:```
lsmod | grep -e orin -e hermes
rfkill list all
```As well, Network Manager is designed to disallow a wireless connection if you have wired. When performing tests, please detach the ethernet cable first. I realize you need to re-connect to post the results.

---

### Post by mrule on 2011-06-19
Thanks for the speedy reply,

```
~$ lsmod | grep -e orin -e hermes
orinoco_cs             12898  0 
orinoco                69899  1 orinoco_cs
cfg80211              156212  1 orinoco
pcmcia                 39671  1 orinoco_cs
pcmcia_core            21505  4 orinoco_cs,pcmcia,yenta_socket,pcmcia_rsrc

```

---

### Post by mrule on 2011-06-19
I re-ran the tests wit the ethernet unplugged :

```
user@host:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
03:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
user@host:~$ lsusb
Bus 005 Device 003: ID 045e:0745 Microsoft Corp. 
Bus 005 Device 002: ID 0d62:2106 Darfon Electronics Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
user@host:~$ lspci -nn | grep 'Wireless Brand'
user@host:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr ##:##:##:##:##:##  
          inet addr:192.168.1.208  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:22ff:fee5:47dc/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:19554 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11354 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:23374973 (23.3 MB)  TX bytes:1486512 (1.4 MB)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr ##:##:##:##:##:##  
          inet addr:192.168.1.209  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2002:4400:d5be:0:202:2dff:fe61:b6c2/64 Scope:Global
          inet6 addr: fe80::202:2dff:fe61:b6c2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1082 (1.0 KB)  TX bytes:10215 (10.2 KB)
          Interrupt:3 Base address:0x100 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:21 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1460 (1.4 KB)  TX bytes:1460 (1.4 KB)

user@host:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"shadowlounge"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1D:7E:4E:5F:5F   
          Bit Rate:11 Mb/s   Sensitivity:1/0  
          Retry limit:8   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=69/70  Signal level=-33 dBm  Noise level=-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:10
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

user@host:~$ lsmod
Module                  Size  Used by
sha256_generic         20911  2 
cryptd                 19801  0 
aes_i586               16956  206 
aes_generic            38023  1 aes_i586
parport_pc             32111  0 
ppdev                  12849  0 
dm_crypt               22463  1 
michael_mic            12540  4 
orinoco_cs             12898  1 
orinoco                69899  1 orinoco_cs
cfg80211              156212  1 orinoco
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80244  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
binfmt_misc            13213  1 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 39671  1 orinoco_cs
dell_laptop            13515  0 
yenta_socket           27230  0 
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dcdbas                 14054  1 dell_laptop
pcmcia_rsrc            18292  1 yenta_socket
psmouse                73312  0 
serio_raw              12990  0 
pcmcia_core            21505  4 orinoco_cs,pcmcia,yenta_socket,pcmcia_rsrc
joydev                 17322  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
i915                  450944  2 
usbhid                 41704  0 
drm_kms_helper         40745  1 i915
hid                    77084  1 usbhid
b44                    35301  0 
drm                   180037  3 i915,drm_kms_helper
firewire_ohci          31504  0 
sdhci_pci              13623  0 
ssb                    45942  1 b44
firewire_core          56138  1 firewire_ohci
sdhci                  22720  1 sdhci_pci
i2c_algo_bit           13184  1 i915
crc_itu_t              12627  1 firewire_core
video                  18951  1 i915
user@host:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: ##:##:##:##:##:##
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half ip=192.168.1.208 latency=64 link=no multicast=yes port=twisted pair speed=10Mbit/s
       resources: irq:18 memory:dfdfe000-dfdfffff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: ##:##:##:##:##:##
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco_cs driverversion=2.6.38-8-generic firmware=Lucent/Agere 9.48 ip=192.168.1.209 link=yes multicast=yes wireless=IEEE 802.11b
user@host:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results

user@host:~$ uname -mr
2.6.38-8-generic i686
user@host:~$ sudo /etc/init.d/networking restart       
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                       RTNETLINK answers: No such process
                                                                      [ OK ]

```

---

### Post by chili555 on 2011-06-19
Your lsmod looks perfect. I noticed this:> $ sudo lshw -C network
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:02:2d:61:b6:c2
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco_cs driverversion=2.6.38-8-generic firmware=Lucent/Agere 9.48 [COLOR="Red"]ip=192.168.1.209[/COLOR] [COLOR="RoyalBlue"]link=no[/COLOR] multicast=yes wireless=IEEE 802.11bHow did it get an IP address with no link? Have you done some manual configuration?> dell_laptop            13515  0 This can sometimes be troublesome. Please post:```
rfkill list all
```

---

### Post by mrule on 2011-06-19
Yes, I forgot to mention. One of the fixes for wireless problems on Natty was to assign a static IP in /etc/networking/interfaces. I have reverted that change, and re-run the tests with only wireless present, after rebooting to make sure I didn't miss something. I can confirm that the problem is still present, I can view networks but fail to connect. The rfkill test has been added.

```
user@host:~/Desktop$ lsmod | grep -e orin -e hermes
orinoco_cs             12898  1 
orinoco                69899  1 orinoco_cs
cfg80211              156212  1 orinoco
pcmcia                 39671  1 orinoco_cs
pcmcia_core            21505  4 orinoco_cs,pcmcia,yenta_socket,pcmcia_rsrc
user@host:~/Desktop$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
user@host:~/Desktop$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
03:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
user@host:~/Desktop$ lsusb
Bus 005 Device 003: ID 045e:0745 Microsoft Corp. 
Bus 005 Device 002: ID 0d62:2106 Darfon Electronics Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
user@host:~/Desktop$ lspci -nn | grep 'Wireless Brand'
user@host:~/Desktop$ ifconfig
eth0      Link encap:Ethernet  HWaddr ##:##:##:##:##:##  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr ##:##:##:##:##:##  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:3 Base address:0x100 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

user@host:~/Desktop$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:""  
          Mode:Managed  Frequency:2.457 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity:1/0  
          Retry limit:8   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-122 dBm  Noise level=-122 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

user@host:~/Desktop$ lsmod
Module                  Size  Used by
sha256_generic         20911  2 
cryptd                 19801  0 
aes_i586               16956  119 
aes_generic            38023  1 aes_i586
parport_pc             32111  0 
ppdev                  12849  0 
dm_crypt               22463  1 
michael_mic            12540  4 
orinoco_cs             12898  1 
orinoco                69899  1 orinoco_cs
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80244  2 snd_intel8x0,snd_ac97_codec
cfg80211              156212  1 orinoco
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
binfmt_misc            13213  1 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
dell_laptop            13515  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
dcdbas                 14054  1 dell_laptop
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73312  0 
pcmcia                 39671  1 orinoco_cs
joydev                 17322  0 
yenta_socket           27230  0 
pcmcia_rsrc            18292  1 yenta_socket
soundcore              12600  1 snd
serio_raw              12990  0 
pcmcia_core            21505  4 orinoco_cs,pcmcia,yenta_socket,pcmcia_rsrc
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
i915                  450944  2 
usbhid                 41704  0 
drm_kms_helper         40745  1 i915
hid                    77084  1 usbhid
drm                   180037  3 i915,drm_kms_helper
firewire_ohci          31504  0 
b44                    35301  0 
sdhci_pci              13623  0 
ssb                    45942  1 b44
firewire_core          56138  1 firewire_ohci
sdhci                  22720  1 sdhci_pci
crc_itu_t              12627  1 firewire_core
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
user@host:~/Desktop$ sudo lshw -C network
[sudo] password for user: 
Sorry, try again.
[sudo] password for user: 
  *-network               
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: ##:##:##:##:##:##
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10Mbit/s
       resources: irq:18 memory:dfdfe000-dfdfffff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: ##:##:##:##:##:##
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco_cs driverversion=2.6.38-8-generic firmware=Lucent/Agere 9.48 link=no multicast=yes wireless=IEEE 802.11b
user@host:~/Desktop$ 
```

---

### Post by mrule on 2011-06-19
one sec, I'm going to try to do a general update. I have not done this since install and maybe this has been fixed.

---

### Post by mrule on 2011-06-19
An update did not resolve the problem.

---

### Post by chili555 on 2011-06-19
> I can view networks but fail to connect.What does this tell us?```
sudo iwlist eth1 scan
sudo iwlist eth1 auth
```> [   22.793062] orinoco_cs 0.0: WPA-PSK supportedI hope this doesn't mean WPA[COLOR="Red"]2[/COLOR] isn't supported.

Manual methods, that is /etc/network/interfaces is unlikely to work if Network Manager is installed and running.

---

### Post by mrule on 2011-06-19
It is an older card.

```
user@host:~$ sudo iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:1D:7E:4E:5F:5F
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-24 dBm  
                    Encryption key:off
                    ESSID:"shadowlounge"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003ed2ef15ae
                    Extra: Last beacon: 152ms ago
                    IE: Unknown: 000C736861646F776C6F756E6765
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180201F0000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: 68:7F:74:A9:9A:FA
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:off
                    ESSID:"RichGiraffe"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000154057f4632
                    Extra: Last beacon: 156ms ago
                    IE: Unknown: 000B5269636847697261666665
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001700000000000000000000000000000000000000
                    IE: Unknown: DD7A0050F204104A00011010440001021041000100103B00010310470010FA6C127F82355CA31262CF9FE5380D2F10210005436973636F1023000D4C696E6B7379732045333030301024000776312E302E30301042000234321054000800060050F20400011011000D4C696E6B737973204533303030100800020084
                    IE: Unknown: DD090010180206F0050000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001700000000000000000000000000000000000000
          Cell 03 - Address: 68:7F:74:A9:9A:FC
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:off
                    ESSID:"RichGiraffe-guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000154057f5345
                    Extra: Last beacon: 152ms ago
                    IE: Unknown: 001152696368476972616666652D6775657374
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001700000000000000000000000000000000000000
                    IE: Unknown: DD090010180206F0050000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001700000000000000000000000000000000000000
          Cell 04 - Address: 10:9A:DD:8B:5D:F5
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"Barburg"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000004f1163f9a4
                    Extra: Last beacon: 244ms ago
                    IE: Unknown: 000742617262757267
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101030003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1700039301720120000E109ADD8B5DF501109ADD8B5DF695

user@host:~$ sudo iwlist eth1 auth
eth1      Authentication capabilities :
		WPA
		CIPHER-TKIP
          Current Key management :
          Current TKIP countermeasures : no
          Current Authentication algorithm :
		open

```

---

### Post by chili555 on 2011-06-19
I'm sorry, I can't see anything wrong to fix so far. I wonder what Network Manager is doing all this time:```
sudo cat /var/log/syslog | grep etwork | tail -n20
```

---

### Post by mrule on 2011-06-19
```
:~$ sudo cat /var/log/syslog | grep etwork | tail -n30
Jun 19 16:19:29 host NetworkManager[789]: <info> (eth1): supplicant connection state:  scanning -> associating
Jun 19 16:19:34 host NetworkManager[789]: <info> (eth1): supplicant connection state:  associating -> disconnected
Jun 19 16:19:34 host NetworkManager[789]: <info> (eth1): supplicant connection state:  disconnected -> scanning
Jun 19 16:19:34 host NetworkManager[789]: <info> (eth1): supplicant connection state:  scanning -> associating
Jun 19 16:19:40 host NetworkManager[789]: <info> (eth1): supplicant connection state:  associating -> disconnected
Jun 19 16:19:40 host NetworkManager[789]: <info> (eth1): supplicant connection state:  disconnected -> scanning
Jun 19 16:19:40 host NetworkManager[789]: <info> (eth1): supplicant connection state:  scanning -> associating
Jun 19 16:19:45 host NetworkManager[789]: <info> (eth1): supplicant connection state:  associating -> disconnected
Jun 19 16:19:45 host NetworkManager[789]: <info> (eth1): supplicant connection state:  disconnected -> scanning
Jun 19 16:19:45 host NetworkManager[789]: <info> (eth1): supplicant connection state:  scanning -> associating
Jun 19 16:19:50 host NetworkManager[789]: <info> (eth1): supplicant connection state:  associating -> disconnected
Jun 19 16:19:50 host NetworkManager[789]: <info> (eth1): supplicant connection state:  disconnected -> scanning
Jun 19 16:19:50 host NetworkManager[789]: <info> (eth1): supplicant connection state:  scanning -> associating
Jun 19 16:19:55 host NetworkManager[789]: <info> (eth1): supplicant connection state:  associating -> disconnected
Jun 19 16:19:55 host NetworkManager[789]: <info> (eth1): supplicant connection state:  disconnected -> scanning
Jun 19 16:19:55 host NetworkManager[789]: <info> (eth1): supplicant connection state:  scanning -> associating
Jun 19 16:20:00 host NetworkManager[789]: <info> (eth1): supplicant connection state:  associating -> disconnected
Jun 19 16:20:00 host NetworkManager[789]: <info> (eth1): supplicant connection state:  disconnected -> scanning
Jun 19 16:20:00 host NetworkManager[789]: <info> (eth1): supplicant connection state:  scanning -> associating
Jun 19 16:20:04 host NetworkManager[789]: <warn> (eth1): link timed out.
Jun 19 16:20:05 host NetworkManager[789]: <info> (eth1): supplicant connection state:  associating -> disconnected
Jun 19 16:20:05 host NetworkManager[789]: <info> (eth1): supplicant connection state:  disconnected -> scanning
Jun 19 16:20:06 host NetworkManager[789]: <info> (eth1): supplicant connection state:  scanning -> associating
Jun 19 16:20:08 host NetworkManager[789]: <warn> Activation (eth1/wireless): association took too long, failing activation.
Jun 19 16:20:08 host NetworkManager[789]: <info> (eth1): device state change: 5 -> 9 (reason 11)
Jun 19 16:20:08 host NetworkManager[789]: <warn> Activation (eth1) failed for access point (shadowlounge)
Jun 19 16:20:08 host NetworkManager[789]: <info> Marking connection 'Auto shadowlounge' invalid.
Jun 19 16:20:08 host NetworkManager[789]: <warn> Activation (eth1) failed.
Jun 19 16:20:08 host NetworkManager[789]: <info> (eth1): device state change: 9 -> 3 (reason 0)
Jun 19 16:20:08 host NetworkManager[789]: <info> (eth1): deactivating device (reason: 0).

```

---

### Post by mrule on 2011-06-19
I suppose its possible that this is a network problem thats not entirely Ubuntu's fault? I can't imagine why it would work only in windows if this is the case though.

---

### Post by chili555 on 2011-06-20
> **mrule said:**
> I suppose its possible that this is a network problem thats not entirely Ubuntu's fault? I can't imagine why it would work only in windows if this is the case though.I doubt that it is. I have responded to a few cases over the years that start with the premise that a certain ISP or a certain router is incompatible with Linux. In every case, the poster has been able to connect.> One of the fixes for wireless problems on Natty was to assign a static IP in /etc/networking/interfaces. We could try assigning a static IP in Network Manager. Please see attached.

We could also, with some care, remove NM and populate /etc/network/interfaces and try that way. I had a Prism card 109 years ago and it worked perfectly using /etc/networking/interfaces; I never tried NM. It hadn't been invented!

We could also try the hostap drivers. I am not confident it's a driver issue, because it scans and sees networks and tries to connect. It may be a driver vs. NM issue.

---

### Post by mrule on 2011-06-20
I was unable to connect by setting a static IP address from within network manager.

([http://ubuntuforums.org/showthread.php?t=527365](http://ubuntuforums.org/showthread.php?t=527365))
However, after disabling network manager
```
sudo update-rc.d NetworkManager remove
```

([http://ubuntuforums.org/showthread.php?t=90137](http://ubuntuforums.org/showthread.php?t=90137))
and manually configuring the wireless in /etc/network/interfaces
```
iface eth1 inet static
address 192.168.1.105
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
wireless-mode managed
wireless-essid YOURSSID

```

and rebooting, I now have functioning wireless.

thank you.


Is there anything else I should look at, now that its running ? Perhaps to help fix whatever bug in network manager was preventing connections ?

---

### Post by chili555 on 2011-06-20
> iface eth1 inet static
address 192.168.1.105
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
wireless-mode managed
wireless-essid YOURSSIDThat's a busy little *interfaces* file! I'm not quite sure how it started on boot without *auto eth1*. I'd probably change it to:```
auto eth1
iface eth1 inet static
address 192.168.1.105
netmask 255.255.255.0
#network 192.168.1.0
#broadcast 192.168.1.255
gateway 192.168.1.1
#wireless-mode managed
wireless-essid YOURSSID
```The reason I commented the lines above is that if it doesn't perform as expected, you can add one or all back in until it does. Make sure the IP address you've selected is outside the range of the DHCP server in the router. > Perhaps to help fix whatever bug in network manager was preventing connections ?You could certainly report a bug: [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

It is very difficult, for me, at least, to see if it's the driver, the hardware, NM or dhcpd. I'm sure the developers will all blame the other. If I were you, I'd register and report it against all of them.

I also suggest you encrypt your network. In that case:```
auto eth1
iface eth1 inet static
address 192.168.1.105
netmask 255.255.255.0
#network 192.168.1.0
#broadcast 192.168.1.255
gateway 192.168.1.1
#wireless-mode managed
wpa-essid YOURSSID
wpa-psk YOURPASSWORD
```In any event, I'm glad you are connected. Would you please use the thread tools at the top and mark this case SOLVED?

---

### Post by northd_tech on 2011-09-01
Just as a hunch and unless I missed it above, it might be worth posting the results of this terminal command for those having trouble with this "orinoco_cs" module and wireless (but this would be specific to PCMCIA cards):

```
sudo pccardctl ident
```

---

