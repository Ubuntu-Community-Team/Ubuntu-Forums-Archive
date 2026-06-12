---
title: "Webcam help for Logitech Clicksmart in Lubuntu 11.10"
date: 2011-11-20
forum: Multimedia Software
---

### Post by dajare on 2011-11-20
Lubuntu has a well-deserved reputation for resurrecting old hardware, and I'm hoping it can even cope with an old Logitech Clicksmart 310.

I **cannot** get it to work as a webcam in Lubuntu 11.10, though. It is readily recognized as a "camera", but I don't want the "camera", but the "webcam". I've done a lot of forum-searching/googling, and it seems to me that the notion that [the camera cabability is "blocking" the webcam recognition]("http://ubuntuforums.org/showpost.php?p=10432450&postcount=6") makes a lot of sense.

I'm not sure what else to do to trouble-shoot, since a lot of the threads addressing this problem are quite old, and some of the commands appear not to work in this up-to-date release.

Some older threads requested information from the lsusb and lsmod commands. Here they are in the hope that it might be relevant:

**lsusb -v**

```
Bus 002 Device 004: ID 046d:0900 Logitech, Inc. ClickSmart 310
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x046d Logitech, Inc.
  idProduct          0x0900 ClickSmart 310
  bcdDevice            0.90
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          167
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
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       1
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0080  1x 128 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       2
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0180  1x 384 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       3
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       4
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0280  1x 640 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       5
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0300  1x 768 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       6
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0380  1x 896 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       7
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x03ff  1x 1023 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
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
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval               8
Device Status:     0x0001
  Self Powered

```

and **lsmod**

```

Module                  Size  Used by
gspca_spca500          17650  0 
gspca_main             27610  1 gspca_spca500
videodev               85626  1 gspca_main
snd_seq_dummy          12686  0 
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  8 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
joydev                 17393  0 
snd_hda_codec_realtek   254125  1 
snd_hda_codec_si3054    12864  1 
snd_hda_intel          24262  2 
snd_hda_codec          91754  3 snd_hda_codec_realtek,snd_hda_codec_si3054,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  3 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
arc4                   12473  2 
radeon                925020  2 
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
pcmcia                 39822  0 
snd_seq                51567  3 snd_seq_dummy,snd_seq_midi,snd_seq_midi_event
ath5k                 145100  0 
ath                    19387  1 ath5k
mac80211              272785  1 ath5k
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  4 snd_seq_dummy,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73673  0 
cfg80211              172392  3 ath5k,ath,mac80211
snd                    55902  14 snd_hda_codec_realtek,snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              12990  0 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
soundcore              12600  1 snd
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
ttm                    65224  1 radeon
i2c_piix4              13093  0 
drm_kms_helper         32889  1 radeon
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
drm                   192226  4 radeon,ttm,drm_kms_helper
binfmt_misc            17292  1 
i2c_algo_bit           13199  1 radeon
shpchp                 32356  0 
ati_agp                13242  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
firewire_ohci          35854  0 
8139too                23283  0 
firewire_core          56937  1 firewire_ohci
hid                    77367  1 usbhid
crc_itu_t              12627  1 firewire_core
8139cp                 22636  0 
pata_atiixp            12967  0 
sata_sil               13278  2 

```

It would be great to be able to use this little device as a webcam. Hope there's some help out there! Thanks!

---

### Post by jontheid on 2011-11-20
How about trying changing the 'volume management' settings under 'preferences' in the file manager menu.
If you uncheck 'mount removable media automatically' then it may not get mounted as a camera and you may be able to use it as a webcam.

Just a guess, I am a bit of a newb too, but it is non-destructive and easily reversible.

Jon

---

### Post by dajare on 2011-11-20
> **jontheid said:**
> How about trying changing the 'volume management' settings under 'preferences' in the file manager menu.
... it is non-destructive and easily reversible.

Good idea, and thanks for it, but sadly doesn't help. In fact, it doesn't seem to make any difference at all! It still comes up in PCManFM as a camera, "046d 0900", and "gphoto2://[usb:002,00n]/" when I click on it. I just don't get any options; but "Show available options" has the same effect. Weird.

I tried stopping the "gvfs-gphoto2-volume-monitor" as suggested in another thread, but that not only prevents the device from being recognized, it also prevents [Cheese]("http://projects.gnome.org/cheese/") from opening.

Any other ideas?

---

### Post by no2498 on 2011-11-21
with my dv cam i need to set the cam to live mode on the back of the cam as it comes on
hope this helps

---

### Post by dajare on 2011-11-21
> **no2498 said:**
> with my dv cam i need to set the cam to live mode on the back of the cam as it comes on
hope this helps

@no2498 - thanks for this. I had hopes too ... alas, unfulfilled! I checked, and when connected the little screen on the back of the Clicksmart says "PC", and that's that.

I've tried other combinations of plugging in, before/after booting, launching Cheese, etc. But the result is always the same.

Strangely, I think when I first put this machine on to Ubuntu 9.04, I had this device work as a webcam with Cheese. I cannot remember how, or find whatever instructions allowed that to work, and latterly even on 9.04 it had stopped working but I didn't try fixing it then. Now with Lubuntu, though, I was hoping it would come good. I'm still hoping!

---

### Post by no2498 on 2011-11-22
? do you have a memory card in it take it out if yes
you may need to set the mode wile its not plugged in to the computer

---

