---
title: "DWA-140 Rev B2 - Very slow wireless with rt2800usb driver."
date: 2012-03-08
forum: Networking &amp; Wireless
---

### Post by cyberbot on 2012-03-08
After the kernel update to 3.0 and the removal of rt2870sta driver, I've had little more than heaps of trouble with my DWA-140 device (which worked flawlessly before).
The only way I've managed to get it connect and recognized, is by running with the rt2800usb driver, and that has given me less than satisfactory performance.
 
Here are the speeds from pinging Google:
```
PING google.com (173.194.69.113) 56(84) bytes of data.
64 bytes from bk-in-f113.1e100.net (173.194.69.113): icmp_req=2 ttl=45 time=51.2 ms
64 bytes from 173.194.69.113: icmp_req=3 ttl=45 time=44.5 ms
64 bytes from bk-in-f113.1e100.net (173.194.69.113): icmp_req=4 ttl=45 time=209 ms
64 bytes from 173.194.69.113: icmp_req=5 ttl=45 time=43.9 ms
64 bytes from 173.194.69.113: icmp_req=9 ttl=45 time=45.2 ms
64 bytes from 173.194.69.113: icmp_req=10 ttl=45 time=1014 ms
64 bytes from 173.194.69.113: icmp_req=11 ttl=45 time=48.3 ms
64 bytes from 173.194.69.113: icmp_req=14 ttl=45 time=149 ms
64 bytes from 173.194.69.113: icmp_req=15 ttl=45 time=147 ms
64 bytes from bk-in-f113.1e100.net (173.194.69.113): icmp_req=16 ttl=45 time=51.5 ms
64 bytes from bk-in-f113.1e100.net (173.194.69.113): icmp_req=17 ttl=45 time=226 ms
64 bytes from bk-in-f113.1e100.net (173.194.69.113): icmp_req=20 ttl=45 time=48.8 ms
64 bytes from bk-in-f113.1e100.net (173.194.69.113): icmp_req=23 ttl=45 time=145 ms
64 bytes from 173.194.69.113: icmp_req=24 ttl=45 time=45.9 ms
64 bytes from bk-in-f113.1e100.net (173.194.69.113): icmp_req=28 ttl=45 time=149 ms
64 bytes from 173.194.69.113: icmp_req=30 ttl=45 time=131 ms
64 bytes from 173.194.69.113: icmp_req=31 ttl=45 time=641 ms
64 bytes from 173.194.69.113: icmp_req=32 ttl=45 time=149 ms
64 bytes from 173.194.69.113: icmp_req=33 ttl=45 time=91.1 ms
64 bytes from bk-in-f113.1e100.net (173.194.69.113): icmp_req=35 ttl=45 time=73.4 ms
64 bytes from 173.194.69.113: icmp_req=37 ttl=45 time=46.1 ms
64 bytes from bk-in-f113.1e100.net (173.194.69.113): icmp_req=38 ttl=45 time=46.7 ms
64 bytes from bk-in-f113.1e100.net (173.194.69.113): icmp_req=39 ttl=45 time=41.0 ms
64 bytes from bk-in-f113.1e100.net (173.194.69.113): icmp_req=41 ttl=45 time=44.0 ms
64 bytes from 173.194.69.113: icmp_req=42 ttl=45 time=42.5 ms
64 bytes from 173.194.69.113: icmp_req=44 ttl=45 time=45.2 ms
64 bytes from bk-in-f113.1e100.net (173.194.69.113): icmp_req=45 ttl=45 time=48.7 ms
64 bytes from bk-in-f113.1e100.net (173.194.69.113): icmp_req=47 ttl=45 time=46.9 ms
64 bytes from bk-in-f113.1e100.net (173.194.69.113): icmp_req=48 ttl=45 time=46.0 ms
64 bytes from 173.194.69.113: icmp_req=50 ttl=45 time=46.3 ms
64 bytes from 173.194.69.113: icmp_req=51 ttl=45 time=146 ms
64 bytes from bk-in-f113.1e100.net (173.194.69.113): icmp_req=53 ttl=45 time=45.4 ms
64 bytes from bk-in-f113.1e100.net (173.194.69.113): icmp_req=54 ttl=45 time=117 ms
64 bytes from 173.194.69.113: icmp_req=55 ttl=45 time=49.6 ms
64 bytes from bk-in-f113.1e100.net (173.194.69.113): icmp_req=60 ttl=45 time=147 ms

```and something like apt-get update sometimes hangs on for ages waiting and downloading at some bBs.

