---
title: "wireless problems"
date: 2010-02-16
forum: Networking &amp; Wireless
---

### Post by RasterBurn on 2010-02-16
hello , i have an EnGenius EPI-3601S wireless card installed in my computer, the output of lspci -vnn shows the card as:

06:06.0 Ethernet controller [0200]: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter [168c:0013] (rev 01)
    Subsystem: Atheros Communications Inc. Device [168c:2051]
    Flags: bus master, medium devsel, latency 168, IRQ 21
    Memory at febf0000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: [44] Power Management version 2
    Kernel driver in use: ath_pci
    Kernel modules: ath_pci, ath5k

the output of iwconfig shows:

lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"Michael's Wireless"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:24:01:42:F9:9C   
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=31/70  Signal level=-57 dBm  Noise level=-88 dBm
          Rx invalid nwid:19970  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

right now i am using the madwifi drivers for the card and i have found it is limiting the TX-Power to 18 and i am having some troubles connecting to the network also i seem to be limited to 802.11b speeds instead of running at full 802.11g

I have tried the ath5k driver and found that my TX-Power is full (27dBm) but my bit rate remains down at 1Mb/s.

I would use ndiswrapper but i had installed it and could not get it to work (had to use the 64-bit windows 7 driver for my card), since it did not work for me(i most likely did something wrong) i have uninstalled ndiswrapper for now.

If anyone can help me get my wireless card running at full power properly that would be great, i am using WPA/WPA2 wireless security on the network

---

### Post by RasterBurn on 2010-03-06
no one has this problem??? I guess i will just update the topic since several updates have been released as well as different variables are in the mix as well....

the output of lspci -vnn is:

```
06:06.0 Ethernet controller [0200]: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter [168c:0013] (rev 01)
    Subsystem: Atheros Communications Inc. Device [168c:2051]
    Flags: bus master, medium devsel, latency 168, IRQ 21
    Memory at febf0000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: [44] Power Management version 2
    Kernel driver in use: ath5k
    Kernel modules: ath5k
```
and the output of iwconfig shows:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Michael's Wireless"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <REMOVED FOR SECURITY>   
          Bit Rate=11 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key: <REMOVED FOR SECURITY>
          Power Management:off
          Link Quality=69/70  Signal level=-41 dBm  Noise level=-75 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.
```

my router is a DLink wireless N router (so i should get full connection) i have had a look at the debian live cd and it also uses ath5k wireless for my card... not sure the status of it but it seems to get 48MB/s connection any help would be highly appreciated

---

### Post by excogitation on 2010-04-18
I filed a bug about the weak reception problem here: [565537]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/565537").
Feel free to contribute.

---

