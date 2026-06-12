---
title: "Ralink RT73 not working on ubuntu 10.4 LTS"
date: 2010-11-10
forum: Networking &amp; Wireless
---

### Post by LeMeun on 2010-11-10
Hello All,

After many days of search I decided to post my thread:

My ralink RT2501USB Wireless is not detected by any drivers i tried so far on Ubuntu 10.04 LTS.

My configuration is as follow: iMac 10.5.8 running Ubuntu 10.04 LTS using Parallels Desktop 5 (Build 5.0.9308 )

lsusb:
```

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 148f:2573 Ralink Technology, Corp. RT2501USB Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

lsusb -vd 148f:2573
```

Bus 001 Device 002: ID 148f:2573 Ralink Technology, Corp. RT2501USB Wireless Adapter
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            6 Imaging
  bDeviceSubClass         2 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x148f Ralink Technology, Corp.
  idProduct          0x2573 RT2501USB Wireless Adapter
  bcdDevice            0.01
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      0
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            6 Imaging
  bDeviceSubClass         2 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)


```

lsmod (at start up):
```

Module                  Size  Used by
prl_fs_freeze           3037  0 
binfmt_misc             6587  1 
ppdev                   5259  0 
prl_fs                 19559  1 
snd_intel8x0           25588  2 
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
snd                    54180  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                63245  0 
serio_raw               3978  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
intel_agp              24119  0 
lp                      7060  0 
prl_eth                 3747  0 
shpchp                 28820  0 
agpgart                31724  1 intel_agp
prl_tg                  9941  1 prl_fs
parport                32635  2 ppdev,lp
floppy                 53016  0 

```

We can see that no drivers module is loaded for my Ralink rt73

dmesg:
```

[   23.981557] intel8x0: clocking to 48000
[   32.116815] eth0: no IPv6 routers present
[  707.600267] usb 1-1: new high speed USB device using ehci_hcd and address 2
[  712.764534] usb 1-1: unable to read config index 0 descriptor/start: -110
[  712.764539] usb 1-1: chopping to 0 config(s)
[  722.795030] usb 1-1: no configuration chosen from 0 choices
[ 4384.188297] usb 1-1: usbfs: USBDEVFS_CONTROL failed cmd lsusb rqt 128 rq 6 len 255 ret -110
[ 4385.196510] usb 1-1: usbfs: USBDEVFS_CONTROL failed cmd lsusb rqt 128 rq 6 len 255 ret -110

```

modprobe rt73usb
lsmod:
```

[COLOR="Red"]**rt73usb                22434  0**[/COLOR] 
crc_itu_t               1371  1 rt73usb
[COLOR="Red"][B]rt2x00usb               9703  1 rt73usb
rt2x00lib              27509  2 rt73usb,rt2x00usb[/B][/COLOR]
led_class               2864  1 rt2x00lib
mac80211              205402  2 rt2x00usb,rt2x00lib
cfg80211              126528  2 rt2x00lib,mac80211
prl_fs_freeze           3037  0 
binfmt_misc             6587  1 
ppdev                   5259  0 
prl_fs                 19559  1 
snd_intel8x0           25588  2 
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
snd                    54180  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                63245  0 
serio_raw               3978  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
intel_agp              24119  0 
lp                      7060  0 
prl_eth                 3747  0 
shpchp                 28820  0 
agpgart                31724  1 intel_agp
prl_tg                  9941  1 prl_fs
parport                32635  2 ppdev,lp
floppy                 53016  0 

```

Still no wifi.

iwconfig:
```

lo        no wireless extensions.

eth0      no wireless extensions.



```

ifconfig wlan0 up:
```

wlan0: ERROR while getting interface flags: No such device

```

ifconfig ra0 up:
```

ra0: ERROR while getting interface flags: No such device

```

ifconfig rausb0 up:
```

rausb0: ERROR while getting interface flags: No such device