Here is provided information as told by the wireless ticket sticky:

**lsusb**
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 07d1:3c0a D-Link System DWA-140 RangeBooster N Adapter(rev.B2) [Ralink RT3072]
Bus 003 Device 002: ID 1532:0016 Razer USA, Ltd 

```**iwconfig**
```
lo        no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"julie60sofia29mathilde"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: 70:71:BC:91:24:B9   
          Bit Rate=6.5 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=31/70  Signal level=-79 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1040  Invalid misc:637   Missed beacon:0

eth0      no wireless extensions.


```**lsmod**
```
Module                  Size  Used by
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61512  1 vfat
uas                    18027  0 
usb_storage            49198  1 
rt2800usb              22684  0 
rt2800lib              58925  1 rt2800usb
crc_ccitt              12667  1 rt2800lib
rt2x00usb              20762  1 rt2800usb
rt2x00lib              51205  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              506816  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              205544  2 rt2x00lib,mac80211
parport_pc             32866  0 
ppdev                  17113  0 
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
arc4                   12529  2 
snd_virtuoso           41045  2 
snd_oxygen_lib         41445  1 snd_virtuoso
snd_pcm                97188  1 snd_oxygen_lib
snd_page_alloc         18529  1 snd_pcm
snd_mpu401_uart        14169  1 snd_oxygen_lib
snd_seq_midi           13324  0 
snd_rawmidi            30748  2 snd_mpu401_uart,snd_seq_midi
adt7475                31231  0 
hwmon_vid              12827  1 adt7475
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  12 snd_virtuoso,snd_oxygen_lib,snd_pcm,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd
nouveau               774586  3 
mac_hid                13253  0 
ttm                    76949  1 nouveau
drm_kms_helper         42489  1 nouveau
drm                   241834  5 nouveau,ttm,drm_kms_helper
shpchp                 37277  0 
i2c_algo_bit           13423  1 nouveau
mxm_wmi                12979  1 nouveau
wmi                    19256  1 mxm_wmi
video                  19411  1 nouveau
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47199  0 
firewire_ohci          41000  0 
hid                    99559  1 usbhid
firewire_core          63558  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
pata_it8213            13079  0 
r8169                  62098  0 
floppy                 70365  0 

```**network configuration**
```
 *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@2:4
       logical name: wlan0
       serial: 14:d6:4d:3b:a5:2c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=3.2.0-18-generic firmware=0.29 ip=192.168.1.16 link=yes multicast=yes wireless=IEEE 802.11bgn

```**network scan**
```
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 70:71:BC:91:24:B9
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"julie60sofia29mathilde"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000e69e99ce3
                    Extra: Last beacon: 10196ms ago
                    IE: Unknown: 00166A756C69653630736F66696132396D617468696C6465
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030103
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1603080000000000000000000000000000000000000000
                    IE: Unknown: DD090010180205F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

eth0      Interface doesn't support scanning.

