---
title: "Bluetooth discovery problems with Ralink 5390 combo card"
date: 2011-03-09
forum: Networking &amp; Wireless
---

### Post by mrmagos on 2011-03-09
I have an HP dm1z laptop that comes with a Ralink 5390 wifi/bluetooth combo card. I was able to get the wifi part working per this thread: [http://ubuntuforums.org/showthread.php?t=1685430]("http://ubuntuforums.org/showthread.php?t=1685430")
Now, the bluetooth modules load and everything appears to be working, but when I scan for devices, nothing comes up. I've tried pairing with a mouse, a headset and my phone, but none were discovered. I know that the bluetooth card and devices I'm trying to pair with all work, because I can discover and pair with them under Win7.

I've tried:
- unloading the wifi module, restarting bluetooth and scanning
- installing bluez-compat and using the legacy tools
with the same results.

hcidump shows that it's doing stuff when I try to scan, and the syslog shows when discovery starts and stops, so I'm not sure where to go from here.

relevant 'lsusb -v' (yes, it shows up as a USB device...strange)
```
Bus 006 Device 003: ID 148f:2000 Ralink Technology, Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          224 Wireless
  bDeviceSubClass         1 Radio Frequency
  bDeviceProtocol         1 Bluetooth
  bMaxPacketSize0        64
  idVendor           0x148f Ralink Technology, Corp.
  idProduct          0x2000 
  bcdDevice           68.17
  iManufacturer           0 
  iProduct                2 CSR BS8510
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          177
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       1
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0009  1x 9 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0009  1x 9 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       2
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0011  1x 17 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0011  1x 17 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       3
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0019  1x 25 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0019  1x 25 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       4
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0021  1x 33 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0021  1x 33 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       5
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0031  1x 49 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0031  1x 49 bytes
        bInterval               1
Device Status:     0x0001
  Self Powered

```

hciconfig -a
```

hci0:	Type: BR/EDR  Bus: USB
	BD Address: 88:9F:FA:E7:E9:0D  ACL MTU: 310:10  SCO MTU: 64:8
	UP RUNNING PSCAN 
	RX bytes:3341 acl:0 sco:0 events:84 errors:0
	TX bytes:827 acl:0 sco:0 commands:72 errors:0
	Features: 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00
	Packet type: DM1 DH1 HV1 
	Link policy: 
	Link mode: SLAVE ACCEPT 
	Name: 'adumbrali-0'
	Class: 0x4a0100
	Service Classes: Networking, Capturing, Telephony
	Device Class: Computer, Uncategorized
	HCI Version: 3.0 (0x5)  Revision: 0x1aa1
	LMP Version: 3.0 (0x5)  Subversion: 0x1aa1
	Manufacturer: Cambridge Silicon Radio (10)

```

lsmod
```
Module                  Size  Used by
rt5390sta            1051282  1 
hidp                   22572  0 
hid                    91020  1 hidp
rfcomm                 47694  8 
parport_pc             36959  0 
ppdev                  17113  0 
snd_hda_codec_idt      71042  1 
snd_hda_codec_hdmi     28103  1 
snd_hda_intel          33211  2 
snd_hda_codec         103804  3 snd_hda_codec_idt,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96625  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
joydev                 17606  0 
binfmt_misc            17565  1 
snd_seq_midi           13324  0 
radeon                982096  3 
sco                    18131  2 
bnep                   18308  2 
l2cap                  53570  17 hidp,rfcomm,bnep
hp_wmi                 13706  0 
snd_rawmidi            30486  1 snd_seq_midi
sparse_keymap          13898  1 hp_wmi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               68099  0 
snd_timer              29602  2 snd_pcm,snd_seq
psmouse                73535  0 
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
videodev               82052  1 uvcvideo
ttm                    76664  1 radeon
btusb                  18600  2 
v4l2_compat_ioctl32    17078  1 videodev
drm_kms_helper         42136  1 radeon
bluetooth              72448  10 hidp,rfcomm,sco,bnep,l2cap,btusb
snd                    67382  14 snd_hda_codec_idt,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   227573  5 radeon,ttm,drm_kms_helper
serio_raw              13166  0 
k10temp                13119  0 
soundcore              12680  1 snd
sp5100_tco             13707  0 
i2c_piix4              13303  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13400  1 radeon
hp_accel               21880  0 
lis3lv02d              19893  1 hp_accel
video                  19438  0 
input_polldev          14007  1 lis3lv02d
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
usb_storage            53538  0 
uas                    17996  0 
ahci                   25951  3 
libahci                26642  1 ahci
r8169                  48013  0 

```

---

### Post by nefan on 2011-05-04
I have the same problem on my dm1. Have you got any closer to a solution?

---

### Post by XEMD38 on 2011-07-06
With Ralink FAE, we found that the radio is OFF and the following command has to be executed to turn ON the device again: 

***sudo bccmd psset -s 0x0000 0x028c 0x0001***

+ reboot

and after that bluetooth work fine (enable and disable in same time with wifi)


Tested on HP DV7-6090EF (Ralink RT5390 Combo Wifi/bluetooth) Driver ([http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2) ) V2.4.0.4  Ubuntu Natty 11.04 64 bits

Source : [https://bugs.meego.com/show_bug.cgi?id=3498](https://bugs.meego.com/show_bug.cgi?id=3498)

---

### Post by forubu on 2011-07-07
> **XEMD38 said:**
> With Ralink FAE, we found that the radio is OFF and the following command has to be executed to turn ON the device again: 

***sudo bccmd psset -s 0x0000 0x028c 0x0001***

+ reboot

and after that bluetooth work fine (enable and disable in same time with wifi)


Thank you XEMD38 :P
It did wonders on my DV7-5090 too. 
Very helpful post.

---

### Post by Redblade20XX on 2011-07-08
> **XEMD38 said:**
> With Ralink FAE, we found that the radio is OFF and the following command has to be executed to turn ON the device again: 

***sudo bccmd psset -s 0x0000 0x028c 0x0001***

+ reboot

and after that bluetooth work fine (enable and disable in same time with wifi)


Tested on HP DV7-6090EF (Ralink RT5390 Combo Wifi/bluetooth) Driver ([http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2) ) V2.4.0.4  Ubuntu Natty 11.04 64 bits

Source : [https://bugs.meego.com/show_bug.cgi?id=3498](https://bugs.meego.com/show_bug.cgi?id=3498)

I applause you!!! =D> Confirmed fixed with Kubuntu 10.10 64-bit

---

### Post by gruntboyx on 2011-08-22
just to add my 2cents.  I had to enable and disable the wireless once for this solution to work.  After that everything was smooth sailing.

Now the Bluetooth is discoverable.  Thanks for the solutions!

Btw works on 11.10 alpha too.

---

### Post by Imbuks on 2012-09-12
Your solution worked perfectly with 12.04 and rt3090 also. Thank you very much.

---

### Post by pkadeel on 2012-10-16
> **XEMD38 said:**
> With Ralink FAE, we found that the radio is OFF and the following command has to be executed to turn ON the device again: 

***sudo bccmd psset -s 0x0000 0x028c 0x0001***

+ reboot

and after that bluetooth work fine (enable and disable in same time with wifi)


Tested on HP DV7-6090EF (Ralink RT5390 Combo Wifi/bluetooth) Driver ([http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2) ) V2.4.0.4  Ubuntu Natty 11.04 64 bits

Source : [https://bugs.meego.com/show_bug.cgi?id=3498](https://bugs.meego.com/show_bug.cgi?id=3498)
:P Fantastic solution.
Worked on HP-G62 running Kubuntu 12.04.1
Hardware: Ralink RT3090 wifi + Ralink Motorola Bluetooth BC4 combo card
Network controller: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe
Bluetooth:- ID 148f:1000 Ralink Technology, Corp.

Note for Forum Admins: This solution shall be a sticky with a proper title. It took me more than a week to reach this simple solution.

---

