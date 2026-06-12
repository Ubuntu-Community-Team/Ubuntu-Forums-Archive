---
title: "Dell Inspirion 1520: No network devices detected"
date: 2013-06-13
forum: Networking &amp; Wireless
---

### Post by GrouchyGaijin on 2013-06-13
Hi Guys,

I have a Dell Inspirion 1520.  It was running 12.04 and connecting fine.
I mucked it up a bit and thought I'd reinstall.
I downloaded 12.04-2 32bit and installed that, removing everything else.

The Live CD (maybe it was a DVD) connected just fine.
After installation was done I had no wifi and no ethernet.
Ubuntu doesn't think I have any network devices.

I installed Linux Mint 15 and the ethernet worked.
I installed Lbuntu 13.04 and the ethernet worked.
I installed Ubuntu 13.04 and again no network devices available.

Does anyone have an idea of how I can fix this?

I can use Mint 15 or Lbuntu but would much rather use Ubuntu.

---

### Post by chili555 on 2013-06-13
Please open a terminal and run and post:```
lspci -nn | grep -e 0200 -e 0280
```Thanks.

---

### Post by GrouchyGaijin on 2013-06-13
Here it is.  It took me a bit of time to reboot and login to Mint:

```


lspci -nn | grep -e 0200 -e 0280
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)


```

I know the wireless has been flaky on Dells running Ubuntu for a couple of years now.  This is the first time my ethernet card hasn't worked.
Thank you, I appreciate the help!

---

### Post by chili555 on 2013-06-13
Please do:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo modprobe b44
```At this point, your ethernet should be working; if so, continue:```
sudo apt-get install linux-firmware-nonfree
sudo modprobe -r b43 && sudo modprobe b43
```And now both should be working.> I know the wireless has been flaky on Dells running Ubuntu for a couple of years now. I think it's a problem with jockey-gtk, also known as Additional Drivers. It merrily offers to install the *wrong driver* for many Broadcom devices and then humans have to undo the harm.

---

### Post by GrouchyGaijin on 2013-06-13
```

sudo modprobe b44

```

Doesn't do anything.  The cursor blinks for a bit then sits there.
I went and had dinner and came back to check - no change.  Just a terminal with a cursor, not even a $

---

### Post by chili555 on 2013-06-13
Go ahead and close the terminal. Reboot, open a new one and show us:```
lsmod
dmesg | grep b4
ifconfig
```These are all diagnostic and don't do anything but gather information.

Thanks.

---

### Post by GrouchyGaijin on 2013-06-13
Before I saw your message I closed the terminal and rebooted.
(Actually I attempted to restart and the machine would not do that - so I held in the power button until it shut down)
When I rebooted I had ethernet - cool.

Now I'll try the rest of your commands for the wifi.

Here is the output you asked for:

```