```I run Ubuntu 12.04 with the 3.2.0-18-generic 64 bit kernel.


Is there anything I can do to speed things up?


EDIT:
Solution was found here: [http://ubuntuforums.org/showthread.php?t=1859558&page=4](http://ubuntuforums.org/showthread.php?t=1859558&page=4) at post 32.

Many thanks to chili555 for your support and wildmanne39![U]
[/U]

---

### Post by chili555 on 2012-03-08
> wlan0     Scan completed :
          Cell 01 - Address: 70:71:BC:91:24:B9
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    [COLOR="Red"]Quality=29/70[/COLOR]  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"julie60sofia29mathilde"
<snip>What do you make of that? Are you in the same *building* with the router? Does the router have a power setting? Is it dialed up to maximum? Please see attached.

Is the result the same with the router on channel 1 or 11?

What firmware version are you using?```
md5sum /lib/firmware/rt2870.bin
```

---

### Post by cyberbot on 2012-03-09
> **chili555 said:**
> What do you make of that? Are you in the same *building* with the router? Does the router have a power setting? Is it dialed up to maximum? Please see attached.
I am in the same building as the router. It's separated by 2 walls, but I've never had problems with the connection in Windows 7 with the same device or with my laptop.
Unfortunately my ISP locks the router, so I am unable to enter it and configure the settings until Monday where I can contact them.

> What firmware version are you using?```
md5sum /lib/firmware/rt2870.bin
```I didn't have any firmware installed for rt2870 apparently. I downloaded it from Ralinks website and placed it there, but now it can't find any networks at all. 
The command returns
```
2bb89af3a7d446deb4695c9a3daa7f9d  /lib/firmware/rt2870.bin
```now.

EDIT: That's weird, now it can recognize networks but can't connect to them.

---

### Post by chili555 on 2012-03-09
> I didn't have any firmware installed for rt2870 apparently.You had to; it's required for the driver to function:```
$ modinfo rt2800usb 
filename:       /lib/modules/3.0.0-16-generic/updates/cw-3.1/rt2800usb.ko
license:        GPL
[COLOR="Red"]firmware:       rt2870.bin[/COLOR]
description:    Ralink RT2800 USB Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     2187927F491270EDE01C13C

```The firmware version you have now is obviously the latest. 

There is an update driver in Synaptic. You might look for and install linux-backports-modules-cw-3.1-oneiric-generic and see if it improves.

---

### Post by cyberbot on 2012-03-09
> **chili555 said:**
> You had to; it's required for the driver to function:```
$ modinfo rt2800usb 
filename:       /lib/modules/3.0.0-16-generic/updates/cw-3.1/rt2800usb.ko
license:        GPL
[COLOR=Red]firmware:       rt2870.bin[/COLOR]
description:    Ralink RT2800 USB Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     2187927F491270EDE01C13C

