---
title: "WUSB100 connection problems"
date: 2011-01-01
forum: Networking &amp; Wireless
---

### Post by carrottop96 on 2011-01-01
Hello,
I'm having an issue with my WUSB100 wireless card. I can scan and detect networks, yet I can't connect to them. I googled the problem and tried many things to no avail. I'm running Ubuntu 10.04.1 LTS 32-bit, and I believe my card is currently using the ralink rt2870sta driver.

The lsusb command outputs:
```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0781:5530 SanDisk Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[COLOR=Red]Bus 001 Device 002: ID 1737:0070 Linksys [/COLOR]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:c0:f0:3d:9c:ff  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:f0ff:fe3d:9cff/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7896 errors:1 dropped:0 overruns:0 frame:0
          TX packets:7023 errors:5 dropped:0 overruns:1 carrier:4
          collisions:0 txqueuelen:1000 
          RX bytes:7253091 (7.2 MB)  TX bytes:1242597 (1.2 MB)
          Interrupt:3 Base address:0x1c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1e:e5:e5:a3:ca  
          inet6 addr: fe80::21e:e5ff:fee5:a3ca/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:17222 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5480 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2284559 (2.2 MB)  TX bytes:357532 (357.5 KB)


```

iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RTxx70 Wireless  ESSID:""  Nickname:"RT3070STA"
          Mode:Auto  Frequency=2.437 GHz  Access Point: 00:25:3C:40:5A:F1   
          Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:-19 dBm  Noise level:-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

lsmod:
```
Module                  Size  Used by
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8933  1 
fat                    47767  1 vfat
isofs                  29250  1 
udf                    78785  0 
crc_itu_t               1371  1 udf
binfmt_misc             6587  1 
fbcon                  35102  72 
snd_via82xx            20058  2 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
gameport                9089  1 snd_via82xx
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_ac97_codec        100646  1 snd_via82xx
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc          7076  2 snd_via82xx,snd_pcm
snd_mpu401_uart         5617  1 snd_via82xx
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
nouveau               467048  3 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ttm                    49943  1 nouveau
drm_kms_helper         29329  1 nouveau
snd                    54180  15 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   162409  3 nouveau,ttm,drm_kms_helper
ppdev                   5259  0 
i2c_algo_bit            5028  1 nouveau
psmouse                63245  0 
via686a                10986  0 
[COLOR=Red]rt2870sta             461811  1 [/COLOR]
serio_raw               3978  0 
via_agp                 5310  1 
soundcore               6620  1 snd
i2c_viapro              5573  0 
parport_pc             25962  1 
shpchp                 28820  0 
agpgart                31724  3 ttm,drm,via_agp
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
usb_storage            39553  1 
pata_via                7272  3 
tulip                  44008  0 
floppy                 53016  0 

```dmesg | grep "rt2870sta"
```
[   19.403486] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   20.028708] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.

```sudo lshw -C network:
```
  *-network               
       description: Ethernet interface
       product: LNE100TX
       vendor: Lite-On Communications Inc
       physical id: 3
       bus info: pci@0000:00:03.0
       logical name: eth0
       version: 20
       serial: 00:c0:f0:3d:9c:ff
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master rom ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.15 ip=192.168.1.64 latency=66 multicast=yes
       resources: irq:3 ioport:1c00(size=256) memory:44000000-440000ff memory:20000000-2003ffff(prefetchable)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1e:e5:e5:a3:ca
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=RTxx70 Wireless

```iwlist scan:
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:25:3C:40:5A:F1
                    Protocol:802.11b/g
                    ESSID:"2WIRE558"
                    Mode:Managed
                    Channel:6
                    Quality:100/100  Signal level:-38 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:18 Mb/s

```Any help would be appreciated!

---

### Post by PatchesTheCaveman on 2011-01-01
Hi carrottop96.  Happy New Year!

Try running this command and see if it helps your situation:
```
sudo iwconfig wlan0 rate 54M
```

If that doesn't work, plug into a wired Ethernet connection and run these commands to download the latest drivers for your wireless card:
```
sudo apt-get update
sudo apt-get install linux-backports-modules-wireless-lucid-generic
```

---

### Post by carrottop96 on 2011-01-02
It's working perfectly now! Thanks for the easy fix!

---

