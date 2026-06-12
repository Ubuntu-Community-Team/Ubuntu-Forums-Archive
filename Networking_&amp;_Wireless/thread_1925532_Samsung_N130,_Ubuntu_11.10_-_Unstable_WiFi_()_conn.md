---
title: "Samsung N130, Ubuntu 11.10 - Unstable WiFi (?) connection"
date: 2012-02-14
forum: Networking &amp; Wireless
---

### Post by sjaakiejj on 2012-02-14
Hi,

I've recently bought a second hand Samsung n130 netbook, and had to do a little bit of renovation work (On/Off switch had broken off, screws had been rounded, etc) to get it running again. When opening the case I noticed that the people who owned it before me had, quite carelessly, damaged the wifi cable lightly by closing the case with the cable hanging half out. Regardless, everything else seemed well, and WiFi appeared to work in Windows.

So as any self-respecting geek would do, I instantly got rid of Windows and installed Linux. Ubuntu in this case due to its painless installation procedure. Everything worked... except for WiFi. It would disconnect soon after boot, and would only reconnect after a computer reboot... Not ideal. After a bit of hassle, I replaced the original Ubuntu drivers for the WiFi connection with Samsung specific ones, and WiFi came back to life. At least, that's what I thought - It worked for a few minutes, then did the same thing again. A stealth "disconnect" from internet - but not from the network! In fact, things only got weirder. After being disconnected, I decided to ping the router to see if I had any hardware problems. I got ping back as usual. Then I tried [www.google.com](www.google.com) - and I got ping back! This is the case every time it "disconnects" from the internet. It seems that it can pass packets of data to and from the internet, but can't actually "connect" to websites unless I reconnect to the WiFi network. 

So here's some command outputs:

ping [www.google.com](www.google.com)
```

PING www.l.google.com (209.85.229.99) 56(84) bytes of data.
64 bytes from ww-in-f99.1e100.net (209.85.229.99): icmp_req=1 ttl=52 time=31.6 ms
64 bytes from ww-in-f99.1e100.net (209.85.229.99): icmp_req=2 ttl=52 time=30.0 ms
64 bytes from ww-in-f99.1e100.net (209.85.229.99): icmp_req=3 ttl=52 time=30.1 ms

```

lspci -nnk | grep -iA2 net
```

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8192E/RTL8192SE Wireless LAN Controller [10ec:8192] (rev 01)
	Subsystem: Askey Computer Corp. Device [144f:7160]
	Kernel driver in use: rtl819xE
--
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
	Subsystem: Samsung Electronics Co Ltd Device [144d:c04d]
	Kernel driver in use: r8169

```

ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:24:54:0e:22:c9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:42 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:26:b6:1f:9c:44  
          inet addr:192.168.1.182  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:b6ff:fe1f:9c44/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21366 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10045 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:30122125 (30.1 MB)  TX bytes:646626 (646.6 KB)
          Interrupt:16 Memory:f83b0000-f83b0100 

```


iwconfig wlan0
```

wlan0     802.11bgn  ESSID:"O2wirelessF2D671"  Nickname:"rtl8192E"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:26:44:F2:D6:71   
          Bit Rate=65 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management period:0us  mode:All packets received
          Link Quality=93/100  Signal level=-72 dBm  Noise level=-116 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

lsmod
```

Module                  Size  Used by
michael_mic            12540  8 
arc4                   12473  4 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
joydev                 17393  0 
snd_hda_codec_realtek   254125  1 
snd_hda_intel          24262  2 
snd_hda_codec          91859  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
r8192e_pci_realtek    360045  0 
rtl8192se              94139  0 
rtlwifi                95614  1 rtl8192se
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
mac80211              393459  2 rtl8192se,rtlwifi
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
psmouse                73673  0 
serio_raw              12990  0 
cfg80211              172427  2 rtlwifi,mac80211
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
binfmt_misc            17292  1 
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i915                  509487  3 
drm_kms_helper         32889  1 i915
drm                   192194  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
r8169                  43104  0 

```