```The firmware version you have now is obviously the latest. 

There is an update driver in Synaptic. You might look for and install linux-backports-modules-cw-3.1-oneiric-generic and see if it improves.
Although it now runs just fine and with much improved speeds, it's still way below what I had on Windows. Currently I get ~10Mbps very unstable download speeds (it keeps going up and down) compared to the ~30Mbps I had on Windows and a much more stable speed at the same server. 
I tried building the rt2870sta driver from RaLink to see if it might help and managed to load the module and everything, but it's not being used at all (the rt2800usb was removed).
```
Module                  Size  Used by
arc4                   12529  0 
rt2870sta             629991  0 
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61512  1 vfat
parport_pc             32866  0 
ppdev                  17113  0 
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
snd_virtuoso           41045  2 
snd_oxygen_lib         41445  1 snd_virtuoso
snd_pcm                97188  1 snd_oxygen_lib
snd_page_alloc         18529  1 snd_pcm
snd_mpu401_uart        14169  1 snd_oxygen_lib
usbhid                 47199  0 
snd_seq_midi           13324  0 
snd_rawmidi            30748  2 snd_mpu401_uart,snd_seq_midi
adt7475                31231  0 
hwmon_vid              12827  1 adt7475
snd_seq_midi_event     14899  1 snd_seq_midi
hid                    99559  1 usbhid
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  12 snd_virtuoso,snd_oxygen_lib,snd_pcm,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13253  0 
soundcore              15091  1 snd
nouveau               774586  3 
ttm                    76949  1 nouveau
drm_kms_helper         42489  1 nouveau
drm                   241834  5 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13423  1 nouveau
mxm_wmi                12979  1 nouveau
wmi                    19256  1 mxm_wmi
video                  19411  1 nouveau
shpchp                 37277  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
firewire_ohci          41000  0 
firewire_core          63558  1 firewire_ohci
pata_it8213            13079  0 
crc_itu_t              12707  1 firewire_core
floppy                 70365  0 
r8169                  62098  0 
usb_storage            49198  1 
```

How do I make it use the driver? I really want to get the same speed as I had on Windows and <kernel 3.0 distros.

---

### Post by chili555 on 2012-03-09
I think you are not quite correct. It is being used:> Module                  Size  Used by
arc4                   12529  0 
[COLOR="Red"]rt2870sta[/COLOR]             629991  0 
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61512  1 vfat
parport_pc             32866  0 
<snip>If you think it's not being used because there is a little zero after it, that's incorrect. That zero means there are no other modules depending on it or that it depends on. That's logical:```
modinfo rt2870sta
```> filename:       Desktop/Forum/bigtdp/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/rt2870sta.ko
version:        2.4.0.0
license:        GPL
description:    RT2870 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
srcversion:     0595725479628E15C80661B
<snip>
[COLOR="Red"]depends:[/COLOR]        
vermagic:       2.6.38-10-generic SMP mod_unload modversions 686 
parm:           mac:rt28xx: wireless mac addr (charp)As you can see, it depends on nothing...zero.

FWIW, my copy of rt2870sta runs 692kb compared to the built-in rt2800usb that runs 44kb but has several dependencies; rt2x00lib,rt2800lib and rt2x00usb.

If your wireless is working at all and rt2870sta is the only rt2xxx that's loaded, you are assured it's being used.

---

### Post by cyberbot on 2012-03-09
> **chili555 said:**
> I think you are not quite correct. It is being used:If you think it's not being used because there is a little zero after it, that's incorrect. That zero means there are no other modules depending on it or that it depends on. That's logical:```
modinfo rt2870sta
```As you can see, it depends on nothing...zero.

FWIW, my copy of rt2870sta runs 692kb compared to the built-in rt2800usb that runs 44kb but has several dependencies; rt2x00lib,rt2800lib and rt2x00usb.

If your wireless is working at all and rt2870sta is the only rt2xxx that's loaded, you are assured it's being used.
Ah, I actually did think it was the 0 which meant it wasn't being used. It doesn't detect any wireless device with only the rt2870sta loaded though.

---

### Post by chili555 on 2012-03-09
It sounds like rt2870sta doesn't claim your device (he says knowingly!); check with:```
modinfo rt2870sta | grep 3C0A
```That's three-cee-zero-ay. We get 3C0A from your usb.id:> ID 07d1:[COLOR="Red"]3c0a[/COLOR] D-Link System DWA-140 RangeBooster N Adapter(rev.B2) [Ralink RT3072]What did you get? Nothing, I bet. That means the module doesn't know about your device.

I bet you'd like to try to get it to work anyway, wouldn't you? Umm hmm. Go into the various files you used to compile the driver. Open common > rtusb_dev_id.c with any text editor, gedit for example. Make the changes I've highlighted below. Spacing, puntuation, brackets, etc. are crucial and must be exactly correct. Proofread twice, get a glass of water and proofread again!

Just add the one line I've highlighted. All the rest of the file must be unchanged.> /* module table */
USB_DEVICE_ID rtusb_dev_id[] = {
#ifdef RT2870
	{USB_DEVICE(0x148F,0x2770)}, /* Ralink */
	[COLOR="Red"]{USB_DEVICE(0x07D1,0x3C0A)}, /* D-link */[/COLOR]
	{USB_DEVICE(0x148F,0x2870)}, /* Ralink */
	{USB_DEVICE(0x07B8,0x2870)}, /* AboCom */
	{USB_DEVICE(0x07B8,0x2770)}, /* AboCom */
	{USB_DEVICE(0x0DF6,0x0039)}, /* Sitecom 2770 */After you have proofread carefully, save and close the text editor. Now we must recompile:```
