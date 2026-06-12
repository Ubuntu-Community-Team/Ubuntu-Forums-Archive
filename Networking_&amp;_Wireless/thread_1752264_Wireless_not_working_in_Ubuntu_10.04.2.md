---
title: "Wireless not working in Ubuntu 10.04.2"
date: 2011-05-07
forum: Networking &amp; Wireless
---

### Post by Maddoktor2 on 2011-05-07
I just upgraded to Ubuntu 10.4.2. The wireless worked perfectly in 9.04, but did not not work at all in 9.10, and now 10.4.2.
I'm running a Planex USB wireless dongle on an ancient ShuttleXPC SN41G (circa 2003) - the wireless dongle is an XLink Kai GW-USMini2N.
Any help fixing this issue would be greatly appreciated. I'm connected right now on the Shuttle via Ethernet cable, but would really like to get the wireless up and running again.
Here's all the info I could get as per the pinned topic instructions:
```
maddoktor2@ShuttleX:~$ lspci
00:00.0 Host bridge: nVidia Corporation nForce2 IGP2 (rev a2)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev a2)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev a2)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev a2)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev a2)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev a2)
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3)
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3)
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
00:05.0 Multimedia audio controller: nVidia Corporation nForce Audio Processing Unit (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
00:0d.0 FireWire (IEEE 1394): nVidia Corporation nForce2 FireWire (IEEE 1394) Controller (rev a3)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev a2)
01:06.0 Communication controller: Conexant Systems, Inc. HSF 56k HSFi Modem (rev 01)
02:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX - nForce GPU] (rev a3)

``````
maddoktor2@ShuttleX:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 002 Device 003: ID 05ac:0204 Apple, Inc. 
Bus 002 Device 002: ID 05ac:1002 Apple, Inc. Extended Keyboard Hub [Mitsumi]
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 2019:ab25 PLANEX 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

``````
maddoktor2@ShuttleX:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:30:1b:af:4c:0b  
          inet addr:192.168.1.18  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::230:1bff:feaf:4c0b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6556 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2356 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1931458 (1.9 MB)  TX bytes:332946 (332.9 KB)
          Interrupt:22 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:120 errors:0 dropped:0 overruns:0 frame:0
          TX packets:120 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9716 (9.7 KB)  TX bytes:9716 (9.7 KB)

wlan3     Link encap:Ethernet  HWaddr 00:90:cc:b4:c5:91  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
``````
maddoktor2@ShuttleX:~$ iwconfig wlan3
wlan3     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=9 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

``````
maddoktor2@ShuttleX:~$ dmesg | grep wlan3
[ 3049.436987] udev: renamed network interface wlan0 to wlan3
[ 3052.935262] ADDRCONF(NETDEV_UP): wlan3: link is not ready

``````
maddoktor2@ShuttleX:~$ sudo lshw -C network
[sudo] password for maddoktor2: 
  *-network               
       description: Ethernet interface
       product: nForce2 Ethernet Controller
       vendor: nVidia Corporation
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: a1
       serial: 00:30:1b:af:4c:0b
       size: 100MB/smaddoktor2@ShuttleX:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.1.18 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
       resources: irq:22 memory:ef087000-ef087fff ioport:d000(size=8)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan3
       serial: 00:90:cc:b4:c5:91
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bgn
``````
maddoktor2@ShuttleX:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan3     No scan results
``````
maddoktor2@ShuttleX:~$ lsb_release -d
Description:    Ubuntu 10.04.2 LTS

``````
maddoktor2@ShuttleX:~$ uname -mr
2.6.32-31-generic i686

``````
maddoktor2@ShuttleX:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]
```That's it - any ideas?

---

### Post by Maddoktor2 on 2011-05-07
I hate to be a bumper, but I really need some help with this. ](*,)

---

### Post by josephmills on 2011-05-07
hi there could we see a ```
lsmod 
```thanks

---