```

modinfo rt73usb:
```

filename:       /lib/modules/2.6.32-25-generic/kernel/drivers/net/wireless/rt2x00/rt73usb.ko
license:        GPL
firmware:       rt73.bin
description:    Ralink RT73 USB Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     B2DAB8FC7411BF51A42D340
alias:          usb:v0586p3415d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp001Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7167p3840d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB50d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB01d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p200Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v6933p5001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0769p31F3d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p9712d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p90ACd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0027d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0024d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p7100d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04E8p4471d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18E8p6238d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18E8p6229d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18E8p6196d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2671d*dc*dsc*dp*ic*isc*ip*
alias:          [COLOR="Red"]**usb:v148Fp2573d*dc*dsc*dp*ic*isc*ip***[/COLOR]
alias:          usb:v04BBp093Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1B75p7318d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0pA874d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0pA861d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6874d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6877d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p4600d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p0028d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p0023d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p0020d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v06F8pE020d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v06F8pE010d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v06F8pE002d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1472p0009d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p8008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15A9p0004d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p3701d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7318d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C07d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C04d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C03d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp002Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C22d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1371p9032d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1371p9022d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p0119d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p0116d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p00F4d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p00D8d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v08DDp0120d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1631pC019d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp905Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp905Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp705Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp7050d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1724d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1723d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0722d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18C5p0002d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0EB0p9021d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp9021d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C10d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8pB21Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8pB21Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8pB21Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8pB21Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8pB21Bd*dc*dsc*dp*ic*isc*ip*
depends:        rt2x00lib,rt2x00usb,crc-itu-t
vermagic:       2.6.32-25-generic SMP mod_unload modversions 586 
parm:           nohwcrypt:Disable hardware encryption. (bool)


```

Drivers tried: RT73usb (out of the box) 

I compiled and installed the following drivers without any success:
RT73_Linux_STA_Drv1.0.3.6 (Ralink website)
2010_0817_RT73_Linux_STA_Drv1.1.0.4 (Ralink website)
rt73-k2wrlz-source_3.0.3-2_ppa0_karmic_all.deb
rt73-k2wrlz-3.0.3.tar.bz2

/etc/modprobe.d/blacklist.conf:
```

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done # by a nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

#Wireless usb
#blacklist rt2x00usb
#blacklist rt2x00lib
blacklist rt2500usb


```

I noticed a blacklist from parallels:
/etc/modprob.d/blacklist-parallels.conf

```

# replaced by prl_eth
blacklist ne2k-pci
# prevent memory corruption
blacklist iTCO_wdt


```

This is as far as I go, at first i wanted to try the rt73-k2wrlz-3.0.3 driver to test my wifi network but now if i can only make my usb wifi working under ubuntu I'll be glad already :)

Of course my USB wifi is working on my MAC OS X 10.5.8 (detected as en3) using Ralink USB Wireless utility ver. 1.5.1.0
ifconfig:
```

en3: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 1500
	inet6 fe80::20e:2eff:fee3:a5bc%en3 prefixlen 64 scopeid 0x5 
	inet 169.254.100.203 netmask 0xffff0000 broadcast 169.254.255.255
	ether 00:0e:2e:e3:a5:bc 
	media: autoselect status: active
	supported media: autoselect

```

Any help or comments will be greatly appreciated.

---

### Post by MooPi on 2010-11-10
Can you give some details as to your failure installing Ralink driver. Where did the process stick ?

---

### Post by LeMeun on 2010-11-10
the interface is never brought up, i don't know if it is the driver that does not recognize the card or the fact that i use parallels emulator but as the dmesg shows:
```

