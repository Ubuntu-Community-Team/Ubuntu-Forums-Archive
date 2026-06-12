---
title: "Leadtek Winfast DTV2000DS Not Working in Mythbuntu 11.04"
date: 2011-09-27
forum: Mythbuntu
---

### Post by daveshep on 2011-09-27
Gday, I've been battling with this for weeks and about to buy Windows 7... 

I'm running Mythbuntu 11.04 (2.6.38-11 kernel) and recently bought a Leadtek Winfast DTV2000DS PCI dual tuner card. It's supposed to work out-of-the-box but mine just doesn't... I've tried the card in a Windows 7 Media PC and it worked sweet as, so I know there's nothing wrong with the hardware...

So the relevant section from lsusb is

$lsusb

```
Bus 006 Device 002: ID 0413:6a04 Leadtek Research, Inc.
```

and with more detail

$sudo lsusb -v -s 006:002

```
Bus 006 Device 002: ID 0413:6a04 Leadtek Research, Inc.
Device Descriptor:
   bLength                18
   bDescriptorType         1
   bcdUSB               2.00
   bDeviceClass            0 (Defined at Interface level)
   bDeviceSubClass         0
   bDeviceProtocol         0
   bMaxPacketSize0        64
   idVendor           0x0413 Leadtek Research, Inc.
   idProduct          0x6a04
   bcdDevice            2.00
   iManufacturer           1
   iProduct                2
   iSerial                 0
   bNumConfigurations      1
   Configuration Descriptor:
     bLength                 9
     bDescriptorType         2
     wTotalLength           46
     bNumInterfaces          1
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
       bNumEndpoints           4
       bInterfaceClass       255 Vendor Specific Class
       bInterfaceSubClass      0
       bInterfaceProtocol      0
       iInterface              0
       Endpoint Descriptor:
         bLength                 7
         bDescriptorType         5
         bEndpointAddress     0x81  EP 1 IN
         bmAttributes            2
           Transfer Type            Bulk
           Synch Type               None
           Usage Type               Data
         wMaxPacketSize     0x0040  1x 64 bytes
         bInterval               0
       Endpoint Descriptor:
         bLength                 7
         bDescriptorType         5
         bEndpointAddress     0x02  EP 2 OUT
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
         bmAttributes            2
           Transfer Type            Bulk
           Synch Type               None
           Usage Type               Data
         wMaxPacketSize     0x0040  1x 64 bytes
         bInterval               0
       Endpoint Descriptor:
         bLength                 7
         bDescriptorType         5
         bEndpointAddress     0x85  EP 5 IN
         bmAttributes            2
           Transfer Type            Bulk
           Synch Type               None
           Usage Type               Data
         wMaxPacketSize     0x0040  1x 64 bytes
         bInterval               0
Device Status:     0x0000
   (Bus Powered)

```

The relevant section from dmesg is

$dmesg

```
[   84.230061] usb 6-1: new full speed USB device using uhci_hcd and address 2
[   99.085019] IR NEC protocol handler initialized
[   99.100323] IR RC5(x) protocol handler initialized
[   99.104296] IR RC6 protocol handler initialized
[   99.107529] IR JVC protocol handler initialized
[   99.110847] IR Sony protocol handler initialized
[   99.119084] lirc_dev: IR Remote Control driver registered, major 250
[   99.133810] IR LIRC bridge handler initialized
[  104.704513] af9015: bulk message failed:-110 (8/0)
[  104.704524] af9015: eeprom read failed:-110
[  104.704547] dvb_usb_af9015: probe of 6-1:1.0 failed with error -110
[  104.706480] usbcore: registered new interface driver dvb_usb_af9015
```

if i try and manually load the driver i get

$ sudo modprobe dvb-usb-af9015
$ dmesg

```
[ 6163.061092] usb 6-1: usbfs: USBDEVFS_CONTROL failed cmd lsusb rqt 128 rq 6 len 255 ret -110
```