dmesg | grep rtl
```

[ 1880.304219] =====>rtl8192_set_chan()====ch:3
[ 1880.424215] =====>rtl8192_set_chan()====ch:4
[ 1880.544134] =====>rtl8192_set_chan()====ch:5
[ 1880.664125] =====>rtl8192_set_chan()====ch:6
[ 1880.784101] =====>rtl8192_set_chan()====ch:7
[ 1880.904092] =====>rtl8192_set_chan()====ch:8
[ 1881.024090] =====>rtl8192_set_chan()====ch:9
[ 1881.144114] =====>rtl8192_set_chan()====ch:10
[ 1881.264102] =====>rtl8192_set_chan()====ch:11
[ 1881.384153] =====>rtl8192_set_chan()====ch:12
[ 1881.504103] =====>rtl8192_set_chan()====ch:13
[ 1881.624113] =====>rtl8192_set_chan()====ch:11
[ 1887.404580] rtl8192e_SetHwReg():HW_VAR_AC_PARAM eACI:0:a42b
[ 1887.404624] ===========>rtl8192e_SetHwReg():HW_VAR_ACM_CTRL:0
[ 1933.496495] rtl8192e_SetHwReg():HW_VAR_AC_PARAM eACI:0:a42b
[ 1933.496532] ===========>rtl8192e_SetHwReg():HW_VAR_ACM_CTRL:0
[ 2000.060262] =====>rtl8192_set_chan()====ch:1
[ 2000.180125] =====>rtl8192_set_chan()====ch:2
[ 2000.300158] =====>rtl8192_set_chan()====ch:3
[ 2000.420124] =====>rtl8192_set_chan()====ch:4
[ 2000.540160] =====>rtl8192_set_chan()====ch:5
[ 2000.660104] =====>rtl8192_set_chan()====ch:6
[ 2000.780150] =====>rtl8192_set_chan()====ch:7
[ 2000.900157] =====>rtl8192_set_chan()====ch:8
[ 2001.020144] =====>rtl8192_set_chan()====ch:9
[ 2001.140089] =====>rtl8192_set_chan()====ch:10
[ 2001.260084] =====>rtl8192_set_chan()====ch:11
[ 2001.380099] =====>rtl8192_set_chan()====ch:12
[ 2001.500087] =====>rtl8192_set_chan()====ch:13
[ 2001.620194] =====>rtl8192_set_chan()====ch:11
[ 2120.060208] =====>rtl8192_set_chan()====ch:1
[ 2120.180103] =====>rtl8192_set_chan()====ch:2
[ 2120.300103] =====>rtl8192_set_chan()====ch:3
[ 2120.420086] =====>rtl8192_set_chan()====ch:4
[ 2120.540092] =====>rtl8192_set_chan()====ch:5
[ 2120.660086] =====>rtl8192_set_chan()====ch:6
[ 2120.780103] =====>rtl8192_set_chan()====ch:7
[ 2120.900109] =====>rtl8192_set_chan()====ch:8
[ 2121.020138] =====>rtl8192_set_chan()====ch:9
[ 2121.140116] =====>rtl8192_set_chan()====ch:10
[ 2121.260099] =====>rtl8192_set_chan()====ch:11
[ 2121.380113] =====>rtl8192_set_chan()====ch:12
[ 2121.500082] =====>rtl8192_set_chan()====ch:13
[ 2121.620153] =====>rtl8192_set_chan()====ch:11

```

sudo lshw -C network
```

PCI (sysfs)  
  *-network               
       description: Wireless interface
       product: RTL8192E/RTL8192SE Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:26:b6:1f:9c:44
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xE driverversion=0015.1013.2010 ip=192.168.1.182 latency=0 link=yes multicast=yes wireless=802.11bgn
       resources: irq:16 ioport:2000(size=256) memory:f0100000-f0103fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:24:54:0e:22:c9
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=N/A latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:3000(size=256) memory:f0510000-f0510fff memory:f0500000-f050ffff memory:f0520000-f053ffff

```

iwlist scan
```

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:26:44:F2:D6:71
                    ESSID:"O2wirelessF2D671"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:130 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality=88/100  Signal level=-84 dBm  Noise level=-114 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 38ms ago


```

Kernel: 3.0.0-15-generic i686

Thanks in advance for any time and effort. I'm completely at a loss here :(

---

### Post by PaulW2U on 2012-02-14
I've tried for hours to get wi-fi working on my N130. I almost succeeded but when I resume from suspend wi-fi refuses to work. :(

Have you seen the [Linux On My Samsung](http://www.voria.org/forum/) website? There's also a PPA with some files to download that should help.

---

### Post by sjaakiejj on 2012-02-14
> **PaulW2U said:**
> I've tried for hours to get wi-fi working on my N130. I almost succeeded but when I resume from suspend wi-fi refuses to work. :(

Have you seen the [Linux On My Samsung](http://www.voria.org/forum/) website? There's also a PPA with some files to download that should help.

Thanks for the swift response. That's actually where I got the driver I'm using now, and it's better than the original Ubuntu ones, but it's still not working as it should :(

---

### Post by sjaakiejj on 2012-02-15
Bump, in the hope of getting this solved :(

---