[   32.116815] eth0: no IPv6 routers present
[  707.600267] usb 1-1: new high speed USB device using ehci_hcd and address 2
[  712.764534] usb 1-1: unable to read config index 0 descriptor/start: -110
[  712.764539] usb 1-1: chopping to 0 config(s)
[  722.795030] usb 1-1: no configuration chosen from 0 choices
[ 4384.188297] usb 1-1: usbfs: USBDEVFS_CONTROL failed cmd lsusb rqt 128 rq 6 len 255 ret -110
[ 4385.196510] usb 1-1: usbfs: USBDEVFS_CONTROL failed cmd lsusb rqt 128 rq 6 len 255 ret -110
[ 4869.724666] cfg80211: Calling CRDA to update world regulatory domain
[ 4869.781321] cfg80211: World regulatory domain updated:
[ 4869.781323] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 4869.781325] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4869.781327] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4869.781329] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4869.781331] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4869.781333] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4869.839636] usbcore: registered new interface driver rt73usb
[ 6641.190050] usb 1-1: USB disconnect, address 2
[18706.088511] usb 1-1: new high speed USB device using ehci_hcd and address 3
[18711.252330] usb 1-1: unable to read config index 0 descriptor/start: -110
[18711.252335] usb 1-1: chopping to 0 config(s)
[18721.283326] usb 1-1: no configuration chosen from 0 choices
[19383.023424] usbcore: deregistering interface driver rt73usb
[19383.297236] rt73: init
[19383.297238] rt73 k2wrlz modification 3.0.3
[19383.297763] usbcore: registered new interface driver rt73
[19558.262858] usb 1-1: USB disconnect, address 3
[19587.840200] usb 1-1: new high speed USB device using ehci_hcd and address 4
[19593.008047] [COLOR="Red"]**usb 1-1: unable to read config index 0 descriptor/start: -110**[/COLOR]
[19593.008055] usb 1-1: chopping to 0 config(s)
[19603.039052] usb 1-1: no configuration chosen from 0 choices
[21591.683787] usbcore: deregistering interface driver rt73
[21591.686454] rt73: exit
[21684.338810] rt73: init
[21684.338812] rt73 k2wrlz modification 3.0.3
[21684.338832] usbcore: registered new interface driver rt73

```

The driver never bring the interface up even when i try ifconfig wlan0 up or any other name used by the different drivers.

---

### Post by MooPi on 2010-11-10
Not what I was looking for. When you tried to compile/config the driver from Ralink what error messages to you get ? Don't know if you have the necessary utils to build the driver.Might need build-essential & gcc to get the driver to config?

---

### Post by LeMeun on 2010-11-10
root@ubuntu:# apt-get install build-essential gcc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
gcc is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 16 not upgraded.

---

### Post by LeMeun on 2010-11-10
the driver compile fine with no error but i'll compil it again and check the log file you might be right.

Thanks

---

### Post by LeMeun on 2010-11-12
I re-compile the rt73 driver, here is the terminal output:

```

yannek@ubuntu:~/2010_0817_RT73_Linux_STA_v1.1.0.4/Module$ [COLOR="Red"]**sudo make**[/COLOR]
[sudo] password for yannek: 
make -C /lib/modules/2.6.32-25-generic/build SUBDIRS=/home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-25-generic'
  CC [M]  /home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/rtmp_main.o
/home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/rtmp_main.c: In function ‘usb_rtusb_probe’:
/home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/rtmp_main.c:1152: warning: return makes integer from pointer without a cast
/home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/rtmp_main.c: In function ‘usb_rtusb_disconnect’:
/home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/rtmp_main.c:1314: warning: initialization discards qualifiers from pointer target type
/home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/rtmp_main.c:1314: warning: ISO C90 forbids mixed declarations and code
/home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/rtmp_main.c: In function ‘usb_rtusb_close’:
/home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/rtmp_main.c:655: warning: the frame size of 2140 bytes is larger than 1024 bytes
  CC [M]  /home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/mlme.o
/home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/mlme.c: In function ‘MlmeEnqueueForRecv’:
/home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/mlme.c:3473: warning: the frame size of 1100 bytes is larger than 1024 bytes
/home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/mlme.c: In function ‘MlmeRadioOff’:
/home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/mlme.c:2213: warning: the frame size of 2088 bytes is larger than 1024 bytes
  CC [M]  /home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/connect.o
  CC [M]  /home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/rtusb_bulk.o
