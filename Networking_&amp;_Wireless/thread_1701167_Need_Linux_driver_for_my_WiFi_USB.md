---
title: "Need Linux driver for my WiFi USB"
date: 2011-03-06
forum: Networking &amp; Wireless
---

### Post by Snooper01 on 2011-03-06
Hello UbuntuForums.org ,
I just installed UBUNTU on my pc, after installing the system I plugged my USB WiFi, but no wifi network is detected,
Please i need quick help, because i can't connect to the Net without this Wifi
Here is some informations:
```

cat /etc/lsb-release :
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04 LTS"

lsusb :
Bus 003 Device 002: ID 046d:c051 Logitech, Inc. G3 (MX518) Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 015: ID 148f:2070 Ralink Technology, Corp. 
Bus 001 Device 014: ID 1516:8628 CompUSA 128M Pen Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

lspci :
00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9500 GT] (rev a1)
02:01.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

lspci -nn | grep -i net:
02:03.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)

sudo lshw -C network :
*-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth0
       version: 10
       serial: 00:16:17:39:5b:4a
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:23 ioport:de00(size=256) memory:fddfe000-fddfe0ff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:08:10:72:a9:98
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bgn

lsmod :
Module                  Size  Used by
arc4                    1153  2 
rt2800usb              31531  0 
rt2x00usb               9703  1 rt2800usb
rt2x00lib              27509  2 rt2800usb,rt2x00usb
led_class               2864  1 rt2x00lib
mac80211              204922  2 rt2x00usb,rt2x00lib
cfg80211              126485  2 rt2x00lib,mac80211
crc_ccitt               1339  1 rt2800usb
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8901  1 
fat                    47767  1 vfat
usb_storage            39425  1 
nls_utf8                1069  1 
isofs                  29250  1 
binfmt_misc             6587  1 
snd_hda_codec_realtek   203168  1 
zl10039                 3548  1 
snd_hda_intel          21877  2 
mt312                   6871  1 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
fbcon                  35102  71 
tileblit                2031  1 fbcon
saa7134_alsa           10380  0 
font                    7557  1 fbcon
snd_pcm_oss            35308  0 
saa7134_dvb            22167  0 
videobuf_dvb            5175  1 saa7134_dvb
snd_mixer_oss          13746  1 snd_pcm_oss
bitblit                 4707  1 fbcon
dvb_core               86142  1 videobuf_dvb
snd_pcm                70662  4 snd_hda_intel,snd_hda_codec,saa7134_alsa,snd_pcm_oss
softcursor              1189  1 bitblit
snd_seq_dummy           1338  0 
vga16fb                11385  0 
vgastate                8961  1 vga16fb
saa7134               143391  2 saa7134_alsa,saa7134_dvb
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
ir_common              38875  1 saa7134
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
v4l2_common            15431  1 saa7134
videodev               34361  2 saa7134,v4l2_common
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
v4l1_compat            13251  1 videodev
videobuf_dma_sg        10782  3 saa7134_alsa,saa7134_dvb,saa7134
snd                    54148  17 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,saa7134_alsa,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videobuf_core          16356  3 videobuf_dvb,saa7134,videobuf_dma_sg
nouveau               467048  2 
tveeprom               11102  1 saa7134
ttm                    49943  1 nouveau
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
drm_kms_helper         29297  1 nouveau
ati_agp                 5094  0 
drm                   162471  4 nouveau,ttm,drm_kms_helper
agpgart                31724  3 ttm,ati_agp,drm
i2c_algo_bit            5028  1 nouveau
i2c_piix4               8335  0 
ppdev                   5259  0 
psmouse                63245  0 
serio_raw               3978  0 
parport_pc             25962  1 
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
8139too                18545  0 
usbhid                 36110  0 
hid                    67032  1 usbhid
8139cp                 16186  0 
floppy                 53016  0 
mii                     4381  2 8139too,8139cp
sata_sil                6959  2 
pata_atiixp             3148  1 

iwconfig :
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=12 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

ifconfig :
eth0      Link encap:Ethernet  HWaddr 00:16:17:39:5b:4a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reÃ§us:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reÃ§us:0 (0.0 B) Octets transmis:0 (0.0 B)
          Interruption:23 Adresse de base:0xde00 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:HÃ´te
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reÃ§us:444 erreurs:0 :0 overruns:0 frame:0
          TX packets:444 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reÃ§us:34880 (34.8 KB) Octets transmis:34880 (34.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:08:10:72:a9:98  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reÃ§us:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reÃ§us:0 (0.0 B) Octets transmis:0 (0.0 B)

sudo iwlist scan :
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

uname -r -m :
2.6.32-21-generic i686

cat /etc/network/interfaces :
auto lo
iface lo inet loopback

nm-tool :

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             unavailable
  Default:           no
  HW Address:        00:16:17:39:5B:4A

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800usb
  State:             disconnected
  Default:           no
  HW Address:        00:08:10:72:A9:98

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points

```

