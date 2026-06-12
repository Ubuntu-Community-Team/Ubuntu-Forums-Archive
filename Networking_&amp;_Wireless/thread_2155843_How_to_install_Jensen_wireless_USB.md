---
title: "How to install Jensen wireless USB"
date: 2013-06-19
forum: Networking &amp; Wireless
---

### Post by yBfj3nbmn7 on 2013-06-19
Hi!

I've got some problems installing a wireless USB stick on my computer.

I'm running Ubuntu 10.04, 32 bit, Linux 2.6.32-48-generic.

The USB I'm trying to install is a Jensen Air:Link 25150. The USB comes with a CD with Linux drivers, and the same drivers can be downloaded from [http://www.jensenscandinavia.com/downloads]("http://www.jensenscandinavia.com/downloads").

The CD includes a readme file which says how to build the drivers. But I've never built a driver before, so I don't understand what's going on.

The readme instructions for doing this are:

```
1> $tar -xvzf DPB_RT2870_Linux_STA_x.x.x.x.tgz
    go to "./DPB_RT2870_Linux_STA_x.x.x.x" directory.
    
2> In Makefile
	 set the "MODE = STA" in Makefile and chose the TARGET to Linux by set "TARGET = LINUX"
	 define the linux kernel source include file path LINUX_SRC
	 modify to meet your need.

3> In os/linux/config.mk 
	define the GCC and LD of the target machine
	define the compiler flags CFLAGS
	modify to meet your need.
	** Build for being controlled by NetworkManager or wpa_supplicant wext functions
	   Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.
	   => #>cd wpa_supplicant-x.x
	   => #>./wpa_supplicant -Dwext -ira0 -c wpa_supplicant.conf -d
	** Build for being controlled by WpaSupplicant with Ralink Driver
	   Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n'.
	   => #>cd wpa_supplicant-0.5.7
	   => #>./wpa_supplicant -Dralink -ira0 -c wpa_supplicant.conf -d

4> $make
	# compile driver source code
	# To fix "error: too few arguments to function ¡¥iwe_stream_add_event"
	  => $patch -i os/linux/sta_ioctl.c.patch os/linux/sta_ioctl.c

5> $cp RT2870STA.dat  /etc/Wireless/RT2870STA/RT2870STA.dat
    
6> load driver, go to "os/linux/" directory.
    #[kernel 2.4]
    #    $/sbin/insmod rt2870sta.o
    #    $/sbin/ifconfig ra0 inet YOUR_IP up
        
    #[kernel 2.6]
    #    $/sbin/insmod rt2870sta.ko
    #    $/sbin/ifconfig ra0 inet YOUR_IP up

7> unload driver    
    $/sbin/ifconfig ra0 down
	$/sbin/rmmod rt2870sta
```

I have no problems with step number 1, but I have no clue what to do from step 2 and forward.

Can anybody help me?

---

### Post by praseodym on 2013-06-19
Hi,

please check the outputs of:
```

lsusb
lsmod
iwconfig
```
Driver rt2870sta is already part of kernel 2.6, but you know that 10.04 is outdated?

---

### Post by yBfj3nbmn7 on 2013-06-19
Yeah, I know that 10.04 is getting quite old. But I still get automatic updates via Update Manager, so I haven't bothered making the switch to something newer when the old system works just fine.

lsusb:

```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c01e Logitech, Inc. MX518 Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 148f:3070 Ralink Technology, Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

The Ralink is the wireless USB.

lsmod:

```
Module                  Size  Used by
rt2870sta             461811  0 
arc4                    1153  2 
rt2800usb              31531  0 
rt2x00usb               9639  1 rt2800usb
rt2x00lib              27573  2 rt2800usb,rt2x00usb
led_class               2864  1 rt2x00lib
mac80211              205434  2 rt2x00usb,rt2x00lib
cfg80211              126496  2 rt2x00lib,mac80211
crc_ccitt               1339  1 rt2800usb
isofs                  29250  1 
udf                    79699  0 
crc_itu_t               1371  1 udf
binfmt_misc             6523  1 
snd_hda_codec_atihdmi     2367  1 
snd_hda_codec_realtek   203472  1 
snd_hda_intel          22069  2 
snd_hda_codec          74297  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_seq_dummy           1338  0 
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19130  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ppdev                   5259  0 
sbp2                   19448  0 
ieee1394               81181  1 sbp2
parport_pc             25962  1 
intel_agp              24375  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
fglrx                2092908  32 
agpgart                31724  2 intel_agp,fglrx
lp                      7060  0 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  1 
vgastate                8961  1 vga16fb
parport                32635  3 ppdev,parport_pc,lp
usbhid                 36110  0 
hid                    67288  1 usbhid
r8169                  34140  0 
mii                     4381  1 r8169

```

iwconfig:

```
lo        no wireless extensions.

eth1      no wireless extensions.

wlan1     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

```

---

### Post by praseodym on 2013-06-19
You need to blacklist the following driver:
```

echo "blacklist rt2800usb" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot.

---

### Post by yBfj3nbmn7 on 2013-06-19
Wow, amazing! That simple advise solved my problem! Now, my new wireless USB is basically as fast as the 15 meter cable I had running through my apartment.

I just rebooted the computer, and the modem worked "out-of-the-box"!

Thank you, Praseodym!

---