cd Desktop/RT2870files   <--or wherever you extracted the files
sudo su
make clean
make
make install
modprobe -rv rt2870sta
modprobe rt2870sta
exit
```There is no guarantee and some doubt that this will be an effective fix; however, the only way to surely lose the race is not show up.

---

### Post by cyberbot on 2012-03-09
Hm, at least it feels like we're making progress.
It now recognizes it as a wireless device and shows up as
```
rt2870sta             629991  1 

```
in lsmod. There are still no networks and it doesn't load at start like the rt2800usb, though.
I have a friend who owns a Netgear N600 (WNDA3100) and I might be able to trade my D-Link adapter for that, do you think that'd be a good idea?

---

### Post by chili555 on 2012-03-09
> Netgear N600 (WNDA3100) and I might be able to trade my D-Link adapter for that, do you think that'd be a good idea?It's a bit tricky but do-able. I don't know that you'll get any better performance at all, however, from this:```
wlan0     Scan completed :
          Cell 01 - Address: 70:71:BC:91:24:B9
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    [COLOR="Red"]Quality=29/70[/COLOR]  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"julie60sofia29mathilde"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
```Have you been able to make any changes in the router? Additionally, I get better performance from my router standing on its nose; please see attached.

I'd be very glad to work with you to try the Netgear N600. Can you try it temporarily?

---

### Post by cyberbot on 2012-03-10
> **chili555 said:**
> It's a bit tricky but do-able. I don't know that you'll get any better performance at all, however, from this:```
wlan0     Scan completed :
          Cell 01 - Address: 70:71:BC:91:24:B9
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    [COLOR=Red]Quality=29/70[/COLOR]  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"julie60sofia29mathilde"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
```Have you been able to make any changes in the router? Additionally, I get better performance from my router standing on its nose; please see attached.

I'd be very glad to work with you to try the Netgear N600. Can you try it temporarily?
I'm still unable to access the router, unfortunately. I've tried the trick with setting the router on its nose without any performance increase, however I've placed the DWA-140 device and cable in extension of the N600 cable with a small increase. The quality is now 31/70, speeds remain about the same. It seems weird that it'd be a problem with the router since it worked so well in Windows and older distros.

I've tried plugging in the N600, but it doesn't detect it as a wireless device, it seems.

lsusb
```
Bus 002 Device 006: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]
```

iwconfig
```
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      no wireless extensions.

```

lsmod
```
Module                  Size  Used by
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61512  1 vfat
bnep                   18281  2 
rfcomm                 47604  0 
parport_pc             32866  0 
ppdev                  17113  0 
bluetooth             180104  10 bnep,rfcomm
vesafb                 13809  1 
arc4                   12529  0 
snd_virtuoso           41045  2 
snd_oxygen_lib         41445  1 snd_virtuoso
snd_pcm                97188  1 snd_oxygen_lib
snd_page_alloc         18529  1 snd_pcm
snd_mpu401_uart        14169  1 snd_oxygen_lib
snd_seq_midi           13324  0 
nvidia              12294232  40 
snd_rawmidi            30748  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  12 snd_virtuoso,snd_oxygen_lib,snd_pcm,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd
mac_hid                13253  0 
usbhid                 47199  0 
hid                    99559  1 usbhid
shpchp                 37277  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
floppy                 70365  0 
firewire_ohci          41000  0 
pata_it8213            13079  0 
firewire_core          63558  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
r8169                  62098  0 
usb_storage            49198  1 

