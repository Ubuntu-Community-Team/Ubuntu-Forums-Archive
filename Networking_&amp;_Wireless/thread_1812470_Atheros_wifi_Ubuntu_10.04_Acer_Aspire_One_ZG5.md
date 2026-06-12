---
title: "Atheros wifi Ubuntu 10.04 Acer Aspire One ZG5"
date: 2011-07-26
forum: Networking &amp; Wireless
---

### Post by PaulG9LXY on 2011-07-26
Hi,
Due to issues with the original OS I've today installed ubuntu 10.04 onto my Aspire one ZG5 and having issues getting the wifi working.

I'm a relative noob to ubuntu, so please be gentle with me! Following the How To Post a Wireless Issue post, please find all the output required:

lspci:

```
03:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
```lsusb:

```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 064e:d101 Suyin Corp. Acer CrystalEye Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

ifconfig:

```
eth0      Link encap:Ethernet  HWaddr 00:1e:68:9c:bd:d1  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:fe9c:bdd1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19473 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11073 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:28057911 (28.0 MB)  TX bytes:1111935 (1.1 MB)
          Interrupt:28 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:76 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5840 (5.8 KB)  TX bytes:5840 (5.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:22:68:ac:aa:3b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```


iwconfig:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```


lsmod:

```
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
joydev                  8740  0 
snd_hda_codec_realtek   203376  1 
arc4                    1153  2 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ath5k                 121632  0 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i915                  288611  3 
mac80211              205402  1 ath5k
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
acerhdf                 6691  0 
ath                     7611  1 ath5k
drm_kms_helper         29329  1 i915
uvcvideo               57374  0 
cfg80211              126144  3 ath5k,mac80211,ath
soundcore               6620  1 snd
drm                   162377  4 i915,drm_kms_helper
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
psmouse                63677  0 
serio_raw               3978  0 
led_class               2864  1 ath5k
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
intel_agp              24375  2 i915
i2c_algo_bit            5028  1 i915
agpgart                31724  2 drm,intel_agp
video                  17375  1 i915
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
r8169                  34140  0 
mii                     4381  1 r8169
```



dmesg | grep ath: 

```
[   17.118668] ath5k 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   17.118702] ath5k 0000:03:00.0: setting latency timer to 64
[   17.118779] ath5k 0000:03:00.0: registered as 'phy0'
[   17.972339] ath: EEPROM regdomain: 0x65
[   17.972348] ath: EEPROM indicates we should expect a direct regpair map
[   17.972359] ath: Country alpha2 being used: 00
[   17.972365] ath: Regpair used: 0x65
[   18.398408] Registered led device: ath5k-phy0::rx
[   18.398488] Registered led device: ath5k-phy0::tx
[   18.398499] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
```

Although there was an entry of:
```
[   16.704646] acer-wmi: Blacklisted hardware detected - not loading
```


sudo lshw -C network
```

  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:68:9c:bd:d1
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.3 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:28 ioport:3000(size=256) memory:31010000-31010fff(prefetchable) memory:31000000-3100ffff(prefetchable) memory:31020000-3103ffff(prefetchable)
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:22:68:ac:aa:3b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:35200000-3520ffff
```


iwlist scan | grep wlan0: 

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results
```



lsb_release -d:

```
Description:    Ubuntu 10.04.3 LTS
```



uname -mr:

```
2.6.32-33-generic i686
```



sudo /etc/init.d/networking restart
 ```
* Reconfiguring network interfaces...                                         
 Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]
```



rfkill list: 

```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

Problem I have is with the wireless not picking up any networks (even though there are about 8 or 9 that I can pick up on my Vista laptop.

Is there anything obvious from all of the info above why this would be like this?

Enable wireless is ticked, Wireless networks show as Disconnected.

Many thanks

Paul

---

### Post by PaulG9LXY on 2011-07-26
Actually, after a reboot, rfkill list now shows:

```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```

and Wireless Networks are now showing as disabled? I haven't touched the wireless on/off button on the front of the netbook though?

Any help would be hugely appreciated as I'm stumped!

Cheers

Paul

---

### Post by lisdavid89 on 2011-07-26
You need to compile and install the madwifi module to get wifi working.

First download the source codes for madwifi. Using terminal:
```
svn checkout http://madwifi-project.org/svn/madwifi/trunk madwifi
```Then change into that directory:
```
cd madwifi
```Then make the files:
```
make
```Then install the module files (you'll need to enter your password when prompted to continue):
```
sudo make install
```Then load the module:
```
sudo modprobe ath_pci
```Then to set the module to load every time you start up, I would do:
```
sudo gedit /etc/modules
```And in the editor that pops up, add "**ath_pci**" (without the quotation marks) to the list of modules to load on start up and save and close (don't delete any of the other modules in that list if there is any). That should be it! Good luck and I hope this works for you!

---

