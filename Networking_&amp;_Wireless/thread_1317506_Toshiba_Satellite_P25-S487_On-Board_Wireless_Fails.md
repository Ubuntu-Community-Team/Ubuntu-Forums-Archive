---
title: "Toshiba Satellite P25-S487 On-Board Wireless Fails to Connect (WPA2)"
date: 2009-11-06
forum: Networking &amp; Wireless
---

### Post by rearviewmirror on 2009-11-06
I just installed 9.10 on this Toshiba laptop, the wireless was working fine with XP and had worked in the past with Ubuntu and Fedora.  Currently I am using a Linksys USB wifi interface to post this, but ideally I'd like to get the on-work wlan interface working.  The interesting bit is that in the upper right corner when I click on the wifi icon I can see my AP SSID there, when I click it, it requests a WEP key, which is fine, but I run WPA2.  I try to configure it through the system preferences using the WPA2 option and it doesn't connect.  Following the same process with the Linksys USB wlan interface I had no issues.  So where do I go from here?  I did a bunch of reading and ran a bunch of iw* commands and what not to no avail.

Edit.. from the info below it appears eth1 (on-board wlan int) scanning the network and working, but it won't connect, I didn't try WEP with it, but it definitely won't connect with WPA2.

1 ) Machine Brand and Model (PC/Laptop):

```
Toshiba Satellite P25-S487
```

2 ) Wireless Brand, Model and Wireless Chipset:

```
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:02.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)

```

3 ) check interface:  (Interesting that the on-board shows up as eth1 (is a wlan interface), wlan 1 is my linksys USB interface.

```
eth1      IEEE 802.11b  ESSID:"dildog"  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.457 GHz  Access Point: None   
          Bit Rate:2 Mb/s   Sensitivity:1/3  
          Retry limit:4   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/92  Signal level=-122 dBm  Noise level=-122 dBm
          Rx invalid nwid:0  Rx invalid crypt:2  Rx invalid frag:5
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wmaster0  no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:"dildog"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: 00:25:9C:14:0C:62   
          Bit Rate=48 Mb/s   Tx-Power=13 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=66/70  Signal level=-44 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

4 ) Check for modules:

```
anthony@rvmlinux:/etc/apt$ lsmod
Module                  Size  Used by
aes_i586                8124  3 
aes_generic            27484  1 aes_i586
arc4                    1660  2 
ecb                     2524  2 
rt73usb                26336  0 
crc_itu_t               1852  1 rt73usb
rt2x00usb              11548  1 rt73usb
rt2x00lib              29756  2 rt73usb,rt2x00usb
led_class               4096  1 rt2x00lib
input_polldev           3716  1 rt2x00lib
mac80211              181236  2 rt2x00usb,rt2x00lib
cfg80211               93052  2 rt2x00lib,mac80211
binfmt_misc             8356  1 
snd_intel8x0           30168  2 
snd_ac97_codec        101216  1 snd_intel8x0
orinoco_cs             13312  1 
orinoco                63600  1 orinoco_cs
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
pcmcia                 36808  1 orinoco_cs
yenta_socket           24200  5 
rsrc_nonstatic         11644  1 yenta_socket
pcmcia_core            35792  4 orinoco_cs,pcmcia,yenta_socket,rsrc_nonstatic
joydev                 10272  0 
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
parport_pc             31940  1 
psmouse                56180  0 
serio_raw               5280  0 
ppdev                   6688  0 
lp                      8964  0 
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
shpchp                 32272  0 
parport                35340  3 parport_pc,ppdev,lp
snd_rawmidi            22208  1 snd_seq_midi
irda                  189564  0 
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
crc_ccitt               1852  1 irda
iptable_filter          3100  0 
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
8139too                22620  0 
8139cp                 19260  0 
mii                     5212  2 8139too,8139cp
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
floppy                 54916  0 
video                  19380  0 
output                  2780  1 video
intel_agp              27484  1 
agpgart                34988  1 intel_agp

```

5 ) Kernel boot messages

```
[   19.756044] pcmcia 0.0: pcmcia: registering new device pcmcia0.0
[   20.367127] orinoco 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel 
Roskin <proski@gnu.org>, et al)
[   20.370293] orinoco_cs 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pav
el Roskin <proski@gnu.org>, et al)
[   20.452080] eth1: Hardware identity 0005:0004:0005:0000
[   20.452196] eth1: Station identity  001f:0001:0008:000a
[   20.452201] eth1: Firmware determined as Lucent/Agere 8.10
[   20.452208] orinoco_cs 0.0: firmware: requesting agere_sta_fw.bin
[   20.609737] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 1
7
[   20.734008] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x820-0x8ff: clea
n.
[   20.734654] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xc00-0xcf7: clea
n.
[   20.735526] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xa00-0xaff: clea
n.
[   20.760445] eth1: Attempting to download firmware agere_sta_fw.bin
[   20.760472] hermes_dld: AUX enable returned 0
[   20.761375] hermes_dld: AUX disable returned 0
[   20.761380] hermes_dld: Actual PDA length 998, Max allowed 1000
[   20.761384] eth1: Read PDA returned 0
[   20.761390] orinoco_cs 0.0: firmware: requesting agere_sta_fw.bin
[   20.768457] eth1: Cannot find firmware agere_sta_fw.bin
[   20.768528] eth1: Hardware identity 0005:0004:0005:0000
[   20.768635] eth1: Station identity  001f:0001:0008:000a
[   20.768642] eth1: Firmware determined as Lucent/Agere 8.10
[   20.768646] eth1: Ad-hoc demo mode supported
[   20.768649] eth1: IEEE standard IBSS ad-hoc mode supported
[   20.768653] eth1: WEP supported, 104-bit key
[   20.768737] eth1: MAC address 00:02:2d:b2:4e:50
[   20.768833] eth1: Station name "HERMES I"
[   20.769401] eth1: ready
[   20.771022] eth1: orinoco_cs at 0.0, irq 18, io 0x3100-0x313f
[   21.045546] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   21.267853] eth1: New link status: Disconnected (0002)
[   21.436836] intel8x0_measure_ac97_clock: measured 52082 usecs (2509 samples)
[   21.436842] intel8x0: clocking to 48000


