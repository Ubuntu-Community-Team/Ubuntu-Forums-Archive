---
title: "Atheros 9462 in Ubuntu 12.04 very frequent wireless network drops"
date: 2013-03-11
forum: Networking &amp; Wireless
---

### Post by kevincs on 2013-03-11
The network on my (Acer Aspire V5-571-6869) laptop drops out very frequently, from between 20 seconds to 20 minutes.  It will come back on it's own after, say, a few long minutes.  Disconnecting to the wireless network and then manually reconnecting solves the problem.

The card is an Atheros 9462, and I'm running Ubuntu 12.04.  Below is some system info, and some fixes I've already tried.

HERE IS SOME OUTPUT:

uname -pr
```

3.2.0-38-generic x86_64

```

(dropped) ifconfig
```

eth0      Link encap:Ethernet  HWaddr 20:6a:8a:88:24:5b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:44 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1402 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1402 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:153992 (153.9 KB)  TX bytes:153992 (153.9 KB)

wlan0     Link encap:Ethernet  HWaddr 44:6d:57:fc:4c:dc  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::466d:57ff:fefc:4cdc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28154 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19576 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:35699855 (35.6 MB)  TX bytes:2176601 (2.1 MB)

```

(dropped) iwconfig
```

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"VIDEOTRON8492"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 84:C9:B2:D3:09:12   
          Bit Rate=130 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=65/70  Signal level=-45 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:13  Invalid misc:190   Missed beacon:0

eth0      no wireless extensions.

```

(working) ifconfig
```

eth0      Link encap:Ethernet  HWaddr 20:6a:8a:88:24:5b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:44 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:417 errors:0 dropped:0 overruns:0 frame:0
          TX packets:417 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:43525 (43.5 KB)  TX bytes:43525 (43.5 KB)

wlan0     Link encap:Ethernet  HWaddr 44:6d:57:fc:4c:dc  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::466d:57ff:fefc:4cdc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4887 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4289 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6098467 (6.0 MB)  TX bytes:510446 (510.4 KB)

```

(working) iwconfig
```

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"VIDEOTRON8492"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 84:C9:B2:D3:09:12   
          Bit Rate=130 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=68/70  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

```

diff on the (working) and (dropped) above
```

15,16c15,16
<           RX packets:1402 errors:0 dropped:0 overruns:0 frame:0
<           TX packets:1402 errors:0 dropped:0 overruns:0 carrier:0
---
>           RX packets:417 errors:0 dropped:0 overruns:0 frame:0
>           TX packets:417 errors:0 dropped:0 overruns:0 carrier:0
18c18
<           RX bytes:153992 (153.9 KB)  TX bytes:153992 (153.9 KB)
---
>           RX bytes:43525 (43.5 KB)  TX bytes:43525 (43.5 KB)
24,25c24,25
<           RX packets:28154 errors:0 dropped:0 overruns:0 frame:0
<           TX packets:19576 errors:0 dropped:0 overruns:0 carrier:0
---
>           RX packets:4887 errors:0 dropped:0 overruns:0 frame:0
>           TX packets:4289 errors:0 dropped:0 overruns:0 carrier:0
27c27,28
<           RX bytes:35699855 (35.6 MB)  TX bytes:2176601 (2.1 MB)
---
>           RX bytes:6098467 (6.0 MB)  TX bytes:510446 (510.4 KB)
> 
39c40
<           Link Quality=65/70  Signal level=-45 dBm  
---
>           Link Quality=68/70  Signal level=-42 dBm  
41c42
<           Tx excessive retries:13  Invalid misc:190   Missed beacon:0
---
>           Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

lspci -v
```

02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5289 (rev 01)
    Subsystem: Acer Incorporated [ALI] Device 0724
    Flags: bus master, fast devsel, latency 0, IRQ 7
    Memory at f0600000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>