/home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/rtusb_bulk.c: In function ‘RTUSBInitRxDesc’:
/home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/rtusb_bulk.c:550: warning: passing argument 6 of ‘RTusb_fill_bulk_urb’ from incompatible pointer type
/home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/rtusb_bulk.c:43: note: expected ‘usb_complete_t’ but argument is of type ‘void (*)(struct urb *, struct pt_regs *)’
/home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/rtusb_bulk.c: In function ‘RTUSBBulkOutDataPacket’:
/home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/rtusb_bulk.c:649: warning: passing argument 4 of ‘RTUSBInitTxDesc’ from incompatible pointer type
/home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/rtusb_bulk.c:505: note: expected ‘usb_complete_t’ but argument is of type ‘void (*)(struct urb *, struct pt_regs *)’
/home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/rtusb_bulk.c: In function ‘RTUSBBulkOutNullFrame’:
/home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/rtusb_bulk.c:705: warning: passing argument 4 of ‘RTUSBInitTxDesc’ from incompatible pointer type
/home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/rtusb_bulk.c:505: note: expected ‘usb_complete_t’ but argument is of type ‘void (*)(struct urb *, struct pt_regs *)’
/home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/rtusb_bulk.c: In function ‘RTUSBBulkOutRTSFrame’:
/home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/rtusb_bulk.c:769: warning: passing argument 4 of ‘RTUSBInitTxDesc’ from incompatible pointer type
/home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/rtusb_bulk.c:505: note: expected ‘usb_complete_t’ but argument is of type ‘void (*)(struct urb *, struct pt_regs *)’
/home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/rtusb_bulk.c: In function ‘RTUSBBulkOutMLMEPacket’:
/home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/rtusb_bulk.c:830: warning: passing argument 4 of ‘RTUSBInitTxDesc’ from incompatible pointer type
/home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/rtusb_bulk.c:505: note: expected ‘usb_complete_t’ but argument is of type ‘void (*)(struct urb *, struct pt_regs *)’
/home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/rtusb_bulk.c: In function ‘RTUSBBulkOutPsPoll’:
/home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/rtusb_bulk.c:882: warning: passing argument 4 of ‘RTUSBInitTxDesc’ from incompatible pointer type
/home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/rtusb_bulk.c:505: note: expected ‘usb_complete_t’ but argument is of type ‘void (*)(struct urb *, struct pt_regs *)’
  CC [M]  /home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/rtusb_io.o
  CC [M]  /home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/sync.o
/home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/sync.c: In function ‘PeerBeaconAtScanAction’:
/home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/sync.c:562: warning: the frame size of 1528 bytes is larger than 1024 bytes
  CC [M]  /home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/assoc.o
/home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/assoc.c: In function ‘link_status_handler’:
/home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/assoc.c:749: warning: embedded ‘\0’ in format
/home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/assoc.c:773: warning: embedded ‘\0’ in format
  CC [M]  /home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/auth.o
  CC [M]  /home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/auth_rsp.o
  CC [M]  /home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/rtusb_data.o
/home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/rtusb_data.c: In function ‘RTUSBRxPacket’:
/home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/rtusb_data.c:2233: warning: ISO C90 forbids mixed declarations and code
/home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/rtusb_data.c:2271: warning: ISO C90 forbids mixed declarations and code
  CC [M]  /home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/rtmp_init.o
/home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/rtmp_init.c: In function ‘RTMPReadParametersFromFile’:
/home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/rtmp_init.c:2328: warning: ‘osFSInfo.fs.seg’ may be used uninitialized in this function
  CC [M]  /home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/sanity.o
  CC [M]  /home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/rtmp_wep.o
  CC [M]  /home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/rtmp_info.o
