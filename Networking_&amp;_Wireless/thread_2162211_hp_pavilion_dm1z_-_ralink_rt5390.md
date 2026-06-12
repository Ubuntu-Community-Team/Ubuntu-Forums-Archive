---
title: "hp pavilion dm1z - ralink rt5390"
date: 2013-07-13
forum: Networking &amp; Wireless
---

### Post by banana jack on 2013-07-13
Network controller: Ralink corp. RT5390 [802.11 b/g/n 1T1R G-band PCI Express Single Chip]

wlan0     IEEE 802.11bgn  ESSID:"OurHouse5"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: F8:8F:CA:04:E2:E8   
          Bit Rate=26 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=61/70  Signal level=-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:465  Invalid misc:109   Missed beacon:0

Fresh install of Xubuntu 13.04, wireless has worked intermittently before, but no longer. When I try to connect, it'll ask for my password, I'll type it in and click ok, it'll think for a bit, then ask me for my password again. I tried to set up wicd to use instead, but it couldn't connect to the d-bus interface. and /etc/wicd/ doesn't contain any .conf files except the default template(I was trying to see if it had added an extra user [])
Currently, for some reason, i'm on ethernet and i can click "connect" and it will connect, but when i then unplug from ethernet, it continues to say "connected"(to wifi) but won't load any pages.
I'm pretty new to ubuntu still, so go easy.

$ sudo lshw -C network
[sudo] password for samuel: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168 PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 06
       serial: 2c:27:d7:aa:1e:0a
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-2.fw ip=192.168.1.6 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:40 ioport:2000(size=256) memory:d0004000-d0004fff memory:d0000000-d0003fff
  *-network
       description: Wireless interface
       product: RT5390 [802.11 b/g/n 1T1R G-band PCI Express Single Chip]
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: c0:f8:da:99:77:fe
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.8.0-26-generic firmware=0.34 ip=192.168.1.8 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:d0100000-d010ffff

$ uname -mr
3.8.0-26-generic x86_64

(i couldn't pull any more seemingly useful information from the commands listed in the howto post)

Ralink's not listed in the recommended wireless manufacturers, am I even going to be able to make this work?

---

### Post by praseodym on 2013-07-14
Check the following outputs:
```

ifconfig -a
cat /etc/resolv.conf
route -n
rfkill list
lsmod
dmesg | grep rt2
sudo iwlist scan
```

---

### Post by banana jack on 2013-07-14
> **praseodym said:**
> Check the following outputs:
```

ifconfig -a
cat /etc/resolv.conf
route -n
rfkill list
lsmod
dmesg | grep rt2
sudo iwlist scan
```

$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 2c:27:d7:aa:1e:0a  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2605:a601:422:a001:2e27:d7ff:feaa:1e0a/64 Scope:Global
          inet6 addr: fd5d:4ffd:7d1b:1:2e27:d7ff:feaa:1e0a/64 Scope:Global
          inet6 addr: fe80::2e27:d7ff:feaa:1e0a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1205741 errors:0 dropped:0 overruns:0 frame:0
          TX packets:198325 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1668760327 (1.6 GB)  TX bytes:26637437 (26.6 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:23235 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23235 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2426177 (2.4 MB)  TX bytes:2426177 (2.4 MB)

wlan0     Link encap:Ethernet  HWaddr c0:f8:da:99:77:fe  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search home

$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

$ rfkill list
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

$ lsmod
Module                  Size  Used by
nls_iso8859_1          12713  0 
bnep                   18036  2 
rfcomm                 42641  4 
bluetooth             228619  10 bnep,rfcomm
parport_pc             28152  0 
ppdev                  17073  0 
binfmt_misc            17500  1 
snd_hda_codec_idt      70256  1 
snd_hda_codec_hdmi     36913  1 
snd_hda_intel          39619  7 
snd_hda_codec         136453  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
joydev                 17377  0 
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
arc4                   12615  2 
radeon                942029  3 
rt2800pci              18582  0 
rt2800lib              66507  1 rt2800pci
uvcvideo               80847  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
videobuf2_vmalloc      13056  1 uvcvideo
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
rt2x00pci              14519  1 rt2800pci
rt2x00lib              54869  3 rt2x00pci,rt2800lib,rt2800pci
ttm                    83187  1 radeon
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
mac80211              606457  3 rt2x00lib,rt2x00pci,rt2800lib
lp                     17759  0 
videobuf2_memops       13202  1 videobuf2_vmalloc
videobuf2_core         40513  1 uvcvideo
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
drm_kms_helper         49394  1 radeon
drm                   286028  5 ttm,drm_kms_helper,radeon
cfg80211              510937  2 mac80211,rt2x00lib
psmouse                95870  0 
snd                    68876  23 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
kvm                   443165  0 
parport                46345  3 lp,ppdev,parport_pc
videodev              129260  2 uvcvideo,videobuf2_core
eeprom_93cx6           13344  1 rt2800pci
crc_ccitt              12707  1 rt2800lib
hp_wmi                 18048  0 
sparse_keymap          13890  1 hp_wmi
hp_accel               26012  0 
wmi                    19070  1 hp_wmi
lis3lv02d              20111  1 hp_accel
input_polldev          13896  1 lis3lv02d
sp5100_tco             13735  0 
i2c_algo_bit           13413  1 radeon
video                  19390  0 
i2c_piix4              13266  0 
soundcore              12680  1 snd
serio_raw              13215  0 
k10temp                13126  0 
mac_hid                13205  0 
microcode              22881  0 
ums_realtek            17949  0 
usb_storage            57204  1 ums_realtek
ahci                   25731  2 
libahci                31364  1 ahci
r8169                  67446  0 

dmesg | grep rt2 didn't come up with anything.

iwlist (this is my wireless, i cut out all the other availables. there's a lot.)
wlan0     Scan completed :
          Cell 01 - Address: F8:8F:CA:04:E2:E8
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=70/70  Signal level=-37 dBm  
                    Encryption key:on
                    ESSID:"OurHouse5"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000005dddfe66f7
                    Extra: Last beacon: 48ms ago
                    IE: Unknown: 00094F7572486F75736535
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030109
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A6E1017FFFFFF0000000000000000000000000000001847FF1F00
                    IE: Unknown: 3D1609070400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A00B400C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD1E00904C336E1017FFFFFF0000000000000000000000000000001847FF1F00
                    IE: Unknown: DD1A00904C3409070400000000000000000000000000000000000000
                    IE: Unknown: DD06005043030000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

---

### Post by praseodym on 2013-07-15
Is there a MAC-address filter active in your router? If yes, deactivate it. Channel set to "fixed", bandwidth to 20MHz. Is the router firmware up-to-date?

---

### Post by banana jack on 2013-07-16
> **praseodym said:**
> Is there a MAC-address filter active in your router? If yes, deactivate it. Channel set to "fixed", bandwidth to 20MHz. Is the router firmware up-to-date?

no mac address filter. Router firmware should be fine, we just got google fiber installed a couple weeks ago. Every other OS in the house connects fine...

---

### Post by praseodym on 2013-07-16
Deactivate the power management
```

sudo iwconfig wlan0 power off
```

---

### Post by banana jack on 2013-07-16
> **praseodym said:**
> Deactivate the power management
```

sudo iwconfig wlan0 power off
```

WHAT WIZARDRY IS THIS.
you. you sir. you have made my day. Thank you.
 if i may ask, what exactly did i just do?

---

### Post by praseodym on 2013-07-17
The PM decreases the current to the wifi card automatically if the battery charge is low. With this, the wifi card will consume the full current independently from the battery charge

---