02:00.2 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 0a)
    Subsystem: Acer Incorporated [ALI] Device 0724
    Flags: bus master, fast devsel, latency 0, IRQ 44
    I/O ports at 2000 [size=256]
    Memory at f0404000 (64-bit, prefetchable) [size=4K]
    Memory at f0400000 (64-bit, prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

03:00.0 Network controller: Atheros Communications Inc. AR9462 Wireless Network Adapter (rev 01)
    Subsystem: Lite-On Communications Inc Device 6621
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at f0500000 (64-bit, non-prefetchable) [size=512K]
    Expansion ROM at dfa00000 [disabled] [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath9k
    Kernel modules: ath9k

```


lsmod | grep ath
```

ath9k                 132428  0 
mac80211              506862  1 ath9k
ath9k_common           14053  1 ath9k
ath9k_hw              411239  2 ath9k,ath9k_common
ath                    24067  3 ath9k,ath9k_common,ath9k_hw
cfg80211              205774  3 ath9k,mac80211,ath

```


lsmod
```

Module                  Size  Used by
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   224173  1 
parport_pc             32866  0 
ppdev                  17113  0 
rfcomm                 47604  12 
bnep                   18281  2 
joydev                 17693  0 
acer_wmi               28418  0 
sparse_keymap          13890  1 acer_wmi
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
snd_pcm                97275  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
psmouse                97485  0 
arc4                   12529  2 
wmi                    19256  1 acer_wmi
serio_raw              13211  0 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
ath9k                 132428  0 
snd                    79041  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              506862  1 ath9k
ath9k_common           14053  1 ath9k
ath9k_hw              411239  2 ath9k,ath9k_common
ath                    24067  3 ath9k,ath9k_common,ath9k_hw
uvcvideo               72627  0 
i915                  477611  3 
videodev               98259  1 uvcvideo
cfg80211              205774  3 ath9k,mac80211,ath
mac_hid                13253  0 
v4l2_compat_ioctl32    17128  1 videodev
btusb                  18332  2 
drm_kms_helper         46978  1 i915
bluetooth             180153  23 rfcomm,bnep,btusb
drm                   241971  4 i915,drm_kms_helper
mei                    41616  0 
i2c_algo_bit           13423  1 i915
video                  19651  1 i915
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47238  0 
hid                    99636  1 usbhid
r8169                  62154  0 

```

lshw -class network
```

  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.2
       bus info: pci@0000:02:00.2
       logical name: eth0
       version: 0a
       serial: 20:6a:8a:88:24:5b
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=N/A latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:44 ioport:2000(size=256) memory:f0404000-f0404fff memory:f0400000-f0403fff
  *-network
       description: Wireless interface
       product: AR9462 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 44:6d:57:fc:4c:dc
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-38-generic firmware=N/A ip=192.168.0.102 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:19 memory:f0500000-f057ffff memory:dfa00000-dfa0ffff

```


AND HERE ARE SOME FIXES I'VE TRIED

nohwcrypt (all the below fixes done in conjunction with this, also)
```

I created the file

   /etc/modprobe.d/ath9k.conf

which contains only the line

   options ath9k nohwcrypt=1

```

disable ipv6
```

I appended the file

   /etc/sysctl.conf

to include the lines

   net.ipv6.conf.all.disable_ipv6 = 1
   net.ipv6.conf.default.disable_ipv6 = 1
   net.ipv6.conf.lo.disable_ipv6 = 1

```

disable 11n in iwlagn
```

I created the file

   /etc/modprobe.d/iwlagn-disable11n.conf

which contains only the line

   options iwlagn 11n_disable=1

(though of course, I don't even see this mod running)

```

blacklist the acer_wmi mod
```

I appended the file

   /etc/modprobe.d/blacklist.conf

to contain the line

   blacklist acer_wmi

```

turn off power management
```

I ran the command

  iwconfig wlan0 power off

```


This has been driving me nuts, and preventing me from working, for five months.  Please let me know what more I can provide, or anything else to try.  Thank you.

---

### Post by praseodym on 2013-03-11
Disable the hardware encryption and the power management of this card:
```

echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
sudo iwconfig wlan0 power off
```

---

### Post by kevincs on 2013-03-11
> **praseodym said:**
> Disable the hardware encryption and the power management of this card:
```

echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
sudo iwconfig wlan0 power off
```

Thanks, but I've already tried both of those.  I know the hwcrypt seems to work for everyone else (for years now), but doesn't seem to fix me.

---

### Post by kevincs on 2013-03-12
> **praseodym said:**
> Disable the hardware encryption and the power management of this card:
```

echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
sudo iwconfig wlan0 power off
```

Well, I get to go ahead and cancel my last post; everything seems to be working fine, and it feels so good.

Though I originally had the .conf file created, I had assumed that a reboot would do the equivalent of your modprobe commands, which I must conclude did not.  So only running the middle two commands must be what fixed me.

So thank you again.... and where is the [SOLVED]?  Can't edit, not a thread tool?

---