```

6 ) Network configuration

```
anthony@rvmlinux:/etc/apt$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:02:3f:81:52:2a
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:17 ioport:3000(size=256) memory:c2004800-c20048ff
  *-network
       description: Wireless LAN Card
       product: Version 01.01
       vendor: TOSHIBA
       physical id: 0
       slot: Socket 0
       resources: irq:18
  *-network:0
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:02:2d:b2:4e:50
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Lucent/Agere 8.10 link=no multicast=yes wireless=IEEE 802.11b
  *-network:1
       description: Wireless interface
       physical id: 3
       logical name: wlan1
       serial: 00:22:6b:a3:5d:dc
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.7 multicast=yes wireless=IEEE 802.11bg

```

7 ) Scan for networks:

```
anthony@rvmlinux:/etc/apt$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:25:9C:14:0C:62
                    ESSID:"dildog"
                    Mode:Master
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Signal level:-41 dBm  Noise level:-98 dBm
                    Encryption key:on
                    Extra:bcn_int=100
                    Extra:capab=0x0411
                    Extra: Last beacon: 74732ms ago
          Cell 02 - Address: 00:15:E9:1B:4B:A8
                    ESSID:"TD Home"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Signal level:-73 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Extra:bcn_int=100
                    Extra:capab=0x0431
                    Extra: Last beacon: 74732ms ago

wmaster0  Interface doesn't support scanning.

wlan1     Scan completed :
          Cell 01 - Address: 00:25:9C:14:0C:62
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"dildog"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000035b12444a8
                    Extra: Last beacon: 65292ms ago
                    IE: Unknown: 000664696C646F67
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030108
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020004


```

8 ) Ubuntu Version: 

```
anthony@rvmlinux:/etc/apt$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 9.10
Release:	9.10
Codename:	karmic

```

9 ) Kernel/architecture (including 32 vs. 64 bit): 

```
anthony@rvmlinux:/etc/apt$ uname -mr
2.6.31-14-generic i686

