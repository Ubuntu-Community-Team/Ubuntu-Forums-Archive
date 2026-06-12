---
title: "Roland USB audio interface impossible to make it work"
date: 2012-01-07
forum: Multimedia Software
---

### Post by Vier_ote on 2012-01-07
Hello to @ll,

Recently I purchased a Roland Duo-Capture USB audio interface to connect my guitar to the computer for my own audio production. This is the last step to pass through and forget everything about Windows and work only with linux. When plugged the Roland Duo-Capture to an USB port Ubuntu recognise it without problem:

[FONT=Courier New]~$ lsusb
Bus 005 Device 003: ID 413c:3200 Dell Computer Corp. Mouse
Bus 005 Device 002: ID 413c:2107 Dell Computer Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 003 Device 002: ID 0582:012b Roland Corp. **
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT]

But does not identify it as an audio card:

[FONT=Courier New]~$ cat /proc/asound/cards
 0 [Audigy2        ]: Audigy2 - SB Audigy 2 ZS [SB0353]
                      SB Audigy 2 ZS [SB0353] (rev.4, serial:0x10031102) at 0xdcc0, irq 18
 1 [UX16           ]: USB-Audio - UX16
                      Yamaha UX16 at usb-0000:00:1d.7-6.4, full speed[/FONT]

Working around over the connected device details it shows as follows:

[FONT=Courier New]~$ sudo lsusb -v | less
Bus 003 Device 002: ID 0582:012b Roland Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass         0 
  bDeviceProtocol       255 
  bMaxPacketSize0        64
  idVendor           0x0582 Roland Corp.
  idProduct          0x012b 
  bcdDevice            1.00
  iManufacturer           1 Roland
  iProduct                2 DUO-CAPTURE
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          115
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower               96mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      2 
      bInterfaceProtocol      2 
      iInterface              0 
      ** UNRECOGNIZED:  06 24 f1 01 00 00
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       1
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      2 
      bInterfaceProtocol      2 
      iInterface              0 
      ** UNRECOGNIZED:  07 24 01 01 00 01 00
      ** UNRECOGNIZED:  0b 24 02 01 02 03 18 01 44 ac 00
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
 bmAttributes            9
          Transfer Type            Isochronous
          Synch Type               Adaptive
          Usage Type               Data
        wMaxPacketSize     0x0120  1x 288 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      2 
      bInterfaceProtocol      1 
      iInterface              0 
      ** UNRECOGNIZED:  07 24 01 07 00 01 00
      ** UNRECOGNIZED:  0b 24 02 01 02 03 18 01 44 ac 00
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0120  1x 288 bytes
        bInterval               1
Device Status:     0x0002
  (Bus Powered)
  Remote Wakeup Enabled[/FONT] 

I also loaded manually snd-usb-audio and forced reload alsa but Ubuntu never identify the usb audio card.

Any idea what could it be done? :confused:  Thanks

---

### Post by pstanis on 2012-01-21
Hi Vier_ote,
I've got exactly the same problem.
I just bought a Duo-capture and it gives a very good sound, but not with the USB and ubuntu.
I was wondering if you had found a solution.
Surely there must be a way to force a USB input to be a sound card.
Does anybody out there know how to do that?
Please help!

---

### Post by Vier_ote on 2012-01-24
**pstanis**, I've tried a lot of procedures but none worked. Even I have restored windows XP with dual boot.

---

### Post by Ascurion on 2013-01-09
Hi all,

I know this thread is already one year old, but it's one of the first when searching for help to get the Duo-Capture working under Linux/Ubuntu (in my case Ubuntu 12.10), so may be it is still of interest. 

I had the same problem that the Roland Duo-Capture (UA-11) was not recognized by Ubuntu 12.10 but I found this message on the alsa development mailing list which did the trick:

[http://comments.gmane.org/gmane.linux.alsa.devel/102869](http://comments.gmane.org/gmane.linux.alsa.devel/102869)

As described there the Duo-Capture has a very tiny switch on the bottom of the device which is labelled "EXT" and has two positions "*" and "**". Normally it is set to "*" and in this state it is not recognized. However if it is set to "**" it works like a charm.  The switch somehow sets the device in an "advanced" mode (not that I know what that means) which changes its USB ID. Seemingly this new ID is supported by the drivers in Ubuntu. 

I tried full duplex recording and playback and got, for my needs, good latency values around 5 ms with Jack and Ardour on Ubuntu Studio 12.10. So far all features of the card I tried worked :p.

---

### Post by Ozor Mox on 2013-01-15
Ascurion you legend! I'd given up on ever getting this thing working under Ubuntu and that simple little trick made it spring to life. What a weird switch, I never even noticed it was there! Thanks very much!

---

### Post by Ascurion on 2013-01-15
I'm glad it did help you! I totally overlooked that switch as well. But  anyway, who would have thought that a hardware-switch could make the  device fully supported in Linux, so why search for it? Mysterious  engineering that is. I was giving it the last chance that day before selling it  again, after I searched my eyes out for a solution some months before  without success. I am very happy now, because I can finally leave  Windows behind for recording! :guitar:

---

### Post by AteTeVoortwis on 2013-01-16
Well that is certainly good news!
Did you go through any other additional steps or is it just with the default alsa driver and settings from 12.04?
I have a Roland Quad Capture, which doesn't have a similar switch and is recognized in lsusb but is not in /proc/asound/cards...

---

### Post by Ascurion on 2013-01-16
I did not do any additional steps.

I have to say however that I first tried it on a  new install of UbuntuStudio 12.10. I expect that there are some tweaks in this system, but I actually did not bother to check on the details on how it is build.   
Then, I tried it on my normal Ubuntu 12.10 but since I played around with this system some months ago to try to get the Duo-Capture working, I can not assure that I don't have anything left that is not standard, although I tried to remove the changes afterwards. 

Right now I am out of reach of my desktop at home running a standard 12.04 with definitely no tweaks. When I am back at home next week I'll try the card on the system and report whether it works out of the box.

---

### Post by Ascurion on 2013-01-16
I just had a quick test on a Ubuntu 12.10 on a laptop of a friend and the Duo-Capture works immediately and with his installation I am sure he did not change the standard driver setups...  as said before I'll test 12.04 in a week and report back...

---

### Post by Vier_ote on 2013-01-16
Yeeesss!! It works!! :guitar:
Thank you, thank you indeed!

After one year, but never it's too late. Mopping my guitar, pluging and coming back to Ubuntu.

---

### Post by Ascurion on 2013-01-22
Hi, like I promised last week, now that I am back home again with my Desktop running a standard Ubuntu 12.04, I tried the Duo-Capture with it and that works (as in 12.10) right out of the box like a charm. Just have to change the sound card in the panel menu from on-board to the USB-Device.

---

### Post by FranzFranc on 2013-06-15
It ist possible Quad Capture to work, with AVLinux 3.8 pae Kernel by Trullan. In this Debian-derivative-distro you can find the kernel in the standard repository, but there are .deb packages, too. I tried to install one package on all our 3 Ubuntu 12.04 PCs. It works only in one PC, with slowed booting. The other 2 PC no  booting with that kernel, i guess due to interaction with Gra-Ca drivers. Working, very basically without volume control at all, but acceptable quality. I have tried, too, in Virtualbox, with Windows Xp. Working only in one PC, I don't know why.

---

