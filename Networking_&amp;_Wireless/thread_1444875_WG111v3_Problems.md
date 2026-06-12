---
title: "WG111v3 Problems"
date: 2010-04-01
forum: Networking &amp; Wireless
---

### Post by maxcat55 on 2010-04-01
I am running Ubuntu 9.04 on a computer of unkown type and origin, however, it has a Pentium 4 and 750 mb or so of ram, if that matters.

A while back, I purchased a WG111v3 USB network adapter to allow my computer to access my home network. It has been working spottily with the supplied drivers that come with 9.04. 

I had been reading, and I saw that ndiswrapper could be used to install windows drivers to allow the adapter to hopefully work better, so I installed it and tried EVERY version of the driver off of the netgear website. everything half works.

WICD simply says "chicken (my network name): validating authentication
then, in about 30 seconds, says "none: validating authentication"

It does this 15-20 times, then gives up. dmesg does not show any errors, although I can send the entire thing here if it becomes necessary.

Honestly, I believe that their is a conflict between the old driver and the ndiswrapper driver, and essentially I need to fully remove the ubuntu supplied driver. Either that, or re-install the ubuntu driver. 

Thanks in advance!

---

### Post by chili555 on 2010-04-01
Please post:```
ndiswrapper -l
lsmod
```Thanks.

---

### Post by maxcat55 on 2010-04-02
ndiswrapper
```
ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
wg111v3 : driver installed
	device (0846:4260) present (alternate driver: rtl8187)
```

lsmod
```
lsmod
Module                  Size  Used by
binfmt_misc            16776  1 
bridge                 56212  0 
stp                    10500  1 bridge
bnep                   20224  2 
video                  25872  0 
output                 11008  1 video
input_polldev          11912  0 
lp                     17156  0 
snd_intel8x0           37532  3 
snd_ac97_codec        112292  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83076  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
snd                    62756  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                61972  0 
dcdbas                 15264  0 
ppdev                  15620  0 
soundcore              15200  1 snd
serio_raw              13444  0 
snd_page_alloc         16904  2 snd_intel8x0,snd_pcm
pcspkr                 10496  0 
shpchp                 40212  0 
ndiswrapper           193436  0 
parport_pc             40100  1 
parport                42220  3 lp,ppdev,parport_pc
intel_agp              34108  1 
agpgart                42696  2 intel_agp
hid_dell               10112  0 
usbhid                 42336  1 hid_dell
b44                    35984  0 
ssb                    41220  1 b44
mii                    13312  1 b44
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit



```

---

### Post by chili555 on 2010-04-02
The native module is not loading in lsmod and ndiswrapper is loaded and showing no signs of distress. May we see:```
iwconfig
```Thanks.

---

### Post by maxcat55 on 2010-04-02
iwconfig
```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



 
```

How would I go about switching back to the native driver?

Thanks for the fast replies by the way

---

### Post by chili555 on 2010-04-02
> wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
Looks pretty normal, actually. Please do:```
sudo iwconfig wlan0 sens 2
sudo iwlist wlan0 scan
```Thanks.

---

### Post by maxcat55 on 2010-04-02
First command returned nothing

Second command:
```
sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:11:50:32:3E:4D
                    ESSID:"chicken"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:64/100  Signal level:-55 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK



 
```

---

### Post by chili555 on 2010-04-03
So far, everything looks perfectly fine. I notice that your network is set for WPA-PSK encryption. Are you sure the card and Windows driver combination does WPA-PSK? Please check with:```
sudo iwlist wlan0 auth
```I am reluctant to suggest going back to the native driver; there are a couple of threads going on now about getting rtl8187 to work at all, or if it does work, it's terribly slow. Some of those guys are thinking of ndiswrapper!

---

### Post by maxcat55 on 2010-04-03
```
sudo iwlist wlan0 auth
wlan0     Authentication capabilities :
		WPA
		WPA2
		CIPHER-TKIP
		CIPHER-CCMP
          Current WPA version :
		disabled
          Current Key management :
          Current Pairwise cipher :
		none
          Current Pairwise cipher :
		none
          Current Authentication algorithm :
		open


 
```

rtl8187 did work very poorly. I was not even able to use jango... and updates took hours. 

I should also note that before rtl8187 came out, I used ndiswrapper for this wireless card and it worked beautifully. I am using the same driver that worked last time... which is what baffles me.

