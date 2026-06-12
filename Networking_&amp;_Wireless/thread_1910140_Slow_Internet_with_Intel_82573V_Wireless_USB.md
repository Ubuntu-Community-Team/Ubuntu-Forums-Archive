---
title: "Slow Internet with Intel 82573V Wireless USB"
date: 2012-01-16
forum: Networking &amp; Wireless
---

### Post by hyngyn on 2012-01-16
Hi,

I installed Ubuntu 11.10 on my desktop recently. I've been lurking this forum trying to find a solution to my slow wireless connection but I haven't been able to fix it. Before, it used to randomly drop my connection until I installed wicd. I'm connected to a Netgear NDR3700 router.

Here are some terminal outputs that maybe helpful. Please let me know if there is anything I can do. Thanks!

lsusb
```
Bus 001 Device 002: ID 0846:6a00 NetGear, Inc. WG111v2 54 Mbps Wireless [RealTek RTL8187L]

```ifconfig -a
```
eth0      Link encap:Ethernet  HWaddr 00:13:20:cb:77:76  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Memory:d0100000-d0120000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:24:b2:3c:78:50  
          inet addr:192.168.1.14  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:b2ff:fe3c:7850/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10953 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7978 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13148115 (13.1 MB)  TX bytes:1619641 (1.6 MB)

```iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"NVC"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: C0:3F:0E:7C:6C:2B   
          Bit Rate=24 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=41/70  Signal level=-69 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1689  Invalid misc:1078   Missed beacon:0

```sudo lshw -C network
```

  *-network               
       description: Ethernet interface
       product: 82573V Gigabit Ethernet Controller (Copper)
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 03
       serial: 00:13:20:cb:77:76
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.3.10-k2 firmware=1.0-1 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:44 memory:d0100000-d011ffff ioport:1000(size=32)
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:2
       logical name: wlan0
       serial: 00:24:b2:3c:78:50
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8187 driverversion=3.0.0-12-generic firmware=N/A ip=192.168.1.14 link=yes multicast=yes wireless=IEEE 802.11bg

```lsmod
```

Module                  Size  Used by
vesafb                 13489  1 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
arc4                   12473  2 
joydev                 17393  0 
snd_hda_codec_hdmi     31426  1 
ppdev                  12849  0 
snd_hda_codec_idt      60049  1 
snd_hda_intel          24262  3 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
rtl8187                56323  0 
mac80211              272785  1 rtl8187
cfg80211              172392  2 rtl8187,mac80211
snd_seq_midi           13132  0 
usbhid                 41905  0 
eeprom_93cx6           12653  1 rtl8187
hid                    77367  1 usbhid
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
psmouse                73673  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
serio_raw              12990  0 
fglrx                2595570  119 
snd_timer              28932  2 snd_pcm,snd_seq
binfmt_misc            17292  1 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
parport_pc             32114  1 
snd                    55902  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
e1000e                139775  0 


```

---

### Post by hyngyn on 2012-01-16
Looks like it's just a bad driver. Going wired instead.

---