/home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/rtmp_info.c: In function ‘rt_ioctl_iwaplist’:
/home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/rtmp_info.c:691: warning: the frame size of 1284 bytes is larger than 1024 bytes
/home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/rtmp_info.c: In function ‘RTMPIoctlStatistics’:
/home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/rtmp_info.c:6541: warning: the frame size of 1608 bytes is larger than 1024 bytes
/home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/rtmp_info.c: In function ‘RTMPIoctlMAC’:
/home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/rtmp_info.c:6325: warning: the frame size of 1336 bytes is larger than 1024 bytes
/home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/rtmp_info.c: In function ‘RTMPIoctlBBP’:
/home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/rtmp_info.c:6139: warning: the frame size of 2324 bytes is larger than 1024 bytes
  CC [M]  /home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/rtmp_tkip.o
  CC [M]  /home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/wpa.o
  CC [M]  /home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/md5.o
  CC [M]  /home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/netif_block.o
  LD [M]  /home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/rt73.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/rt73.mod.o
  LD [M]  /home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/rt73.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-25-generic'


```
yannek@ubuntu:~/2010_0817_RT73_Linux_STA_v1.1.0.4/Module$ [COLOR="Red"]**sudo make install**[/COLOR]
make -C /lib/modules/2.6.32-25-generic/build \
	INSTALL_MOD_DIR=extra SUBDIRS=/home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module \
	modules_install 
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-25-generic'
  INSTALL /home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/rt73.ko
  DEPMOD  2.6.32-25-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-25-generic'
Network device directory /etc/sysconfig/network-scripts
Module configuration file /etc/modprobe.conf 
grep: /etc/modprobe.conf: No such file or directory
append 'alias [COLOR="Red"]**rausb0**[/COLOR] rt73' to /etc/modprobe.conf 
/sbin/depmod -a

```

yannek@ubuntu:~/2010_0817_RT73_Linux_STA_v1.1.0.4/Module$ ifconfig rausb0 up
rausb0: ERROR while getting interface flags: No such device


```

now that's what i got:

```

yannek@ubuntu:~/2010_0817_RT73_Linux_STA_v1.1.0.4/Module$ sudo depmod -a
yannek@ubuntu:~/2010_0817_RT73_Linux_STA_v1.1.0.4/Module$ sudo modprobe rt73
WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.
FATAL: [COLOR="Red"]**Module rt73 not found**[/COLOR].

```

```

yannek@ubuntu:~/2010_0817_RT73_Linux_STA_v1.1.0.4/Module$ lsmod
Module                  Size  Used by
prl_fs_freeze           3037  0 
binfmt_misc             6587  1 
ppdev                   5259  0 
prl_fs                 19559  1 
snd_intel8x0           25588  2 
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
psmouse                63245  0 
serio_raw               3978  0 
snd                    54180  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
intel_agp              24119  0 
shpchp                 28820  0 
lp                      7060  0 
prl_eth                 3747  0 
agpgart                31724  1 intel_agp
prl_tg                  9941  1 prl_fs
parport                32635  2 ppdev,lp
floppy                 53016  0 

```

any suggestion?

---

### Post by uncaspi on 2010-11-12
Try locate rt73.ko and copy it to the directory where the other drivers are stored. Usually this will be somewhere in
/lib/modules............./kernel/drivers/2.6.32-25-generic/net/wireless  
Something like that.

---

### Post by LeMeun on 2010-11-12
Thanks uncaspi,

I run a search and found rt73.ko in those location:
/lib/modules/2.6.32-25/updates/dkms/rt73.ko
/lib/modules/2.6.32-25-generic/kernel/drivers/net/wireless/rt2x00/rt73.ko
/lib/modules/2.6.32-25-generic/extra/rt73.ko

I replace it with the one i just compiled previously. I search for rt73.bin and found it here:
/lib/firmware/rt73.bin
and replaced with mine too. (I made backup of course)

so i ran modprobe without a problem then the lsmod:

```