### Post by Maddoktor2 on 2011-05-07
Sure thing - here you go:
```
maddoktor2@ShuttleX:~$ lsmod
Module                  Size  Used by
rt2870sta             461811  0 
arc4                    1153  2 
rt2800usb              31531  0 
rt2x00usb               9703  1 rt2800usb
rt2x00lib              27509  2 rt2800usb,rt2x00usb
led_class               2864  1 rt2x00lib
mac80211              205402  2 rt2x00usb,rt2x00lib
cfg80211              126528  2 rt2x00lib,mac80211
crc_ccitt               1339  1 rt2800usb
binfmt_misc             6587  1 
nfsd                  238807  11 
lockd                  64849  1 nfsd
nfs_acl                 2245  1 nfsd
auth_rpcgss            33767  1 nfsd
sunrpc                193117  10 nfsd,lockd,nfs_acl,auth_rpcgss
exportfs                3437  1 nfsd
snd_intel8x0           25652  2 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd                    54180  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ppdev                   5259  0 
nvidia               4701243  32 
vga16fb                11385  1 
vgastate                8961  1 vga16fb
soundcore               6620  1 snd
nvidia_agp              4483  1 
serio_raw               3978  0 
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
shpchp                 28835  0 
i2c_nforce2             5199  0 
agpgart                31724  2 nvidia,nvidia_agp
parport_pc             25962  1 
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
ohci1394               26950  0 
usbhid                 36110  0 
hid                    67096  1 usbhid
ieee1394               81181  1 ohci1394
forcedeth              49556  0 
pata_amd                8766  2 
floppy                 53016  0 

```
Thanks very much for the reply. :)

---

### Post by josephmills on 2011-05-07
how about a ```
dmesg | grep rt
```if nothing shows up fine just tell us thanks could we also see a ```
rfkill list all
``` Do you a connection to the internet now  (cable)?

---

