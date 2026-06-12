---
title: "Wired network not working"
date: 2010-05-30
forum: Networking &amp; Wireless
---

### Post by ceixeoida on 2010-05-30
Hi!
My wired network is not working!

This is the result of ifconfig -a:
```
eth0      Link encap:Ethernet  HWaddr 00:1c:25:3e:fe:50  
          inet6 addr: fe80::21c:25ff:fe3e:fe50/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1904 (1.9 KB)  TX bytes:1904 (1.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:80:5a:54:41:b5  
          inet addr:192.168.0.105  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::280:5aff:fe54:41b5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:852 errors:0 dropped:0 overruns:0 frame:0
          TX packets:885 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:642473 (642.4 KB)  TX bytes:147722 (147.7 KB)
```

And with netstat -rn
```
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface

```

I checked /etc/network/interfaces:
```
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp
```

And /etc/NetworkManager/nm-system-settings.conf:
```
...
[ifupdown]
managed=true
```

Any idea?

EDIT: Hardware
```
           *-network
                description: Ethernet interface
                product: 88E8056 PCI-E Gigabit Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 20
                serial: 00:1c:25:3e:fe:50
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 duplex=full firmware=N/A latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
                resources: irq:25 memory:fdcfc000-fdcfffff ioport:ee00(size=256) memory:fdf00000-fdf1ffff(prefetchable)
```

---

### Post by Iowan on 2010-05-30
From a terminal, try running **dhclient eth0**. Post results.

---

### Post by ceixeoida on 2010-05-30
Results for dhclient eth0:
```
There is already a pid file /var/run/dhclient.pid with pid 2039
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/00:1c:25:3e:fe:50
Sending on   LPF/eth0/00:1c:25:3e:fe:50
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

---

### Post by Julita on 2010-05-30
Hello! What is the output of
```
ifconfig eth0 up
``` (should be run as a root)

Sometimes you have to disable the wireless for the wired network to work properly. Try that!

Can you please post the output of
```
lsmod
``` It is also possible that you have conflicting drivers. Another issue is that the installed driver is faulty. It was my case with wireless.

---

### Post by ceixeoida on 2010-05-30
I disabled wireless connection before all tests. The command 'sudo ifconfig eth0 up' gives nothing back.
Result for lsmod:
```
Module                  Size  Used by
nls_iso8859_1           4633  0 
nls_cp437               6351  0 
vfat                   10802  0 
fat                    55350  1 vfat
binfmt_misc             7960  1 
arc4                    1473  2 
snd_hda_codec_realtek   278890  1 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12757  0 
vgastate                9857  1 vga16fb
snd_hda_intel          25645  2 
snd_hda_codec          85727  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87850  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23388  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
rt73usb                24256  0 
crc_itu_t               1715  1 rt73usb
rt2x00usb              11260  1 rt73usb
rt2x00lib              32133  2 rt73usb,rt2x00usb
snd_seq                57417  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
radeon                739595  3 
mac80211              238128  2 rt2x00usb,rt2x00lib
snd_timer              23553  2 snd_pcm,snd_seq
snd_seq_device          6824  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ttm                    60815  1 radeon
drm_kms_helper         30742  1 radeon
usb_storage            49833  0 
ppdev                   6375  0 
cfg80211              148386  2 rt2x00lib,mac80211
led_class               3732  1 rt2x00lib
snd                    70978  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   198770  5 radeon,ttm,drm_kms_helper
i2c_algo_bit            6024  1 radeon
psmouse                64608  0 
serio_raw               4918  0 
parport_pc             29958  1 
edac_core              45423  0 
edac_mce_amd            9214  0 
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
i2c_piix4               9639  0 
k8temp                  3912  0 
shpchp                 33679  0 
lp                      9336  0 
parport                37160  3 ppdev,parport_pc,lp
usbhid                 40988  0 
ohci1394               30260  0 
hid                    83376  1 usbhid
floppy                 63156  0 
ieee1394               94675  1 ohci1394
ahci                   37646  4 
sky2                   48803  0 
pata_atiixp             4209  0 

```

---

### Post by ceixeoida on 2010-06-06
*bump*

---

### Post by brwarner on 2010-06-06
I think we're in the same boat: [http://ubuntuforums.org/showthread.php?t=1503135](http://ubuntuforums.org/showthread.php?t=1503135)

---

### Post by marcoftheknight on 2010-06-06
Sorry can you also tell me the ouput of 
iwconfig

thanks

---

### Post by dineshs on 2010-06-07
I have a suggestion
Let  /etc/network/interfaces
```
sudo gedit /etc/network/interfaces
``` contain only this
```
auto lo 
iface lo inet loopback
```   
Now configure NM manually if you know the IP address and gateway 
Right-click on the NM icon(two opposite arrows on top right) and then click on Edit Connections. 
Select the tab, wired 
select the ethernet connection you want and click edit(you can add the ethernet connection if not listed) 
select ipv4 
method-manual 
click add 
address 192.168.1.100 
mask 255.255.255.0 
gateway 192.168.1.1 
then hit enter 
DNS 4.2.2.1
then click apply 
ref:[https://help.ubuntu.com/community/NetworkManager0.7](https://help.ubuntu.com/community/NetworkManager0.7) 
Note :The IP addresses are examples.Substitute your values

---

