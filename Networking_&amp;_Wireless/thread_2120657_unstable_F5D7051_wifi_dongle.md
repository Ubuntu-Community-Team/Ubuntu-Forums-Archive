---
title: "unstable F5D7051 wifi dongle"
date: 2013-02-27
forum: Networking &amp; Wireless
---

### Post by sailah on 2013-02-27
Yello,

I have posted this on mint forum, but no reply yet so I hope for some more audience.

I am running 64bit Mint 13 (3.2.0-23-generic) & 14, on both the same symptoms. Presume the same would be on ubuntu since the guts are the same.

```
CPU~Dual core Intel Core2 CPU 6600 (-MCP-) clocked at 1596.000 Mhz Kernel~3.5.0-17-generic x86_64 Up~1 min Mem~986.7/2002.6MB HDD~320.1GB(1.7% used) Procs~168 Client~Shell inxi~1.8.4
```I have Belqin (F5D7051) wifi dongle based on broadcom 4320 chip that works randomly after booting machine. I believe the proper driver is rndis_wlan. My suggestion is udevd loads modules asynchronously and therefore this russian roulette behaviour depending on what loads first. Perhaps blacklisting something would help. Please give me some advice where to start? When it loads correctly it works perfectly so the solution should be simple and strightforward !?

lsusb -v (when WIFI)

```
Bus 001 Device 003: ID 050d:7051 Belkin Components F5D7051 802.11g Adapter v1000 [Broadcom 4320 USB]
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            2 Communications
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x050d Belkin Components
  idProduct          0x7051 F5D7051 802.11g Adapter v1000 [Broadcom 4320 USB]
  bcdDevice            0.06
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           48
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         2 Communications
      bInterfaceSubClass      2 Abstract (modem)
      bInterfaceProtocol    255 Vendor Specific (MSFT RNDIS?)
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
        bInterval               4
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
```When no WIFI present than lsusb -v hangs at some stage. lsusb alone still works:

```
Bus 001 Device 003: ID 050d:7051 Belkin Components F5D7051 802.11g Adapter v1000 [Broadcom 4320 USB]
```lsmod (WIFI):

```
Module                  Size  Used by
snd_hda_codec_analog    97987  1 
joydev                 17693  0 
snd_usb_audio         122982  1 
bnep                   18281  2 
snd_usbmidi_lib        25395  1 snd_usb_audio
rfcomm                 47604  0 
bluetooth             180104  10 bnep,rfcomm
parport_pc             32866  0 
ppdev                  17113  0 
snd_hda_intel          33773  2 
snd_hda_codec         127706  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep              13668  2 snd_usb_audio,snd_hda_codec
snd_pcm                97188  3 snd_usb_audio,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
rt2500usb              27294  0 
rt2x00usb              20762  1 rt2500usb
rt2x00lib              55301  2 rt2500usb,rt2x00usb
snd_seq_midi_event     14899  1 snd_seq_midi
usbhid                 47199  0 
snd_rawmidi            30748  2 snd_usbmidi_lib,snd_seq_midi
binfmt_misc            17540  1 
rndis_wlan             37554  0 
mac80211              506816  2 rt2x00usb,rt2x00lib
hid                    99559  1 usbhid
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
cfg80211              205544  3 rt2x00lib,rndis_wlan,mac80211
v4l2_compat_ioctl32    17128  1 videodev
psmouse                87603  0 
serio_raw              13211  0 
rndis_host             13848  1 rndis_wlan
cdc_ether              13536  1 rndis_host
usbnet                 26212  3 rndis_wlan,rndis_host,cdc_ether
snd_timer              29990  2 snd_pcm,snd_seq
nouveau               774571  3 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
ttm                    76949  1 nouveau
drm_kms_helper         46978  1 nouveau
drm                   242038  5 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13423  1 nouveau
mxm_wmi                12979  1 nouveau
wmi                    19256  1 mxm_wmi
video                  19596  1 nouveau
asus_atk0110           18078  0 
mac_hid                13253  0 
snd                    78855  17 snd_hda_codec_analog,snd_usb_audio,snd_usbmidi_lib,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usb_storage            49198  0 
uas                    18027  0 
firewire_ohci          41000  0 
firewire_core          63558  1 firewire_ohci
skge                   49902  0 
crc_itu_t              12707  1 firewire_core
sky2                   59043  0 
pata_jmicron           12747  0
```lsmod (no WIFI):