### Post by Maddoktor2 on 2011-05-07
Here's both:
```
led for offset 0x101c with error -110.
[ 5510.690798] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110.
[ 5513.188291] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 5515.688189] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110.
[ 5518.188204] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 5520.688197] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x132c with error -110.
[ 5523.188215] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x132c with error -110.
[ 5525.688236] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x1328 with error -110.
[ 5528.188116] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110.
[ 5530.688134] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 5533.188149] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110.
[ 5535.688155] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110.
[ 5538.188171] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 5540.688172] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110.
[ 5543.188196] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 5545.688199] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110.
[ 5548.188220] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110.
[ 5550.688229] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 5553.196250] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110.
[ 5555.696248] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 5558.196138] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x1004 with error -110.
[ 5560.696535] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x1004 with error -110.
[ 5563.196164] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110.
[ 5565.696680] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 5568.320188] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x1004 with error -110.
[ 5570.820199] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x1004 with error -110.
[ 5573.320207] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0500 with error -110.
[ 5575.820219] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0500 with error -110.
[ 5578.320235] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0500 with error -110.
[ 5580.820118] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0500 with error -110.
[ 5583.320138] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0500 with error -110.
[ 5585.820147] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 5588.320152] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0500 with error -110.
[ 5590.820173] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0500 with error -110.
[ 5593.320183] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0500 with error -110.
[ 5595.820189] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0500 with error -110.
[ 5598.320206] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 5600.820477] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0500 with error -110.
[ 5603.320312] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0500 with error -110.
[ 5605.820112] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0500 with error -110.
[ 5608.320383] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0500 with error -110.
[ 5610.820136] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 5613.320153] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0500 with error -110.
[ 5615.820167] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0500 with error -110.
[ 5618.320178] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0500 with error -110.
[ 5620.820193] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0500 with error -110.
[ 5623.321285] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0500 with error -110.
[ 5625.820222] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0500 with error -110.
[ 5628.320220] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 5630.820107] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0500 with error -110.
[ 5633.320127] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0500 with error -110.
[ 5635.820138] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0500 with error -110.
[ 5638.320152] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110.
[ 5640.820165] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 5643.320173] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110.
[ 5645.820183] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 5648.320196] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110.
[ 5650.820209] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 5653.320225] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110.
[ 5655.820242] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 5658.320127] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110.
[ 5660.820138] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 5663.320146] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110.
[ 5665.820160] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 5668.320177] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x132c with error -110.
[ 5670.820185] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x132c with error -110.
[ 5673.320200] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x1328 with error -110.
[ 5675.820212] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110.
[ 5678.320220] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 5680.820236] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110.
[ 5683.320119] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110.
[ 5685.820135] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 5688.320277] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110.
[ 5690.820153] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 5693.320175] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110.
[ 5695.824181] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110.
[ 5698.324323] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 5700.832201] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110.
[ 5703.332204] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 5705.832101] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x1004 with error -110.
[ 5708.332111] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x1004 with error -110.
[ 5710.832378] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110.
[ 5713.332270] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 5715.932142] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x1004 with error -110.
[ 5718.432155] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x1004 with error -110.
[ 5720.932165] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0500 with error -110.
[ 5723.432177] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0500 with error -110.
[ 5725.932182] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0500 with error -110.
[ 5728.432208] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0500 with error -110.
[ 5730.932213] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0500 with error -110.
[ 5733.432103] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 5735.932106] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0500 with error -110.
[ 5738.432120] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0500 with error -110.
[ 5740.932134] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0500 with error -110.
[ 5743.432153] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0500 with error -110.
[ 5745.932164] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 5748.432176] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0500 with error -110.
[ 5750.932180] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0500 with error -110.
[ 5753.432201] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0500 with error -110.
[ 5755.932214] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0500 with error -110.
[ 5758.432378] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 5760.932110] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0500 with error -110.
[ 5763.432125] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0500 with error -110.
[ 5765.932138] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0500 with error -110.
[ 5768.432144] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0500 with error -110.
[ 5770.932164] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0500 with error -110.
[ 5773.432172] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0500 with error -110.
[ 5775.932316] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 5778.432190] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0500 with error -110.
[ 5780.932202] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0500 with error -110.
[ 5783.432217] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0500 with error -110.
[ 5785.932109] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110.
[ 5788.432118] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 5790.932127] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110.
[ 5793.432146] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 5795.932156] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110.
[ 5798.432165] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 5800.932183] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110.
[ 5803.432196] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 5805.932199] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110.
[ 5808.432219] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 5810.932108] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110.
[ 5813.432110] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 5815.932130] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x132c with error -110.
[ 5818.432143] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x132c with error -110.
[ 5820.932162] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x1328 with error -110.
[ 5823.432173] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110.
[ 5825.932180] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 5828.432721] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110.
[ 5830.932206] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110.
[ 5833.432206] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 5835.932099] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110.
[ 5838.432116] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 5840.932129] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110.
[ 5843.432132] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110.
[ 5845.932154] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 5848.440170] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110.
[ 5850.940182] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 5853.440192] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x1004 with error -110.
[ 5855.940207] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x1004 with error -110.
[ 5858.440228] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110.
[ 5860.940236] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 5863.496242] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x1004 with error -110.
[ 5865.996693] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x1004 with error -110.
[ 5868.496131] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0500 with error -110.
[ 5870.996139] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0500 with error -110.
[ 5873.496161] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0500 with error -110.
[ 5875.996173] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0500 with error -110.
[ 5878.496188] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0500 with error -110.
[ 5880.996186] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 5883.496216] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0500 with error -110.
[ 5885.996223] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0500 with error -110.
[ 5888.496109] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0500 with error -110.
[ 5890.996125] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0500 with error -110.
[ 5893.496135] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 5895.996146] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0500 with error -110.
[ 5898.496161] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0500 with error -110.
[ 5900.996171] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0500 with error -110.
[ 5903.496189] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0500 with error -110.
[ 5905.996191] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 5908.496208] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0500 with error -110.
[ 5910.996217] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0500 with error -110.
[ 5913.496102] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0500 with error -110.
[ 5915.996122] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0500 with error -110.
[ 5918.496134] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0500 with error -110.
[ 5920.996146] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0500 with error -110.
[ 5923.496163] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 5925.996165] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0500 with error -110.
[ 5928.496180] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0500 with error -110.
[ 5930.996185] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0500 with error -110.
[ 5933.496207] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110.
[ 5935.996217] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 5938.496105] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110.
[ 5940.996113] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 5943.496132] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110.
[ 5945.996128] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 5948.496364] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110.
[ 5950.996164] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 5953.496179] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110.
[ 5955.996186] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 5958.496203] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110.
[ 5960.996216] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 5963.496233] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x132c with error -110.
[ 5965.996114] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x132c with error -110.
[ 5968.496124] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x1328 with error -110.
[ 5970.996139] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110.
[ 5973.497152] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 5975.996163] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110.
[ 5978.496178] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110.
[ 5980.996189] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 5983.496201] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110.
[ 5985.996459] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 5988.496936] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110.
[ 5990.996248] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110.
[ 5993.496758] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 5996.004370] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110.
[ 5998.505407] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 6001.005110] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x1004 with error -110.
[ 6003.504172] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x1004 with error -110.
[ 6006.004191] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110.
[ 6008.504571] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 6011.060213] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x1004 with error -110.
[ 6013.560323] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x1004 with error -110.
[ 6016.060255] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0500 with error -110.
[ 6018.560123] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0500 with error -110.
[ 6021.060134] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0500 with error -110.
[ 6023.561772] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0500 with error -110.
[ 6026.060160] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0500 with error -110.
[ 6028.561686] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 6031.061444] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0500 with error -110.
[ 6033.560942] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0500 with error -110.
[ 6036.061600] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0500 with error -110.
[ 6038.560267] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0500 with error -110.
[ 6041.060103] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 6043.560989] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0500 with error -110.
[ 6046.060581] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0500 with error -110.
[ 6048.560141] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0500 with error -110.
[ 6051.060348] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0500 with error -110.
[ 6053.560166] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 6056.060180] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0500 with error -110.
[ 6058.560190] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0500 with error -110.
[ 6061.060325] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0500 with error -110.
[ 6063.560218] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0500 with error -110.
[ 6066.060231] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0500 with error -110.
[ 6068.560117] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0500 with error -110.
[ 6071.060388] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 6073.561393] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0500 with error -110.
[ 6076.060153] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0500 with error -110.
[ 6078.560164] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0500 with error -110.
[ 6081.060171] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110.
[ 6083.561462] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 6086.060872] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110.
[ 6088.560212] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 6091.060229] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110.
[ 6093.560237] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 6096.060126] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110.
[ 6098.560271] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 6101.060920] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110.
[ 6103.560159] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 6106.060171] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110.
[ 6108.560183] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 6111.060189] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x132c with error -110.
[ 6113.560213] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x132c with error -110.
[ 6116.060226] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x1328 with error -110.
[ 6118.560239] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110.
[ 6121.060126] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 6123.560138] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110.
[ 6126.060143] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110.
[ 6128.560161] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 6131.060172] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110.
[ 6133.560203] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110.
[ 6136.060194] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110.
[ 6138.382215] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -71.
[ 6138.420027] phy0 -> rt2800usb_wait_wpdma_ready: Error - WPDMA TX/RX busy, aborting.
[10442.445424] Registered led device: rt2800usb-phy1::radio
[10442.445590] Registered led device: rt2800usb-phy1::assoc
[10442.445744] Registered led device: rt2800usb-phy1::quality
[10442.577577] rt2800usb 1-6:1.0: firmware: requesting rt2870.bin

```
```
maddoktor2@ShuttleX:~$ rfkill list all
1: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```
Yes, I am connected via Ethernet cable.