$ lsmod
Module                  Size  Used by
parport_pc             27504  0 
ppdev                  12817  0 
bnep                   17669  2 
rfcomm                 37420  0 
bluetooth             202069  10 bnep,rfcomm
uvcvideo               71279  0 
videobuf2_vmalloc      12920  1 uvcvideo
videobuf2_memops       13042  1 videobuf2_vmalloc
videobuf2_core         39161  1 uvcvideo
snd_usb_audio         114886  2 
videodev               95806  2 uvcvideo,videobuf2_core
nouveau               834513  3 
snd_usbmidi_lib        24210  1 snd_usb_audio
snd_hda_codec_idt      63896  1 
b43                   351918  0 
snd_hda_intel          38307  3 
r852                   17873  0 
snd_hda_codec         117580  2 snd_hda_codec_idt,snd_hda_intel
sm_common              16772  1 r852
joydev                 17097  0 
nand                   49670  2 r852,sm_common
coretemp               13131  0 
mxm_wmi                12893  1 nouveau
snd_hwdep              13272  2 snd_usb_audio,snd_hda_codec
nand_ecc               13105  1 nand
ttm                    71289  1 nouveau
snd_pcm                80890  3 snd_usb_audio,snd_hda_codec,snd_hda_intel
nand_bch               13003  1 nand
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
bch                    17226  1 nand_bch
drm_kms_helper         47545  1 nouveau
bcma                   39645  1 b43
mac80211              526519  1 b43
nand_ids                8547  1 nand
drm                   228750  5 ttm,drm_kms_helper,nouveau
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25114  2 snd_usbmidi_lib,snd_seq_midi
mtd                    38922  2 nand,sm_common
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
r592                   17707  0 
i2c_algo_bit           13197  1 nouveau
psmouse                81038  0 
gpio_ich               13236  0 
microcode              18286  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
dell_laptop            17161  0 
dell_wmi               12601  0 
lpc_ich                16925  0 
memstick               15842  1 r592
mac_hid                13037  0 
serio_raw              13031  0 
sparse_keymap          13658  1 dell_wmi
dcdbas                 14021  1 dell_laptop
snd_timer              24411  2 snd_pcm,snd_seq
cfg80211              436177  2 b43,mac80211
snd                    56485  21 snd_usb_audio,snd_hwdep,snd_timer,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device
ssb_hcd                12749  0 
soundcore              12600  1 snd
wmi                    18590  3 dell_wmi,mxm_wmi,nouveau
video                  18894  1 nouveau
lp                     13299  0 
parport                40753  3 lp,ppdev,parport_pc
hid_generic            12484  0 
firewire_ohci          35292  0 
b44                    31137  0 
sdhci_pci              18158  0 
sdhci                  31824  1 sdhci_pci
firewire_core          61718  1 firewire_ohci
usbhid                 41805  0 
crc_itu_t              12627  1 firewire_core
hid                    82666  2 hid_generic,usbhid
usb_storage            47684  1 
ssb                    50628  3 b43,b44,ssb_hcd
john@U13:~$ dmesg | grep b4
[    1.001262] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    1.001267] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.001270] usb usb4: Product: UHCI Host Controller
[    1.001274] usb usb4: Manufacturer: Linux 3.8.0-19-generic uhci_hcd
[    1.001278] usb usb4: SerialNumber: 0000:00:1a.1
[    2.676308] b44: Broadcom 44xx/47xx 10/100 PCI ethernet driver version 2.0
[    2.698799] b44 ssb1:0 eth0: Broadcom 44xx/47xx 10/100 PCI ethernet driver 00:19:b9:84:0d:da
[   11.770972] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[   11.816052] b43-phy0: Found PHY: Analog 4, Type 2 (G), Revision 8
[   11.851740] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   11.851815] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   11.851887] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   24.816216] b44 ssb1:0 eth1: Link is up at 100 Mbps, full duplex
[   24.816225] b44 ssb1:0 eth1: Flow control is off for TX and off for RX
john@U13:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:19:b9:84:0d:da  
          inet addr:85.89.91.106  Bcast:85.89.91.255  Mask:255.255.252.0
          inet6 addr: fe80::219:b9ff:fe84:dda/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3309 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2319 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4337652 (4.3 MB)  TX bytes:249837 (249.8 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:226 errors:0 dropped:0 overruns:0 frame:0
          TX packets:226 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:27036 (27.0 KB)  TX bytes:27036 (27.0 KB)







```

---

### Post by chili555 on 2013-06-13
It looks like your ethernet is working beautifully, yes? Please proceed to the next step:```
sudo apt-get install linux-firmware-nonfree
sudo modprobe -r b43 && sudo modprobe b43
```

---

### Post by GrouchyGaijin on 2013-06-13
Thank you so much!

My system is working both with ethernet and wifi again.

I _**really**_&#8203; appreciate the help!

---

### Post by chili555 on 2013-06-13
Awesome! Glad it's working.

---

### Post by victormar on 2013-07-12
and really worked for me after a long day of digging :)) thanks man!

---