---

### Post by chili555 on 2010-04-03
Would you care to try a different driver? Please see attached.

---

### Post by maxcat55 on 2010-04-03
the enclosed driver does not work at all. iwconfig does not return any wireless devices, ect.

---

### Post by chili555 on 2010-04-03
What does this tell us?```
ndiswrapper -l
```

---

### Post by maxcat55 on 2010-04-03
```
ndiswrapper -l
net8187b : driver installed

 
```

and thats it. The way I see it, the driver installed just fine, but simply does not work with the device.

---

### Post by chili555 on 2010-04-03
Does this hsve anything interesting to tell us?```
dmesg | grep -i ndis -i wlan
```

---

### Post by maxcat55 on 2010-04-03
```
dmesg | grep -i ndis
[   18.586784] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   19.165559] ndiswrapper: driver wg111v3 (NETGEAR Inc.,07/31/2009,5.1175.0731.2009) loaded
[   20.284958] wlan0: ethernet device 00:22:3f:e8:b9:6d using NDIS driver: wg111v3, version: 0x1, NDIS version: 0x500, vendor: 'Realtek RTL8187 Wireless LAN USB NIC                                     ', 0846:4260.F.conf
[   20.285050] usbcore: registered new interface driver ndiswrapper
[  211.333007] ndiswrapper: device wlan0 removed
[ 1607.876416] ndiswrapper: driver wg111v3 (NETGEAR Inc.,07/31/2009,5.1175.0731.2009) loaded
[ 1608.932443] wlan0: ethernet device 00:22:3f:e8:b9:6d using NDIS driver: wg111v3, version: 0x1, NDIS version: 0x500, vendor: 'Realtek RTL8187 Wireless LAN USB NIC                                     ', 0846:4260.F.conf
[52554.383566] ndiswrapper (iw_get_auth:1615): invalid cmd 4
[52554.383574] ndiswrapper (iw_get_auth:1615): invalid cmd 5
[52554.383646] ndiswrapper (iw_get_auth:1615): invalid cmd 8
[52554.383650] ndiswrapper (iw_get_auth:1615): invalid cmd 9
[52554.383652] ndiswrapper (iw_get_auth:1615): invalid cmd 10
[55224.990481] usbcore: deregistering interface driver ndiswrapper
[55225.001701] ndiswrapper: device wlan0 removed
[55225.013800] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[55225.030999] usbcore: registered new interface driver ndiswrapper 
```

```
dmesg | grep -i wlan
[   20.284958] wlan0: ethernet device 00:22:3f:e8:b9:6d using NDIS driver: wg111v3, version: 0x1, NDIS version: 0x500, vendor: 'Realtek RTL8187 Wireless LAN USB NIC                                     ', 0846:4260.F.conf
[   20.284999] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   42.480013] wlan0: no IPv6 routers present
[   76.708337] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   78.587954] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   88.920019] wlan0: no IPv6 routers present
[  132.448007] wlan0: no IPv6 routers present
[  176.720015] wlan0: no IPv6 routers present
[  211.333007] ndiswrapper: device wlan0 removed
[ 1608.932443] wlan0: ethernet device 00:22:3f:e8:b9:6d using NDIS driver: wg111v3, version: 0x1, NDIS version: 0x500, vendor: 'Realtek RTL8187 Wireless LAN USB NIC                                     ', 0846:4260.F.conf
[ 1608.932473] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[ 1619.264008] wlan0: no IPv6 routers present
[ 1645.473585] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1648.403830] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1659.324011] wlan0: no IPv6 routers present
[55225.001701] ndiswrapper: device wlan0 removed

 
```

---

### Post by chili555 on 2010-04-03
I think you are right, it's not correct, although it works for others. I am sorry. I suggest you remove it and re-install your previous driver.

---

### Post by maxcat55 on 2010-04-03
how would I go about reverting to the native linux one? that way I actually have some internet capability....

---

### Post by chili555 on 2010-04-03
You can try it temporarily with:```
sudo rmmod -f ndiswrapper
sudo modprobe rtl8187
```If it works, remove ndiswrapper from /etc/modules and add rtl8187. Remove rtl8187 from /etc/modprobe.d/blacklist.conf and add ndiswrapper.

Post back if you need more specific instructions.

---