```

I really appreciate your willingness to help a Ubuntu newcomer like me. :)

---

### Post by chili555 on 2012-03-10
The process to install it involves ndiswrapper. Please see post #29 here: [http://ubuntuforums.org/showthread.php?t=1695036&highlight=bcmwlhigh5&page=3](http://ubuntuforums.org/showthread.php?t=1695036&highlight=bcmwlhigh5&page=3)

The actual files are sligtly different. Download and use the files I've attached here, rather than at post #29. Also, instead of 'cd Desktop/wna3100-drivers' you will instead:```
cd Desktop/ndis_bcmwl
etc., etc.
```

As always, post back if you get stuck.

---

### Post by cyberbot on 2012-03-10
> **chili555 said:**
> The process to install it involves ndiswrapper. Please see post #29 here: [http://ubuntuforums.org/showthread.php?t=1695036&highlight=bcmwlhigh5&page=3](http://ubuntuforums.org/showthread.php?t=1695036&highlight=bcmwlhigh5&page=3)

The actual files are sligtly different. Download and use the files I've attached here, rather than at post #29. Also, instead of 'cd Desktop/wna3100-drivers' you will instead:```
cd Desktop/ndis_bcmwl
etc., etc.
```As always, post back if you get stuck.
That works, but the internet stops abruptly under load (downloading a file or even running a test on speedtest.net) and I have to reboot to get it working.

EDIT: Something like logging onto Skype also shuts it down, so it doesn't take much.

this is the dmesg output after it stops
```

*zip*
[   15.582959] init: failsafe main process (767) killed by TERM signal
[   15.584914] init: hybrid-gfx main process (964) terminated with status 127
[   19.538724] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[   29.800009] wlan1: no IPv6 routers present
[   51.779444] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   62.547669] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[   80.816011] wlan1: no IPv6 routers present

```iwconfig (if it's to any use)
```

lo        no wireless extensions.

wlan1     IEEE 802.11g  ESSID:"julie60sofia29mathilde"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: 70:71:BC:91:24:B9   
          Bit Rate=52 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:42/100  Signal level:-69 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:27  Invalid misc:1161   Missed beacon:0

eth1      no wireless extensions.

eth0      no wireless extensions.

```

---

### Post by chili555 on 2012-03-10
I see the link quality is slightly improved. Are the other drivers rt28xx unloaded?```
lsmod | grep rt2
```Are there any informative messages about ndiswrapper itself?```
dmesg | grep ndis
```

---

### Post by cyberbot on 2012-03-10
> **chili555 said:**
> I see the link quality is slightly improved. Are the other drivers rt28xx unloaded?```
lsmod | grep rt2
```Are there any informative messages about ndiswrapper itself?```
dmesg | grep ndis
```
This is output of dmesg | grep ndis
```

[    7.836503] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
[    9.000627] ndiswrapper: driver bcmwlhigh5 (Netgear,05/05/2009, 5.10.79.30) loaded
[    9.259220] usbcore: registered new interface driver ndiswrapper
[    9.276338] ndiswrapper: changing interface name from 'wlan0' to 'wlan1'