I've messed around a lot, different versions of the firmware etc, i chucked in an empty HDD and tried a clean install of 11.04, and tried to install 11.10 Beta 1 and 2 (they don't work - they freeze after the Remote Control Setup page as someone reported here [https://bugs.launchpad.net/bugs/854426](https://bugs.launchpad.net/bugs/854426)), the live disks give me some error about loading a failsafe something, so I can't see if it's going to work in 11.10. Nothing has worked besides using it in a Windows machine... I've always said myth was worth the effort, but this has gone too far.

Any ideas?

cheers

Shep

---

### Post by nickrout on 2011-09-28
Is that an analogue card? If so update to latest .024.1-fixes via mythbuntu repos.

---

### Post by daveshep on 2011-10-06
nah man its digital... 

now i'm just hanging for the real 11.10, hoping it "just works" in that one ;)

---

### Post by nickrout on 2011-10-06
Oh is the driver in the newer kernel then?

---

### Post by goffa on 2011-10-07
The card does work with 2.6.38 but I've found some updates to be buggy. 

To get the card to work try installing the most recent V4L drivers [http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers)

This may also help [http://linuxtv.org/wiki/index.php/Leadtek_WinFast_DTV2000DS](http://linuxtv.org/wiki/index.php/Leadtek_WinFast_DTV2000DS)

It this does not work, try adding the patch as mentioned here [http://forums.whirlpool.net.au/forum-replies.cfm?t=1758402](http://forums.whirlpool.net.au/forum-replies.cfm?t=1758402) 

BTW I'm using firmware version 4.95

---

### Post by daveshep on 2011-10-12
thanks goffa, i'll give that a crack and write up how it goes...

---

### Post by daveshep on 2011-10-28
nah no luck, i'd actually tried that all before but thought i'd have another crack in case anything had changed... i've since upgraded to mythbuntu 11.10 hoping the new kernel would help, but it still doesn't work. 

any chance it's my hardware? eg motherboard?

---

### Post by goffa72 on 2011-11-01
well, I'm not too sure what other help I can provide, you are getting errors in you dmesg so have you checked the firmware is located in the correct location, /lib/firmware/dvb-usb-af9015.fw. 
do you get anything under /dev/dvb/

btw I'm using Mythbuntu 10.04 with 2.6.38-12, the kernel was updated a few days ago and the card worked without having to update v4l drivers, I even had two recordings of different channels working at the same time a few nights ago.
Perhaps you could try 10.04 and install 2.6.38 kernel.

The is the relevant lines from my dmesg, as you can see it loads adapter 0 and adapter 1.

> [    0.000000] Linux version 2.6.38-12-generic (buildd@vernadsky) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #51~lucid1-Ubuntu SMP Thu Sep 29 19:55:22 UTC 2011 (Ubuntu 2.6.38-12.51~lucid1-generic 2.6.38.

[   39.710331] dvb-usb: found a 'Leadtek WinFast DTV2000DS' in cold state, will try to load a firmware
[   39.765179] dvb-usb: downloading firmware from file 'dvb-usb-af9015.fw'
[   39.778583] IR JVC protocol handler initialized
[   39.834123] dvb-usb: found a 'Leadtek WinFast DTV2000DS' in warm state.
[   39.834940] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   39.835329] DVB: registering new adapter (Leadtek WinFast DTV2000DS)


[   40.942662] af9013: firmware version:4.95.0.0
[   40.945915] DVB: registering adapter 0 frontend 0 (Afatech AF9013 DVB-T)...


[   41.151236] tda18271 1-00c0: creating new instance
[   41.157069] TDA18271HD/C2 detected @ 1-00c0
[   41.246583] usbcore: registered new interface driver snd-usb-audio
[   41.432490] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   41.432951] DVB: registering new adapter (Leadtek WinFast DTV2000DS)


[   42.781454] af9013: found a 'Afatech AF9013 DVB-T' in warm state.
[   42.870960] af9013: firmware version:4.95.0.0
[   42.930444] DVB: registering adapter 1 frontend 0 (Afatech AF9013 DVB-T)...
[   42.931239] tda18271 2-00c0: creating new instance
[   42.970476] TDA18271HD/C2 detected @ 2-00c0


[   43.388044] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:08.0/0000:01:06.2/usb3/3-1/rc/rc1/input7
[   43.388636] rc1: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:08.0/0000:01:06.2/usb3/3-1/rc/rc1
[   43.388641] dvb-usb: schedule remote query interval to 500 msecs.
[   43.388646] dvb-usb: Leadtek WinFast DTV2000DS successfully initialized and connected.
[   43.398388] usbcore: registered new interface driver dvb_usb_af9015

---

### Post by daveshep on 2011-11-06
ok yeh last resort i installed mythbuntu 10.04, updated the kernel to 2.6.38 and... nothing. same errors, still no /dev/dvb, same annoyed me.

i bought a digitalnow tinytwin which is supposed to work out of the box... well, one tuner works - the other one just never locks. and sometimes the "working" tuner doesn't lock either.

i just installed windows 7, everything works. how about that? i've had it with linux. it's free so i can't really get too mad but i've wasted a lot of time on something that's supposed to work. the problem is mythtv is so much better than the MS version, but i've got no choice - it's MS or errors. so 'ken annoyed... 

thanks for the help...

---

