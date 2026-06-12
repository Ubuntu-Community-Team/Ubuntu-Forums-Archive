---
title: "Hardwire to USB"
date: 2011-10-10
forum: Networking &amp; Wireless
---

### Post by rickggreen on 2011-10-10
I have been running a machine that has been hardwired to the router that I have moved into another room and want to run wireless with a dlink DWA-130 usb stick. What do I have to do to get it to ignore the build in lan and see the usb stick instead? It is working in windows 7 without a hiccup.

---

### Post by praseodym on 2011-10-10
Hi,

please show the outputs of

```
lspci -nnk | grep -iA2 net
lsusb
lsmod
```

---

### Post by rickggreen on 2011-10-11
```
rick@rick-desktop:~$ lspci -nnk | grep -iA2 net
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
	Subsystem: ASRock Incorporation Motherboard (one of many) [1849:8168]
	Kernel driver in use: r8169
rick@rick-desktop:~$ 
rick@rick-desktop:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 1038:0777 Ideazon, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 046d:c227 Logitech, Inc. G15 Refresh Keyboard
Bus 003 Device 003: ID 046d:c226 Logitech, Inc. G15 Refresh Keyboard
Bus 003 Device 002: ID 046d:c223 Logitech, Inc. G11/G15 Keyboard / USB Hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 2001:3301 D-Link Corp. DWA-130 802.11n Wireless N Adapter(rev.C1) [Realtek RTL8192U]
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 4971:ce17 SimpleTech 1TB SimpleDrive II USB External Hard Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
rick@rick-desktop:~$ 
rick@rick-desktop:~$ lsmod
Module                  Size  Used by
binfmt_misc            17565  1 
vesafb                 13761  1 
snd_hda_codec_realtek   336693  1 
mt2131                 13387  1 
s5h1409                18754  1 
r8192u_usb            324806  0 
ppdev                  17113  0 
ir_lirc_codec          12898  0 
lirc_dev               19232  1 ir_lirc_codec
ir_sony_decoder        12549  0 
nvidia              10709116  40 
snd_hda_intel          33211  2 
snd_hda_codec         103804  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96625  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29602  2 snd_pcm,snd_seq
cx23885               142382  0 
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
ir_jvc_decoder         12546  0 
ir_rc6_decoder         12546  0 
snd                    67382  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ir_rc5_decoder         12546  0 
ir_nec_decoder         12546  0 
rc_core                26918  7 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx23885
edac_core              53845  0 
edac_mce_amd           23464  0 
cx2341x                28272  1 cx23885
psmouse                73535  0 
videobuf_dma_sg        19307  1 cx23885
videobuf_dvb           14147  1 cx23885
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
sp5100_tco             13744  0 
k10temp                13119  0 
serio_raw              13166  0 
dvb_core              110487  2 cx23885,videobuf_dvb
i2c_piix4              13303  0 
parport_pc             36959  1 
videobuf_core          26135  3 cx23885,videobuf_dma_sg,videobuf_dvb
v4l2_common            17647  2 cx23885,cx2341x
videodev               82052  3 cx23885,cx2341x,v4l2_common
v4l2_compat_ioctl32    17078  1 videodev
btcx_risc              13640  1 cx23885
tveeprom               21249  1 cx23885
lp                     17825  0 
parport                46458  3 ppdev,parport_pc,lp
usbhid                 46956  0 
hid                    91020  1 usbhid
usb_storage            53538  1 
uas                    17996  0 
ahci                   25951  5 
r8169                  48022  0 
libahci                26642  1 ahci
pata_atiixp            13165  0 
rick@rick-desktop:~$ 
rick@rick-desktop:~$
```

---

### Post by praseodym on 2011-10-11
Ok, check additionally:

```
dmesg | grep r8
rfkill list
iwconfig
```
You may want to update the driver from the Realtek-HP:

[http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

Driver RTL8192CU Version 3.1.2590. Unpack it to /home, change the directory and install it:

```
sudo apt-get install linux-headers-$(uname -r) build-essential
cd foldername/
sudo chmod +x install.sh
sudo ./install.sh
```
Reboot and check:

```
uname -a
iwconfig
lsmod
sudo iwlist scan
dmesg | grep 8192
```
If you have problems with LAN, too, install the "right" driver r8168 instead of r8169, description here:

[http://forum.ubuntuusers.de/topic/lan-karte-funktioniert-nicht/#post-3005217](http://forum.ubuntuusers.de/topic/lan-karte-funktioniert-nicht/#post-3005217)

---

### Post by rickggreen on 2011-10-11
I must have done something wrong


rick@rick-desktop:~$ uname -a
Linux rick-desktop 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
rick@rick-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g/n  Mode:Managed  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

rick@rick-desktop:~$ lsmod
Module                  Size  Used by
binfmt_misc            17565  1 
vesafb                 13761  1 
snd_hda_codec_realtek   336693  1 
mt2131                 13387  1 
s5h1409                18754  1 
sp5100_tco             13744  0 
usbhid                 46956  0 
hid                    91020  1 usbhid
snd_hda_intel          33211  2 
snd_hda_codec         103804  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96625  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
ir_lirc_codec          12898  0 
lirc_dev               19232  1 ir_lirc_codec
snd_seq_midi_event     14899  1 snd_seq_midi
ir_sony_decoder        12549  0 
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
ir_jvc_decoder         12546  0 
r8192u_usb            324806  0 
ir_rc6_decoder         12546  0 
ir_rc5_decoder         12546  0 
ppdev                  17113  0 
cx23885               142382  0 
ir_nec_decoder         12546  0 
rc_core                26918  7 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx23885
cx2341x                28272  1 cx23885
videobuf_dma_sg        19307  1 cx23885
videobuf_dvb           14147  1 cx23885
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    67382  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73535  0 
edac_core              53845  0 
soundcore              12680  1 snd
nvidia              10709116  40 
serio_raw              13166  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
k10temp                13119  0 
edac_mce_amd           23464  0 
i2c_piix4              13303  0 
dvb_core              110487  2 cx23885,videobuf_dvb
parport_pc             36959  1 
videobuf_core          26135  3 cx23885,videobuf_dma_sg,videobuf_dvb
v4l2_common            17647  2 cx23885,cx2341x
videodev               82052  3 cx23885,cx2341x,v4l2_common
v4l2_compat_ioctl32    17078  1 videodev
btcx_risc              13640  1 cx23885
tveeprom               21249  1 cx23885
lp                     17825  0 
parport                46458  3 ppdev,parport_pc,lp
usb_storage            53538  1 
uas                    17996  0 
pata_atiixp            13165  0 
ahci                   25951  3 
libahci                26642  1 ahci
r8169                  48022  0 
rick@rick-desktop:~$ sudo iwlist scan
[sudo] password for rick: 
Sorry, try again.
[sudo] password for rick: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

rick@rick-desktop:~$

---

### Post by praseodym on 2011-10-11
Check:

```
modinfo 8192cu
dmesg | grep 81
rfkill list
```

---