---

### Post by taylorchase on 2011-03-06
Did you just plug in the adapter and hoped that it worked or did you activate the driver? lsusb sees that your device is connected so I'm guessing it's not the hardware. System-->Administration-->Additional Drivers then select your driver and click Activate. If that doesn't work, you can try compiling compat-wireless and installing the modules yourself.

---

### Post by Snooper01 on 2011-03-06
tank you for ur reply, im new Ubuntu user,
and i can't find anything in Additional Drivers cause im not connected to the intenet ? , i just can connect to the net with my other pc so may need to download drivers from this pc ?

---

### Post by chili555 on 2011-03-06
Your device is here:> Bus 001 Device 015: ID 148f:2070 Ralink Technology, Corp. It is claimed by two conflicting drivers, let's blacklist some and explicitly load the other. Open the terminal and do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add four lines at the end:```
blacklist rt2800usb
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00lib
```Proofread, save and close gedit. Now do:```
sudo gedit /etc/modules
```Add one line:```
rt2870sta
```Proofread, save and close gedit. Reboot and tell us how well your wireless is working.

---

### Post by Snooper01 on 2011-03-06
Thank you for reply ,
i can't connect yet :( but there some changes on the terminal commands :

```

lsusb :
Bus 003 Device 002: ID 046d:c051 Logitech, Inc. G3 (MX518) Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 1516:8628 CompUSA 128M Pen Drive
Bus 001 Device 005: ID 148f:2070 Ralink Technology, Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


sudo lshw -C network :
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth0
       version: 10
       serial: 00:16:17:39:5b:4a
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:23 ioport:de00(size=256) memory:fddfe000-fddfe0ff

lsmod :
Module                  Size  Used by
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8901  1 
fat                    47767  1 vfat
usb_storage            39425  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_codec_realtek   203168  1 
snd_hda_intel          21877  2 
zl10039                 3548  1 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
saa7134_alsa           10380  0 
mt312                   6871  1 
saa7134_dvb            22167  0 
videobuf_dvb            5175  1 saa7134_dvb
dvb_core               86142  1 videobuf_dvb
snd_pcm                70662  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss,saa7134_alsa
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
saa7134               143391  2 saa7134_alsa,saa7134_dvb
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ir_common              38875  1 saa7134
nouveau               467048  2 
v4l2_common            15431  1 saa7134
ttm                    49943  1 nouveau
drm_kms_helper         29297  1 nouveau
ppdev                   5259  0 
rt2870sta             461811  0 
videodev               34361  2 saa7134,v4l2_common
v4l1_compat            13251  1 videodev
psmouse                63245  0 
snd                    54148  17 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,saa7134_alsa,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   162471  4 nouveau,ttm,drm_kms_helper
videobuf_dma_sg        10782  3 saa7134_alsa,saa7134_dvb,saa7134
videobuf_core          16356  3 videobuf_dvb,saa7134,videobuf_dma_sg
tveeprom               11102  1 saa7134
serio_raw               3978  0 
i2c_piix4               8335  0 
parport_pc             25962  1 
ati_agp                 5094  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
i2c_algo_bit            5028  1 nouveau
agpgart                31724  3 ttm,drm,ati_agp
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
usbhid                 36110  0 
hid                    67032  1 usbhid
8139too                18545  0 
8139cp                 16186  0 
mii                     4381  2 8139too,8139cp
pata_atiixp             3148  0 
sata_sil                6959  2 
floppy                 53016  0 