root@ubuntu:/home/yannek# lsmod
Module                  Size  Used by
[COLOR="Red"]**rt73                  331550  0 **[/COLOR]
prl_fs_freeze           3037  0 
binfmt_misc             6587  1 
ppdev                   5259  0 
prl_fs                 19559  1 
snd_intel8x0           25588  2 
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
psmouse                63245  0 
serio_raw               3978  0 
snd                    54180  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
intel_agp              24119  0 
shpchp                 28820  0 
lp                      7060  0 
prl_eth                 3747  0 
agpgart                31724  1 intel_agp
prl_tg                  9941  1 prl_fs
parport                32635  2 ppdev,lp
floppy                 53016  0 


```

We can see rt73 is assigned to 0 device!  

lsusb:
```

root@ubuntu:/home/yannek# lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device [COLOR="Red"]**005**[/COLOR]: ID [COLOR="Red"]**148f:2573 Ralink**[/COLOR] Technology, Corp. RT2501USB Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```

My Wifi usb is device 05 so still not working.
I moved the /etc/modprbe.conf to /etc/modprobe.d/rt73.conf
the content of this file is:
```

alias rausb0 rt73

```
which coincide with the last line of the make install. For this driver my interface name should be rausb0

modinfo give me this:

```

root@ubuntu:/home/yannek# modinfo rt73
filename:       [COLOR="Red"]**/lib/modules/2.6.32-25-generic/updates/dkms/rt73.ko**[/COLOR]
license:        GPL
description:    RT73 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
srcversion:     F7413197302F8AC660DEED1
alias:          usb:v13B1p0020d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p0023d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C03d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp705Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1724d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1723d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p3415d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p00D8d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0EB0p9021d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp9021d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p90ACd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p9712d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0722d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1631pC019d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1371p9032d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1371p9022d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1472p0009d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0769p31F3d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8pB21Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0pA861d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0pA874d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6877d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C22d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p8008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18E8p6238d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18E8p6229d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18E8p6196d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp093Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2671d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2573d*dc*dsc*dp*ic*isc*ip*
depends:        
vermagic:       2.6.32-25-generic SMP mod_unload modversions 586 
parm:           hostname:Host Name (charp)


```

So the rt73.ko loaded by the system come from the dkms folder maybe i should delete it and uninstall dkms (since it is the only driver it is handling) to see if the system will go look in the others locations previously cited.

For those like me in trouble with drivers and following up this thread to get new ideas how to solve there problem. Please keep in mind that I am under a virtual machine so if anything goes bad my main OS will not crash just the emulated Ubuntu. Be cautious when messing around with the /lib/ content under Ubuntu only.

---

### Post by LeMeun on 2010-11-12
To summaries still not working:
The rt73 driver is loaded and the usb connected but the ifconfig give:
```

root@ubuntu:/home/yannek# ifconfig rausb0 up
rausb0: ERROR while getting interface flags: No such device

```

Even though my usb shows up on lsusb and the rt73 driver on lsmod i cannot bring up my interface. I rebooted many times with the usb plug and not plug, i try to plug and load the driver after or the reverse. I set to load the driver at boot with /etc/modules with the usb plug at booting. 

Nothing work and this is the latest ralink driver straight from the Ralink website. (2010_0817_RT73_Linux_STA_v1.1.0.4)

This card was working on hardy heron (Ralink driver) without problem and it is working on an emulated Slitaz (k2wlrz driver 3.0.3)

I am out of idea.

---

### Post by uncaspi on 2010-11-12
I think rt73.ko must reside in
/lib/modules/2.6.32-25-generic/kernel/drivers/net/wireless

modprobe it again and restart networking or reboot

The file must not be named rt73.bin but rt73.ko

and you'll probably found in the directory you compiled it. If not type updatedb   and type locate rt73.ko