---

### Post by Maddoktor2 on 2011-05-07
I have to hit the sack, so I'll check back on this topic in the morning for further instructions - thanks again for the replies. :)

---

### Post by josephmills on 2011-05-08
```
modinfo rt2870sta | grep -i ab25 
```anything come up ?

---

### Post by Maddoktor2 on 2011-05-08
Yes - it returned this:
```
maddoktor2@ShuttleX:~$ modinfo rt2870sta | grep -i ab25
alias:          usb:v2019pAB25d*dc*dsc*dp*ic*isc*ip*

```

---

### Post by Maddoktor2 on 2011-05-08
Another quick question - should I try upgrading to 10.10, or get this issue sorted first and hope that the fix carries over when I do? If it doesn't, I'm only going to have to start over with this again, since I do plan on upgrading as soon as I can.
Thanks again for taking the time to help. :)

---

### Post by josephmills on 2011-05-08
> **Maddoktor2 said:**
> Another quick question - should I try upgrading to 10.10, or get this issue sorted first and hope that the fix carries over when I do? If it doesn't, I'm only going to have to start over with this again, since I do plan on upgrading as soon as I can.
Thanks again for taking the time to help. :)

you should distro-upgrade right now if you are going to do it. dont know if it will work out the kinks I think that you just need to black list a couple of mods and modprobe the sta mod and it might work but if you are going to up grade do it now please so we dont have to do this again.

---

### Post by Maddoktor2 on 2011-05-08
Sounds good - I'm beginning the upgrade now, and will post back when it's completed.
Thanks for the sound advice. :)

---

### Post by Maddoktor2 on 2011-05-08
Update: Since the option was presented at reboot into Maverick (10.10), I decided to bump it all the way up to Natty (11.04) - the upgrade is proceeding now. I will post back when the upgrade and any associated updates are completed.
Thanks again. :)

---

### Post by Maddoktor2 on 2011-05-08
Well, disaster struck - this old Shuttle's graphics card just can't handle 11.04, so I was forced to start from scratch and reformat it to roll it back to 9.04. I'm currently updating it so I can obtain the driver needed to get it out of 800x600 mode, and the wireless is performing just flawlessly. Go figure...#-o

---

