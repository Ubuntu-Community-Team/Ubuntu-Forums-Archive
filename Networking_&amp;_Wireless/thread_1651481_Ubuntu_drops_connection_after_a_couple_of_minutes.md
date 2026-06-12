---
title: "Ubuntu drops connection after a couple of minutes"
date: 2010-12-23
forum: Networking &amp; Wireless
---

### Post by stathisdim on 2010-12-23
I have ubuntu for about a week but I face a serious problem with my Wi-Fi connection as it drops after some minutes (sometimes even after some seconds). My network card is a [SMCWUSBS-N2 EU]("http://www.smc.com/index.cfm?event=viewProduct&localeCode=EN_CZE&cid=5&scid=117&pid=1653").

Here are the results of 
lsusb
```
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 083a:b522 Accton Technology Corp. EZ Connect N Draft 11n Wireless USB2.0 Adapter
Bus 001 Device 002: ID 1058:1021 Western Digital Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```lspci -nn
```
00:00.0 Host bridge [0600]: ATI Technologies Inc RS690 Host Bridge [1002:7910]
00:02.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Graphics Port 0) [1002:7913]
00:07.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3) [1002:7917]
00:12.0 SATA controller [0106]: ATI Technologies Inc SB600 Non-Raid-5 SATA [1002:4380]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI0) [1002:4387]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI1) [1002:4388]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI2) [1002:4389]
00:13.3 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI3) [1002:438a]
00:13.4 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI4) [1002:438b]
00:13.5 USB Controller [0c03]: ATI Technologies Inc SB600 USB Controller (EHCI) [1002:4386]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 14)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB600 IDE [1002:438c]
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB600 PCI to LPC Bridge [1002:438d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:00.0 VGA compatible controller [0300]: nVidia Corporation G84 [GeForce 8600 GT] [10de:0402] (rev a1)
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 01)
03:02.0 Modem [0703]: Motorola SM56 Data Fax Modem [1057:3052] (rev 04)
03:03.0 Multimedia controller [0480]: Philips Semiconductors SAA7130 Video Broadcast Decoder [1131:7130] (rev 01)
03:06.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller [1106:3044] (rev c0)

```lsmod
```
Module                  Size  Used by
nls_utf8                1069  1 
isofs                  30022  1 
aes_i586                7280  0 
aes_generic            26875  1 aes_i586
parport_pc             26058  0 
ppdev                   5556  0 
binfmt_misc             6599  1 
snd_hda_codec_realtek   217980  1 
snd_hda_intel          22107  2 
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
saa7134_alsa           10412  0 
snd_pcm                71475  3 snd_hda_intel,snd_hda_codec,saa7134_alsa
rt2870sta             405890  0 
arc4                    1165  2 
nouveau               516971  2 
snd_seq_midi            4588  0 
ir_lirc_codec           3092  0 
snd_rawmidi            17783  1 snd_seq_midi
lirc_dev                9393  1 ir_lirc_codec
rt2800usb               8367  0 
ir_sony_decoder         1889  0 
snd_seq_midi_event      6047  1 snd_seq_midi
rt2800lib              28897  1 rt2800usb
rt2x00usb               9779  2 rt2800usb,rt2800lib
rt2x00lib              27275  2 rt2800lib,rt2x00usb
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
ttm                    56633  1 nouveau
saa7134               148613  1 saa7134_alsa
led_class               2633  1 rt2x00lib
ir_jvc_decoder          1950  0 
drm_kms_helper         30200  1 nouveau
mac80211              231541  2 rt2x00usb,rt2x00lib
ir_rc6_decoder          2334  0 
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
ir_rc5_decoder          1950  0 
cfg80211              144470  2 rt2x00lib,mac80211
drm                   168054  4 nouveau,ttm,drm_kms_helper
ir_nec_decoder          2014  0 
v4l2_common            17329  1 saa7134
videodev               43098  2 saa7134,v4l2_common
crc_ccitt               1351  2 rt2870sta,rt2800usb
v4l1_compat            13359  1 videodev
videobuf_dma_sg         9806  2 saa7134_alsa,saa7134
snd                    49006  14 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,saa7134_alsa,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videobuf_core          16907  2 saa7134,videobuf_dma_sg
ir_common               5167  1 saa7134
psmouse                59033  0 
ir_core                14654  8 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,saa7134,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,ir_common
tveeprom               11178  1 saa7134
ati_agp                 5202  0 
k8temp                  3132  0 
soundcore                880  1 snd
serio_raw               4022  0 
i2c_piix4               8635  0 
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
i2c_algo_bit            5168  1 nouveau
agpgart                32011  3 ttm,drm,ati_agp
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
usb_storage            40172  1 
floppy                 54311  0 
ahci                   19013  0 
r8169                  36489  0 
firewire_ohci          21106  0 
firewire_core          46643  1 firewire_ohci
crc_itu_t               1383  1 firewire_core
pata_atiixp             3288  1 
mii                     4425  1 r8169
libahci                21667  3 ahci

```sudo iwlist scan
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:24:17:1A:46:B7
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=48 dBm  
                    Encryption key:on
                    ESSID:"ThomsonD8C8BB"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000022a2603189
                    Extra: Last beacon: 1236ms ago
                    IE: Unknown: 000D54686F6D736F6E443843384242
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050402030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD060010180201F0


