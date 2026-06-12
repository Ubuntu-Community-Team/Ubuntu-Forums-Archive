---
title: "Can't connect to MY wireless network"
date: 2010-07-17
forum: Networking &amp; Wireless
---

### Post by psycho5 on 2010-07-17
Hello,

I have a weird problem, I am using a wireless USB card, which picks up signals just fine. I can't however connect to my own wireless SSID. I can connect to my neighbor's. 

If I try to connect to mine, it tries to connect and keeps asking for the network key. I am sure the key is correct because in windows I can connect just fine. 

Here's dmseg : 

```

[   18.445508] usbcore: registered new interface driver ndiswrapper
[   18.717886] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   18.717890] vboxdrv: Successfully done.
[   18.717893] vboxdrv: Found 2 processor cores.
[   18.718878] vboxdrv: fAsync=1 offMin=0x51045 offMax=0x51045
[   18.719851] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
[   18.719855] vboxdrv: Successfully loaded version 3.1.6_OSE (interface 0x00100001).
[   18.807154] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.853761] ioremap error for 0x0-0x2000, requested 0x10, got 0x0
[   18.867434] usbcore: registered new interface driver snd-usb-audio
[   18.959487] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input7
[   89.008031] Clocksource tsc unstable (delta = -236680668 ns)
[   90.654967] r8192s_usb: module is from the staging directory, the quality is unknown, you have been warned.
[   90.668644] ieee80211_crypt: registered algorithm 'NULL'
[   90.668651] ieee80211_crypt: registered algorithm 'TKIP'
[   90.668655] ieee80211_crypt: registered algorithm 'CCMP'
[   90.668659] ieee80211_crypt: registered algorithm 'WEP'
[   90.668663] 
[   90.668664] Linux kernel driver for RTL8192 based WLAN cards
[   90.668668] Copyright (c) 2007-2008, Realsil Wlan
[   90.668752] usbcore: registered new interface driver rtl819xU
[  182.699985] usb 1-1: USB disconnect, address 2
[  187.436035] usb 1-1: new high speed USB device using ehci_hcd and address 5
[  187.616316] usb 1-1: configuration #1 chosen from 1 choice
[  248.606397] usb 1-1: USB disconnect, address 5
[  255.052039] usb 1-1: new high speed USB device using ehci_hcd and address 6
[  255.201701] usb 1-1: configuration #1 chosen from 1 choice
[  255.203757] 
[  255.203760] 
[  255.203762] === pAd = fa11e000, size = 566748 ===
[  255.203764] 
[  255.203770] <-- RTMPAllocAdapterBlock, Status=0
[  255.513547] <-- RTMPAllocTxRxRingMemory, Status=0
[  255.515503] -->RTUSBVenderReset
[  255.515626] <--RTUSBVenderReset
[  255.805924] --> Error 2 opening /etc/Wireless/RT3070STA/RT3070STA.dat
[  255.805932] 1. Phy Mode = 0
[  255.805936] 2. Phy Mode = 0
[  255.862557] 3. Phy Mode = 0
[  255.867557] RTMPSetPhyMode: channel is out of range, use first channel=1 
[  255.867564] MCS Set = 00 00 00 00 00
[  255.935940] <==== RTMPInitialize, Status=0
[  255.937446] 0x1300 = 00073200
[  260.969630] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 416
[  261.609214] DRS: unkown mode,default use 11N 1S AP 
[  261.609225] DRS: unkown mode (SupRateLen=0, ExtRateLen=0, MCSSet[0]=0x0, MCSSet[1]=0x0)
[  266.037035] wlan0: no IPv6 routers present
[  272.460090] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 416
[  272.460484] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=11)
[  272.503817] DRS: unkown mode,default use 11N 1S AP 
[  272.503828] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[  287.506783] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 416
[  287.506987] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=11)
[  287.549536] DRS: unkown mode,default use 11N 1S AP 
[  287.549542] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[  298.607896] DRS: unkown mode,default use 11N 1S AP 
[  298.607907] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[  302.550379] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 416
[  302.550775] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=11)
[  302.602177] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[  302.602192] DRS: unkown mode,default use 11N 1S AP 
[  302.602198] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[  317.603259] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 416
[  317.603770] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=11)
[  317.655938] DRS: unkown mode,default use 11N 1S AP 
[  317.655950] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[  337.252267] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 416
[  337.253003] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=11)
[  337.316063] DRS: unkown mode,default use 11N 1S AP 
[  337.316074] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[  352.318554] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 416
[  352.319342] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=11)
[  352.371696] DRS: unkown mode,default use 11N 1S AP 
[  352.371707] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[  367.374240] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 416
[  367.374619] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=11)
[  367.422208] DRS: unkown mode,default use 11N 1S AP 
[  367.422219] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[  374.933569] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 416
[  374.934067] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
[  375.046845] DRS: unkown mode,default use 11N 1S AP 
[  375.046857] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[  404.272101] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 416
[  417.332095] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 416
[  417.336606] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
[  417.757702] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[  417.757717] DRS: unkown mode,default use 11N 1S AP 
[  417.757723] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[  444.276474] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 416
[  504.274505] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 416
[  584.277688] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 416
oj@oj-desktop:~$ 

```

ifconfig and iwconfig: 

```

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:18:f3:10:92:ba  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:26 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10964 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10964 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1996777 (1.9 MB)  TX bytes:1996777 (1.9 MB)

wlan0     Link encap:Ethernet  HWaddr 00:26:75:01:9d:d5  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:75ff:fe01:9dd5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6766 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2224 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2921374 (2.9 MB)  TX bytes:355744 (355.7 KB)

oj@oj-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

wlan0     RTxx70 Wireless  ESSID:"ks"  Nickname:"RT3070STA"
          Mode:Managed  Frequency=2.412 GHz  Access Point: 00:30:0A:F0:5C:06   
          Bit Rate=18 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=54/100  Signal level:-83 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

oj@oj-desktop:~$ lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c218 Logitech, Inc. Logitech RumblePad 2 USB
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 148f:3070 Ralink Technology, Corp. 
Bus 001 Device 003: ID 093a:2700 Pixart Imaging, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
oj@oj-desktop:~$


```



If there is anything else I can post to help clear up the situation let me know plz

EDIT: Solved, it was an encryption problem, I just changed the encryption type now it works fine. I think the driver doesn't support that encryption in linux for this card.

---