iwconfig :
lo        no wireless extensions.

eth0      no wireless extensions.

ifconfig :
eth0      Link encap:Ethernet  HWaddr 00:16:17:39:5b:4a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0xde00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:148 errors:0 dropped:0 overruns:0 frame:0
          TX packets:148 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11440 (11.4 KB)  TX bytes:11440 (11.4 KB)


sudo iwlist scan :
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.


uname -r -m :
2.6.32-21-generic i686


cat /etc/network/interfaces :
auto lo
iface lo inet loopback


nm-tool :

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             unavailable
  Default:           no
  HW Address:        00:16:17:39:5B:4A

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off



```

---

### Post by chili555 on 2011-03-06
Let's see if there any interesting messages about this:```
dmesg | grep rt2
modinfo rt2870sta | grep 2070
```

---

### Post by Snooper01 on 2011-03-06
```
dmesg | grep rt2 :
[   11.213287] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   11.241313] usbcore: registered new interface driver rt2870


modinfo rt2870sta | grep 2070:
```
nothing for modinfo rt2870sta | grep 2070
thx

---

### Post by chili555 on 2011-03-06
> nothing for modinfo rt2870sta | grep 2070Ah, ha! Because you have an older Ubuntu version, the usb.id is not in the rt2870sta driver. Let's fix that.

Remove the device and in a terminal, do:

```
sudo gedit /etc/udev/rules.d/network_drivers.rules

```
Add one long line:

```
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="148f", ATTR{idProduct}=="2070", RUN+="/sbin/modprobe -qba rt2870sta"
```

Caps, brackets, punctuation, spaces, etc. are crucial. Proofread twice, save and close gedit.

```
sudo gedit /etc/modprobe.d/network_drivers.conf

```
Add one long single line:

```
install rt2870sta /sbin/modprobe --ignore-install rt2870sta $CMDLINE_OPTS; /bin/echo "148f 2070" > /sys/bus/usb/drivers/rt2870/new_id
```

Proofread twice, save and close gedit. Insert the device. It ought to start immediately.

---

### Post by Snooper01 on 2011-03-06
Oh yeah , thank you , all working good now thank you so much , i can connect with my Ubuntu now :P

---

### Post by chili555 on 2011-03-06
Good job! You have helped some searchers, too. Have fun!

---

### Post by milkyky on 2012-04-04
[QUOTE=chili555;10528517]Your device is here:It is claimed by two conflicting drivers, let's blacklist some and explicitly load the other. Open the terminal and do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add four lines at the end:```
blacklist rt2800usb
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00lib
```

Hi chili555,
i know this thread is old, but i have a question regarding how u know that the device is conflicted by two drivers? because i've got my TL-WN321Gv4 recently and when i type lsmod i can see all the drivers rt.... just like his one. But i have no problem on connecting my wifi. Thou i have no problem on my wifi but just to understand this. I'm learning linux system recently.

thank you.

---

### Post by chili555 on 2012-04-05
Up until Ubuntu 11.10, certain devices were claimed by both rt2800usb and rt2870sta. Years of experience told me that rt2870sta worked well and rt2800usb didn't; hence the blacklist.

As of 11.10, rt2870sta was folded into rt2800usb and no longer exists in the kernel. If your *lsmod* shows rt2800usb and its cousins but *not* rt2870sta and, most importantly, your wireless is working well, then you are fine.

You can find out what devices are claimed by a driver with *modinfo* <some driver>:```
 modinfo rt2800usb
filename:       /lib/modules/3.0.0-17-generic-pae/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
license:        GPL
firmware:       rt2870.bin
description:    Ralink RT2800 USB Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     D2D2B027FF946B30926F11F
alias:          usb:v0586p341Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v177Fp0313d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v177Fp0153d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApF511d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApD522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApC522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA512d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0062d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0060d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0053d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p004Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p004Ad*dc*dsc*dp*ic*isc*ip*
<snip>
alias:          usb:v[COLOR="Red"]148F[/COLOR]p[COLOR="Red"]2070[/COLOR]d*dc*dsc*dp*ic*isc*ip*
<snip>
```I've highlighted the original poster's device from *lsusb*.

---