```

Could it have something to do with my network being WPA? It says WPA-Personal and AES encryption on Windows.

---

### Post by chili555 on 2012-03-10
> [    7.836503] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
[    9.000627] ndiswrapper: driver bcmwlhigh5 (Netgear,05/05/2009, 5.10.79.30) loaded
[    9.259220] usbcore: registered new interface driver ndiswrapper
[    9.276338] ndiswrapper: changing interface name from 'wlan0' to 'wlan1'Looks perfect!> Could it have something to do with my network being WPA?Perhaps it's having trouble with mixed mode WPA and WPA2. Let's have a peek at:```
sudo iwlist wlan1 scan
sudo iwlist wlan1 auth
ndiswrapper -l
```That's l for **l**ist. Thanks.

---

### Post by cyberbot on 2012-03-10
> **chili555 said:**
> Looks perfect!Perhaps it's having trouble with mixed mode WPA and WPA2. Let's have a peek at:```
sudo iwlist wlan1 scan
sudo iwlist wlan1 auth
ndiswrapper -l
```That's l for **l**ist. Thanks.
iwlist wlan1 scan
```
wlan1     Scan completed :
          Cell 01 - Address: 70:71:BC:91:24:B9
                    ESSID:"julie60sofia29mathilde"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.422 GHz (Channel 3)
                    Quality:45/100  Signal level:-67 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 00166A756C69653630736F66696132396D617468696C6465
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030103
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1603080400000000000000000000000000000000000000
                    IE: Unknown: DD090010180202F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: 00:24:93:34:53:B0
                    ESSID:"Internet"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:10/100  Signal level:-89 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 0008496E7465726E6574
                    IE: Unknown: 010582848B960C
                    IE: Unknown: 030101
                    IE: Unknown: 050C010200000000000000000000
                    IE: Unknown: 2A0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

```
iwlist wlan1 auth

```

wlan1     Authentication capabilities :
        WPA
        WPA2
        CIPHER-TKIP
        CIPHER-CCMP
          Current WPA version :
        WPA
          Current Key management :
        PSK
          Current Pairwise cipher :
        CCMP
          Current Pairwise cipher :
        TKIP
          Current Authentication algorithm :
        open


```ndiswrapper -l
```

bcmwlhigh5 : driver installed
    device (0846:9011) present

```

---

### Post by chili555 on 2012-03-10
Also looks perfect. I am not so sure we have ndiswrapper to blame. What do the logs say at and after the crash. Please run:```
sudo cat /var/log/syslog
```Note the timestamp at the last line; for example:> Mar 10 08:54:00 LAPTOP60 wpa_supplicant[11169]: WPA: Key negotiation completed with 99:13:10:62:88:77 [PTK=CCMP GTK=CCMP]
Mar 10 [COLOR="Red"]08:54:00[/COLOR] LAPTOP60 wpa_supplicant[11169]: CTRL-EVENT-CONNECTED - Connection to 99:13:10:62:88:77 completed (reauth) [id=0 id_str=]
Provoke the crash and reboot. Then run:```
sudo less /var/log/syslog
```'less' will allow you to use the arrow keys to scroll back and forth through the log to see what happened right after your noted timestamp. You can copy and paste from the terminal to a text document so you can post it here and Google it.> Current Authentication algorithm :
        openWere you connected at the time? Does ndiswrapper mis-report the authentication details?

---

### Post by cyberbot on 2012-03-10
> **chili555 said:**
> Also looks perfect. I am not so sure we have ndiswrapper to blame. What do the logs say at and after the crash. Please run:```
sudo cat /var/log/syslog
```Note the timestamp at the last line; for example:Provoke the crash and reboot. Then run:```
sudo less /var/log/syslog
```'less' will allow you to use the arrow keys to scroll back and forth through the log to see what happened right after your noted timestamp. You can copy and paste from the terminal to a text document so you can post it here and Google it.Were you connected at the time? Does ndiswrapper mis-report the authentication details?
```
Mar 10 15:56:05 goblet kernel: [   91.656011] wlan1: no IPv6 routers present
Mar 10 15:56:10 goblet kernel: [   96.837827] ndiswrapper (iw_get_auth:1659): invalid cmd 4
Mar 10 15:56:10 goblet kernel: [   96.837830] ndiswrapper (iw_get_auth:1659): invalid cmd 5
Mar 10 15:56:10 goblet kernel: [   96.837840] ndiswrapper (iw_get_auth:1659): invalid cmd 8
Mar 10 15:56:10 goblet kernel: [   96.837842] ndiswrapper (iw_get_auth:1659): invalid cmd 9
Mar 10 15:56:10 goblet kernel: [   96.837845] ndiswrapper (iw_get_auth:1659): invalid cmd 10
Mar 10 15:56:15 goblet NetworkManager[835]: <info> (wlan1): IP6 addrconf timed out or failed.
Mar 10 15:56:15 goblet NetworkManager[835]: <info> Activation (wlan1) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Mar 10 15:56:15 goblet NetworkManager[835]: <info> Activation (wlan1) Stage 4 of 5 (IPv6 Configure Timeout) started...
Mar 10 15:56:15 goblet NetworkManager[835]: <info> Activation (wlan1) Stage 4 of 5 (IPv6 Configure Timeout) complete.