```
Module                  Size  Used by
bnep                   18281  2 
rfcomm                 47604  0 
bluetooth             180104  10 bnep,rfcomm
snd_hda_codec_analog    97987  1 
parport_pc             32866  0 
ppdev                  17113  0 
snd_usb_audio         122982  1 
snd_usbmidi_lib        25395  1 snd_usb_audio
snd_hda_intel          33773  2 
snd_hda_codec         127706  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep              13668  2 snd_usb_audio,snd_hda_codec
snd_pcm                97188  3 snd_usb_audio,snd_hda_intel,snd_hda_codec
binfmt_misc            17540  1 
joydev                 17693  0 
snd_seq_midi           13324  0 
snd_rawmidi            30748  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
rndis_wlan             51461  1 
mac_hid                13253  0 
asus_atk0110           18078  0 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  17 snd_hda_codec_analog,snd_usb_audio,snd_usbmidi_lib,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                87603  0 
rt2500usb              38364  1 
rt2x00usb              20762  1 rt2500usb
rt2x00lib              55301  2 rt2500usb,rt2x00usb
mac80211              506816  2 rt2x00usb,rt2x00lib
nouveau               774571  3 
ttm                    76949  1 nouveau
drm_kms_helper         46978  1 nouveau
drm                   242038  5 nouveau,ttm,drm_kms_helper
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
rndis_host             13848  1 rndis_wlan
cdc_ether              13536  1 rndis_host
usbnet                 26212  3 rndis_wlan,rndis_host,cdc_ether
cfg80211              205544  3 rndis_wlan,rt2x00lib,mac80211
i2c_algo_bit           13423  1 nouveau
mxm_wmi                12979  1 nouveau
wmi                    19256  1 mxm_wmi
video                  19596  1 nouveau
soundcore              15091  1 snd
usbhid                 47199  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
v4l2_compat_ioctl32    17128  1 videodev
serio_raw              13211  0 
hid                    99559  1 usbhid
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usb_storage            49198  0 
firewire_ohci          41000  0 
firewire_core          63558  1 firewire_ohci
skge                   49902  0 
crc_itu_t              12707  1 firewire_core
pata_jmicron           12747  0 
sky2                   59043  0
```The difference I see is that module rt2500usb is 'used by':
1 (no WIFI)
0 (WIFI)

Am I right to think that it means that when no WIFI present rt2500usb is used by deamon (according to /etc/passwd) presumably udevd? And it shouldn't be so has to be blacklisted?? Or do I have it completely wrong?


Also when no WIFI present than /var/log/syslog is being updated every second with 2 udevd timeout messages:

```
Feb 24 11:32:34 JUPITER udevd[336]: timeout: killing '/sbin/modprobe -bv usb:v050Dp7051d0006dc02dsc00dp00ic02isc02ipFF' [421]
Feb 24 11:32:34 JUPITER udevd[337]: timeout: killing '/sbin/modprobe -bv usb:v050Dp7051d0006dc02dsc00dp00ic0Aisc00ip00' [422]
Feb 24 11:32:35 JUPITER udevd[336]: timeout: killing '/sbin/modprobe -bv usb:v050Dp7051d0006dc02dsc00dp00ic02isc02ipFF' [421]
Feb 24 11:32:35 JUPITER udevd[337]: timeout: killing '/sbin/modprobe -bv usb:v050Dp7051d0006dc02dsc00dp00ic0Aisc00ip00' [422]
Feb 24 11:32:36 JUPITER udevd[337]: timeout: killing '/sbin/modprobe -bv usb:v050Dp7051d0006dc02dsc00dp00ic0Aisc00ip00' [422]
Feb 24 11:32:36 JUPITER udevd[336]: timeout: killing '/sbin/modprobe -bv usb:v050Dp7051d0006dc02dsc00dp00ic02isc02ipFF' [421]
```

---

### Post by chili555 on 2013-02-27
Please see: [http://srchea.com/blog/2012/04/set-up-belkin-f5d7051-on-ubuntu/](http://srchea.com/blog/2012/04/set-up-belkin-f5d7051-on-ubuntu/)> If you see both modules: rt2500usb and rndis_wlan, edit the /etc/modprobe.d/blacklist.conf and add the following line at the end of the file ```
blacklist rt2500usb
```> Am I right to think that it means that when no WIFI present rt2500usb is used by deamon (according to /etc/passwd) presumably udevd? And it shouldn't be so has to be blacklisted??Exactly.

I suggest you undertake the blacklist, reboot and post back if it's not perfect.

---

### Post by varunendra on 2013-02-27
Beaten by the master, now watching with interest :D.

---

### Post by sailah on 2013-02-27
Guys,

Strange I didn't try it myslef. Actually I did try, but I went over the top (being influenced by some posts) and blacklisted two other rt... modules which must be needed than. Maybe I also blacklisted in a wrong place - don't remember.

So seems to be cured. Hope it will be usefull for some other poor souls out there.

Cheers.

---

### Post by chili555 on 2013-02-27
Glad it's working. Please use thread tools at the top to mark Solved. The searchers will appreciate it.

---

### Post by sailah on 2013-02-27
believe I did it already.. :)

---

### Post by chili555 on 2013-02-27
> **sailah said:**
> believe I did it already.. :)
Yep. Thanks.

---