```

---

### Post by rearviewmirror on 2009-11-06
:p

Hey.. any experts on this.. I think it's a driver issue, I'm just not sure how to fix it.

thanks!

---

### Post by rearviewmirror on 2009-11-07
:D

I still haven't solved it!

---

### Post by Roasted on 2009-11-07
Just a thought, not too sure where to go with this, but what if you delete your existing connection and re-scan for the wifi network again? I've had issues with Windows at work on our wifi network, and sometimes that's what I had to do to make it work again. Just a thought.

---

### Post by rearviewmirror on 2009-11-07
> **Roasted said:**
> Just a thought, not too sure where to go with this, but what if you delete your existing connection and re-scan for the wifi network again? I've had issues with Windows at work on our wifi network, and sometimes that's what I had to do to make it work again. Just a thought.

I did re-scan, the card sees the network, it just won't actually talk to it.  Again, I think it's a driver issue, but I really can't tell.

---

### Post by rearviewmirror on 2009-11-07
lshw -C network

On-board card showed as eth1 (not a wlan, but is a wlan interface).
```

  *-network:0
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:02:2d:b2:4e:50
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Lucent/Agere 8.10 link=no multicast=yes wireless=IEEE 802.11b
```

Linksys USB adapter which is working fine....

```
 *-network:1
       description: Wireless interface
       physical id: 3
       logical name: wlan1
       serial: 00:22:6b:a3:5d:dc
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.7 multicast=yes wireless=IEEE 802.11bg

```

---

### Post by Roasted on 2009-11-08
Did you not copy/paste right, or am I seeing that one sees the card as B and the other as BG? Not sure if it matters, but... just something I noticed.

---

### Post by rearviewmirror on 2009-11-08
> **Roasted said:**
> Did you not copy/paste right, or am I seeing that one sees the card as B and the other as BG? Not sure if it matters, but... just something I noticed.

The on-board is B only, the Linksys USB wifi is B/G.  My AP will support B or G.

---

### Post by rearviewmirror on 2009-11-08
Maybe the ubuntu night shift has a few ideas?

---

### Post by Roasted on 2009-11-08
So, let me get this straight - Your wireless card (internal) is B only, yet it supports WPA2 security in Windows?

Somehow the stars in my head just aren't lining up right hearing that. B is pretty darn old... much older than WPA2 I would think. The wifi card in my iBook is a G card and it won't even support WPA2 cause it was pretty new when the G standard came mainstream. I'm stuck having to run WPA security at home BECAUSE of my iBooks limitations. Not only that, but within WPA security you have AES or TKIP as encryption options, and it doesn't support AES. So because of my iBook, I'm running WPA instead of WPA2, and using TKIP instead of AES encryption. But hey - at least I'm not on WEP. :lolflag:

---

### Post by rearviewmirror on 2009-11-09
> **Roasted said:**
> So, let me get this straight - Your wireless card (internal) is B only, yet it supports WPA2 security in Windows?

Somehow the stars in my head just aren't lining up right hearing that. B is pretty darn old... much older than WPA2 I would think. The wifi card in my iBook is a G card and it won't even support WPA2 cause it was pretty new when the G standard came mainstream. I'm stuck having to run WPA security at home BECAUSE of my iBooks limitations. Not only that, but within WPA security you have AES or TKIP as encryption options, and it doesn't support AES. So because of my iBook, I'm running WPA instead of WPA2, and using TKIP instead of AES encryption. But hey - at least I'm not on WEP. :lolflag:

Thanks for the heads up on 802.11b and WPA.  Being an Orinoco card I figured there might be a driver to allow B to work with WPA.  I really don't want to switch back to WEP, not that I live in an area that is at risk for WEP cracking, I still don't want to change.  Is there a way to get it work with this card?

---

### Post by Roasted on 2009-11-09
> **rearviewmirror said:**
> Thanks for the heads up on 802.11b and WPA.  Being an Orinoco card I figured there might be a driver to allow B to work with WPA.  I really don't want to switch back to WEP, not that I live in an area that is at risk for WEP cracking, I still don't want to change.  Is there a way to get it work with this card?

I'm not saying that as a fact. I just find it hard to believe a wireless B card would support WPA2. WPA2 is pretty darn new, and wireless B is pretty darn old, much like WEP from what I understand. 

Adjust your network security to WPA (different from WPA2) and see if you can connect. Also play around with the different ciphers (AES, TKIP, etc) to see if you get different results. As I said, my iBook only supports WPA if I use the TKIP cipher. Perhaps you'd be some sort of results like that as well.

---