```

---

### Post by pastalavista on 2010-12-23
Check the output of```
lshw -C network
```and you'll probably see r8169 as your wireless driver (it's listed in your lsmod.. I have the same) so you may be able to restart your wireless with ```
sudo rmmod r8169 && sleep 2 && sudo modprobe r8169
``` and to keep it running longer try editing /etc/NetworkManager/nm-system-settings.conf and change the line ```
[ifupdown]
managed=false (change to managed=true)

```

You can do that in terminal with ```
sudo nano /etc/NetworkManager/nm-system-settings.conf
``` save and log out/ back in

This worked for me.. hope it helps

---

### Post by stathisdim on 2010-12-23
here are the results 
but we have a different driver
```
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:1d:92:32:12:0f
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes
       resources: irq:42 ioport:d800(size=256) memory:feaff000-feafffff memory:feac0000-feadffff
  *-network
       description: Wireless interface
       physical id: 2
       bus info: usb@1:4
       logical name: wlan0
       serial: 00:22:2d:01:9f:02
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=2.6.35-22-generic firmware=N/A ip=192.168.1.65 multicast=yes wireless=IEEE 802.11bgn
```

---

### Post by pastalavista on 2010-12-23
I see, so in that case, to restart the driver module use ```
sudo rmmod rt2800usb && sleep 2 && sudo modprobe rt2800usb
```and try more than 2 seconds sleep if it doesn't work at first

---

### Post by stathisdim on 2010-12-23
I edited nm-system-settings.conf but it didn't help.

---

### Post by pastalavista on 2010-12-23
Did you try installing the Linux driver from the [SMC site]("http://www.smc.com/index.cfm?event=downloads.doSearchCriteria&localeCode=EN_CZE&productCategory=5&modelNumber=1653&partNumber=4193&downloadType=1&knowsPartNumber=false")?

---

### Post by stathisdim on 2010-12-24
no as i don't know how to compile it.

---

### Post by stathisdim on 2010-12-24
well i found a guide about who to compile this driver but when i run: "make" it says there is an error

```
make -C tools
make[1]: Entering directory `/home/stathis/bc/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/stathis/bc/tools'
/home/stathis/bc/tools/bin2h
cp -f os/linux/Makefile.6 /home/stathis/bc/os/linux/Makefile
make  -C  /lib/modules/2.6.35-24-generic/build SUBDIRS=/home/stathis/bc/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-24-generic'
  CC [M]  /home/stathis/bc/os/linux/../../common/rtmp_init.o
  CC [M]  /home/stathis/bc/os/linux/../../os/linux/rt_profile.o
/home/stathis/bc/os/linux/../../os/linux/rt_profile.c: In function ‘RTMPReadParametersHook’:
/home/stathis/bc/os/linux/../../os/linux/rt_profile.c:928: error: ‘struct task_struct’ has no member named ‘fsuid’
/home/stathis/bc/os/linux/../../os/linux/rt_profile.c:929: error: ‘struct task_struct’ has no member named ‘fsgid’
/home/stathis/bc/os/linux/../../os/linux/rt_profile.c:930: error: ‘struct task_struct’ has no member named ‘fsuid’
/home/stathis/bc/os/linux/../../os/linux/rt_profile.c:930: error: ‘struct task_struct’ has no member named ‘fsgid’
/home/stathis/bc/os/linux/../../os/linux/rt_profile.c:1593: error: ‘struct task_struct’ has no member named ‘fsuid’
/home/stathis/bc/os/linux/../../os/linux/rt_profile.c:1594: error: ‘struct task_struct’ has no member named ‘fsgid’
make[2]: *** [/home/stathis/bc/os/linux/../../os/linux/rt_profile.o] Error 1
make[1]: *** [_module_/home/stathis/bc/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-24-generic'
make: *** [LINUX] Error 2

```

---

### Post by pastalavista on 2010-12-24
Make sure you have build-essential installed```
sudo apt-get install build-essential
```then try make again.

---

### Post by stathisdim on 2010-12-24
I have it

---

### Post by stathisdim on 2010-12-26
At last i fixed it using ndiswrapper.

---

