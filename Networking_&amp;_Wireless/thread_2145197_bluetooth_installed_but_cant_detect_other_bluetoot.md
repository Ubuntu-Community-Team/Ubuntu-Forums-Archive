---
title: "bluetooth installed but cant detect other bluetooth devices"
date: 2013-05-14
forum: Networking &amp; Wireless
---

### Post by tilakrajsingh on 2013-05-14
I have installed bluetooth driver but it is not able to pair with other devices. It cant search for other devices.
  OUTPUT of "lspci"
```


00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09) 00:01.0 PCI bridge: Intel Corporation Ivy Bridge PCI Express Root Port (rev 09) 00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09) 00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04) 00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04) 00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04) 00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04) 00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4) 00:1c.4 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 5 (rev c4) 00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04) 00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04) 00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04) 00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04) 01:00.0 VGA compatible controller: NVIDIA Corporation Device 0de9 (rev ff) 02:00.0 Network controller: Broadcom Corporation Device 4365 (rev 01) 03:00.0 Ethernet controller: Atheros Communications Inc. AR8162 Fast Ethernet (rev 10)
```

output of "dmesg | grep Bluetooth"

```

[   15.744190] Bluetooth: Core ver 2.16 [   15.744212] Bluetooth: HCI device and connection manager initialized [   15.744218] Bluetooth: HCI socket layer initialized [   15.744220] Bluetooth: L2CAP socket layer initialized [   15.744225] Bluetooth: SCO socket layer initialized [   15.744503] Bluetooth: Generic Bluetooth USB driver ver 0.6 [   16.050311] Bluetooth: BNEP (Ethernet Emulation) ver 1.3 [   16.050314] Bluetooth: BNEP filters: protocol multicast [   16.054600] Bluetooth: RFCOMM TTY layer initialized [   16.054605] Bluetooth: RFCOMM socket layer initialized [   16.054607] Bluetooth: RFCOMM ver 1.11 [   16.750642] Bluetooth: hci0 command tx timeout [   17.156673] Bluetooth: can't load firmware, may not work correctly
```

i installed linux-firmware-nonfree but that doesnt help...I think the  problem lies in the last two lines of the output of dmesg...Please help

---

### Post by praseodym on 2013-05-14
Did you install:

```
sudo apt-get install bluez-utils  libopenobex1 bluez-gnome 
sudo service bluetooth restart 
```

Check also:
```

lsusb
lsmod
hciconfig --all 

```
Which Ubuntu version is it?

---

### Post by tilakrajsingh on 2013-05-14
> **praseodym said:**
> Did you install:

```
sudo apt-get install bluez-utils  libopenobex1 bluez-gnome 
sudo service bluetooth restart 
```

Check also:
```

lsusb
lsmod
hciconfig --all 

```
Which Ubuntu version is it?

bluez-gnome gives the following error message > Package bluez-gnome is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source



installed other packages but still not working

lsusb gives ```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 12d1:140b Huawei Technologies Co., Ltd. EC1260 Wireless Data Modem HSD USB Card
Bus 003 Device 003: ID 0461:4dfa Primax Electronics, Ltd 
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 0c45:648d Microdia 
Bus 002 Device 003: ID 0a5c:21d7 Broadcom Corp.
```

lsmod gives

```
Module                  Size  Used by
ppp_deflate            12878  0 
zlib_deflate           26622  1 ppp_deflate
bsd_comp               12842  0 
ppp_async              17307  1 
crc_ccitt              12627  1 ppp_async
bbswitch               13347  0 
snd_hda_codec_hdmi     31775  1 
snd_hda_codec_conexant    52521  1 
parport_pc             32114  0 
ppdev                  12849  0 
rfcomm                 38139  12 
bnep                   17830  2 
binfmt_misc            17292  1 
rts5139               279659  0 
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
snd_hda_intel          32719  3 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
joydev                 17393  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
lib80211_crypt_tkip    17275  0 
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
dell_laptop            17767  0 
dcdbas                 14098  1 dell_laptop
btusb                  17948  2 
bluetooth             158479  23 rfcomm,bnep,btusb
option                 25756  3 
usb_wwan               19779  1 option
usbserial              37173  9 option,usb_wwan
wl                   2906597  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                86520  0 
serio_raw              13027  0 
snd                    62218  16 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  423549  3 
alx                    71673  0 
cfg80211              178877  1 wl
lib80211               14040  2 lib80211_crypt_tkip,wl
mei                    36570  0 
soundcore              14635  1 snd
drm_kms_helper         45466  1 i915
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
drm                   197641  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
wmi                    18744  1 dell_wmi
video                  19115  1 i915
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41937  0 
hid                    77428  1 usbhid
usb_storage            39683  0 

```

and hciconfig --all gives

```
hci0:    Type: BR/EDR  Bus: USB
    BD Address: E0:06:E6:D6:52:9E  ACL MTU: 1021:8  SCO MTU: 64:1
    UP RUNNING PSCAN ISCAN 
    RX bytes:2043 acl:0 sco:0 events:90 errors:0
    TX bytes:1368 acl:0 sco:0 commands:82 errors:0
    Features: 0xff 0xfe 0xcf 0xfe 0xdb 0xff 0x7b 0x87
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
    Link policy: RSWITCH HOLD SNIFF 
    Link mode: SLAVE ACCEPT 
    Name: 'Marty-0'
    Class: 0x6e0100
    Service Classes: Networking, Rendering, Capturing, Audio, Telephony
    Device Class: Computer, Uncategorized
    HCI Version: 4.0 (0x6)  Revision: 0x0
    LMP Version: 4.0 (0x6)  Subversion: 0x210b
    Manufacturer: Broadcom Corporation (15)


```

its ubuntu 12.04 LTS

---

### Post by praseodym on 2013-05-14
[http://askubuntu.com/questions/217590/dell-vostro-3560-bluetooth-doesnt-work](http://askubuntu.com/questions/217590/dell-vostro-3560-bluetooth-doesnt-work)

Check this one according to 12.04

---

### Post by tilakrajsingh on 2013-05-14
yeah i did check that out but the package listed there is for 64 bit. I am using 32bit ubuntu

---

### Post by praseodym on 2013-05-14
Check on the CD in the folder ~/pool/main/b

---

### Post by tilakrajsingh on 2013-05-14
nope still not working....dmesg displays same output for bluetooth

it used to work before but then i had to reinstall ubuntu due to some reason...i reinstalled the drivers and then it stopped working...maybe i installed wrong driver for wireless?????

---