```This is from during and after the crash.
I googled the invalid cmd parts and saw others were having trouble with WPA connections and ndiswrapper. I'll try looking at how to configure the wpa_supplicant.conf file and see if it might help.
EDIT: Hm, that didn't seem to work, partially because I have little clue how it actually works.

>  Were you connected at the time?Yes.
> Does ndiswrapper mis-report the authentication details?I'm not quite sure what that is.

---

### Post by chili555 on 2012-03-10
> [ 7.836503] ndiswrapper version [COLOR="Red"]1.57[/COLOR] loaded (smp=yes, preempt=no)Is this a default, Ubuntu-from-the-repositories version or did you build a tar.gz?

I really thought the invalid cmd was fixed a long time ago.

Can you give me a link to what you are working on at the wpa_supplicant.conf file?

---

### Post by cyberbot on 2012-03-10
> **chili555 said:**
> Is this a default, Ubuntu-from-the-repositories version or did you build a tar.gz?

I really thought the invalid cmd was fixed a long time ago.

Can you give me a link to what you are working on at the wpa_supplicant.conf file?
I downloaded the latest release from sourceforge and built it.
I was following this for wpa_supplicant.conf
[http://wiki.zenwalk.org/index.php?title=Wpa_supplicant](http://wiki.zenwalk.org/index.php?title=Wpa_supplicant)
but when I got to
```
wpa_supplicant -i wlan1 -D wext -c /etc/wpa_supplicant.conf -B
```it returned
```
ioctl[SIOCSIWENCODEEXT]: Invalid argument
ioctl[SIOCSIWENCODEEXT]: Invalid argument
```My file looks like this:

```
network={
ssid="julie60sofia29mathilde"
key_mgmt=WPA-PSK
proto=WPA
pairwise=CCMP TKIP
group=CCMP TKIP
#psk="*removed*"
psk=*removed*
}
```

---

### Post by chili555 on 2012-03-10
I don't think you need any of that if Network Manager is working correctly. Isn't it?

In fact, even if you have removed NM, you can set up /etc/network/interfaces *without* /etc/wpa_supplicant.conf. Just like I have done! Less is more.

---

### Post by cyberbot on 2012-03-10
I googled around a bit and found this.
[http://forums.linuxmint.com/viewtopic.php?f=53&t=43820&start=0](http://forums.linuxmint.com/viewtopic.php?f=53&t=43820&start=0)
I'll try it out and report back with results. I hope this is the rock in the machinery.

EDIT: Ach, that did nothing.

---

### Post by cientista99 on 2012-07-05
I don't know if i will help but i had that problem...

I have a conceptronic device that use the rt2800usb in my linux kernel 3.1 and used to be very very slow: less than 1 Mbps in a 120 Mbps connection..

After a long search and nothing resolved i remember a similar problem that i had in my internal laptop wifi device that i resolved downloading, compiling, installing the compat-wireless release from [http://linuxwireless.org/en/users/Download/stable/](http://linuxwireless.org/en/users/Download/stable/) website. 
I did the same process choosing the rt2x00 driver in a script inside the package.

After the installation and a reboot, i just plug the wifi device and everything is perfect.:lolflag:

I don't know if ubuntu has a more easy way to install with apt-get (i'm a openSUSE user, i don't know ubuntu very well).

Hope i help (sorry for my bad english)...

---