---

### Post by LeMeun on 2010-11-12
I place the rt73.ko i compiled in the 
/lib/modules/2.6.32-25-generic/kernel/drivers/net/wireless

I uninstalled the dkms:
```

root@ubuntu:/home/yannek# dkms
The program 'dkms' is currently not installed.  You can install it by typing:
apt-get install dkms

```

I rebooted and lsmod doesn't show any rt73 so I ran modprobe:

```

root@ubuntu:/home/yannek# modprobe rt73
FATAL: Could not open '/lib/modules/2.6.32-25-generic/updates/dkms/rt73.ko': No such file or directory

```

I cannot load the module even though it is present in those locations:
```

root@ubuntu:/home/yannek# updatedb
root@ubuntu:/home/yannek# locate rt73.ko
/home/yannek/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/rt73.ko
/home/yannek/wifi/2010_0817_RT73_Linux_STA_v1.1.0.4/Module/rt73.ko
/lib/modules/2.6.32-25-generic/extra/rt73.ko
/lib/modules/2.6.32-25-generic/kernel/drivers/net/wireless/rt73.ko
/lib/modules/2.6.32-25-generic/kernel/drivers/net/wireless/rt2x00/rt73.ko


```

---

### Post by LeMeun on 2010-11-12
The system still looking in the dkms location which I desinstall. The dkms folder doesn't exist anymore. I don't know where do we define the path for the module.

Anyway prior to that i tried to put my rt73.ko in the dkms folder just in case and I didn't get the FATAL ERROR, the module load but the usb still not work.

---

### Post by uncaspi on 2010-11-12
OK install dkms again and we take it from there.

---

### Post by LeMeun on 2010-11-12
ok i though after messing up with my Ubuntu 10.04 /lib/ folder and installing different drivers I should just make a fresh install. So backup some files and erase the virtual machine.

Then tempted by a Ubuntu 10.10, I installed it. My usb adapter RT73 still not recognized, the virtual machine tools can't be compiled (with make, linux-headers, gcc,... installed) and it is very slow on virtual machine. So I end up trashing it too.

I brought back my old laptop where everything was working ages ago and found out that the working flavor was Ubuntu 9.10 Karmic Koala (2.6.31-14-generic). Got it online and installed, my card is working at first boot!
nothing to do! Ifconfig and it is there:
```

yannek@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1c:42:ed:7f:64  
          inet addr:10.0.0.5  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:42ff:feed:7f64/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:207034 errors:0 dropped:0 overruns:0 frame:0
          TX packets:111833 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:311226559 (311.2 MB)  TX bytes:7984061 (7.9 MB)
          Interrupt:10 Base address:0x8200 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

[COLOR="Red"]**wlan0**[/COLOR]     Link encap:Ethernet  HWaddr 00:0e:2e:e3:a5:bc  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-0E-2E-E3-A5-BC-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

lsmod:
```

yannek@ubuntu:~$ lsmod
Module                  Size  Used by
isofs                  31620  1 
udf                    80900  0 
prl_fs_freeze           4316  0 
binfmt_misc             8356  1 
ppdev                   6688  0 
arc4                    1660  2 
snd_intel8x0           30168  2 
ecb                     2524  2 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
iptable_filter          3100  0 
snd_mixer_oss          16028  1 snd_pcm_oss
prl_fs                 21444  1 
ip_tables              11692  1 iptable_filter
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
x_tables               16544  1 ip_tables
[COLOR="Red"]**rt73usb**[/COLOR]                26336  0 
crc_itu_t               1852  2 udf,rt73usb
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
[COLOR="Red"]**rt2500usb**[/COLOR]              21152  0 
[COLOR="Red"]**rt2x00usb**[/COLOR]              11548  2 rt73usb,rt2500usb
[COLOR="Red"]**rt2x00lib**[/COLOR]              29756  3 rt73usb,rt2500usb,rt2x00usb
led_class               4096  1 rt2x00lib
input_polldev           3716  1 rt2x00lib
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
mac80211              181236  2 rt2x00usb,rt2x00lib
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
cfg80211               93052  2 rt2x00lib,mac80211
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                56180  0 
serio_raw               5280  0 
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
shpchp                 32272  0 
prl_eth                 5180  0 
prl_tg                 11840  1 prl_fs
lp                      8964  0 
parport                35340  2 ppdev,lp
floppy                 54916  0 
intel_agp              27484  0 
agpgart                34988  1 intel_agp


```

As we can see many modules are involved but it is working and it is all i ask. So sorry to give up on the Ubuntu 10.04 but 9.10 is my new flavor now. Does not sound progressive but it is practical... at least until 2011 for the support.

uncaspi and Moopi thanks for the help

---

### Post by LeMeun on 2010-11-13
**To summarize:**

I was not able to find a suitable driver/module for my USB RT73 wifi adapter:

```

Bus 001 Device 002: ID **148f:2573 Ralink** Technology, Corp. RT2501USB Wireless Adapter

```

under Ubuntu 10.04. I tried on Ubuntu 10.10 and I had the same issues, the driver rt73usb (out of the box) should recognize my Usb adapter but does not!

Under Ubuntu 9.10 Karmic Koala my Usb adapter work right away after first boot using the driver RT73usb and many others (out of the box) so problem solved for me until the support last for this flavor of Ubuntu (2011).

PS: For those looking for monitor mode and injection, the RT73usb driver from Ubuntu 9.10 does not support monitor mode and injection! If you are looking for a good RT73 driver for monitor mode, injections, fragmentation attack here is the link:
[[COLOR="Blue"]_http://homepages.tu-darmstadt.de/~p_larbig/wlan/]("http://homepages.tu-darmstadt.de/~p_larbig/wlan/")_[/COLOR]

but if you try to compile the rt73-k2wrlz-3.0.3.tar.bz2 driver yourself you may encounter some kernel issues during the "make" process so i found a nice deb package that work fine with my 9.10 karmic koala kernel 2.6.31-22. It is attached, I had to tar.gz it in order to post it so just untar it (by clicking on it) and double click on the **rt73-k2wrlz-source_3.0.3-2~ppa0~karmic_all.deb** file to install it. It does the blacklist of the bad rt2500usb,rt73usb,... drivers that jeopardize the usb adapter detection.

your interface name will be [COLOR="Black"]ralan0[/COLOR] for smoother wireshark experience...

all thumbs up for Pedro Larbiq (driver) and [[COLOR="Blue"]_Marco Giorgi_[/COLOR]]("https://launchpad.net/~marco/+archive/ppa/+build/1408570") (deb package)

So long, will make some coffee ;)

---

### Post by psulinux24 on 2011-03-09
So I'm hoping this thread is still active.  I download and installed the .deb but seemingly to no effect.  I still only get wlan0 (shouldn't it be rausb0 or r*  if it worked?)   and when I attempt to go to monitor mode on airmon-ng I get: 

Interface    Chipset        Driver

wlan0        Unknown         usb (monitor mode enabled)
  
which immediately reverts to:
Interface    Chipset        Driver

wlan0        Unknown         usb


Going crazy try9ing to figure out how to get it to stay in monitor mode and actually work!?

---

### Post by forrestgump2000 on 2011-05-20
The problem is with Parallels. USB support is quite spotty.  I too get the following error when attempting to use my RT73:
unable to read config index 0 descriptor/start: -110 
[FONT=monospace]
[/FONT]Using the exact same Linux live cd with Virtualbox or VMWare allows the adapter to work flawlessly.  I am using Parallels 5, and I'm not sure if Parallels 6 improves the situation any.  I am not currently aware of any workaround.

Why does the title of this thread have "[solved]" in it, actually?   Is there a fix somewhere in it that I missed?

---

