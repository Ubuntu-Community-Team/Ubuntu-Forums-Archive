---
title: "Kubuntu Feisty - No Sound!!"
date: 2007-09-26
forum: Multimedia &amp; Video
---

### Post by sommazzi on 2007-09-26
HI, 

Ever since installing Kubuntu I have had no sound whatsoever, and despite reading the various forum threads I have as yet (and with my limited knowledge of linux) been unable to  cure the problem. 

The sound card I am using is a Roland BOSS GS-10 usb audio device, which I have previously had fully functioning under Ubuntu Dapper. Using aplay -l brings up the following:

**** List of PLAYBACK Hardware Devices ****
card 1: GS10 [GS-10], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Which to me suggests that ubuntu is aware of the device. Using lsusb -v also shows that ubuntu is detecting the device, though i'm not sure what everything here means. apologies for the long list . . . .

[COLOR="Indigo"][B]Bus 001 Device 005: ID 0582:003b Roland Corp.
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass         0
  bDeviceProtocol       255
  bMaxPacketSize0         8
  idVendor           0x0582 Roland Corp.
  idProduct          0x003b
  bcdDevice            1.00
  iManufacturer           1
  iProduct                2
  iSerial                 0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          374
    bNumInterfaces          4
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xc0
      Self Powered
    MaxPower                2mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      1
      bInterfaceProtocol      0
      iInterface              0
      Class specific interface descriptor for class 255 is unsupported
      Class specific interface descriptor for class 255 is unsupported
      Class specific interface descriptor for class 255 is unsupported
      Class specific interface descriptor for class 255 is unsupported
      Class specific interface descriptor for class 255 is unsupported
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      2
      bInterfaceProtocol      0
      iInterface              0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       1
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      2
      bInterfaceProtocol      0
      iInterface              0
      Class specific interface descriptor for class 255 is unsupported
      Class specific interface descriptor for class 255 is unsupported
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
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      2
      bInterfaceProtocol      0
      iInterface              0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       1
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      2
      bInterfaceProtocol      0
      iInterface              0
      Class specific interface descriptor for class 255 is unsupported
      Class specific interface descriptor for class 255 is unsupported
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
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        3
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      3
      bInterfaceProtocol      0
      iInterface              0
      Class specific interface descriptor for class 255 is unsupported
      Class specific interface descriptor for class 255 is unsupported
      Class specific interface descriptor for class 255 is unsupported
      Class specific interface descriptor for class 255 is unsupported
      Class specific interface descriptor for class 255 is unsupported
      Class specific interface descriptor for class 255 is unsupported
      Class specific interface descriptor for class 255 is unsupported
      Class specific interface descriptor for class 255 is unsupported
      Class specific interface descriptor for class 255 is unsupported
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        3
      bAlternateSetting       1
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      3
      bInterfaceProtocol      0
      iInterface              0
      Class specific interface descriptor for class 255 is unsupported
      Class specific interface descriptor for class 255 is unsupported
      Class specific interface descriptor for class 255 is unsupported
      Class specific interface descriptor for class 255 is unsupported
      Class specific interface descriptor for class 255 is unsupported
      Class specific interface descriptor for class 255 is unsupported
      Class specific interface descriptor for class 255 is unsupported
      Class specific interface descriptor for class 255 is unsupported
      Class specific interface descriptor for class 255 is unsupported
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               1
cannot read device status, Operation not permitted (1)[/B][/COLOR]

the last line may be of interest - perhaps this is something to do with permissions?!!
also of note is the result alsamixer gives me:

**[COLOR="Indigo"]alsamixer: function snd_ctl_open failed for default: No such device[/COLOR]**

and alsaconfig brings up command not found, despite the fact that I have alsa-base and alsa-utils installed.

Lastly, and strangely, sound system settings recognises the GS-10 midi, and does not bring up any errors when detecting soundcards/devices, I just dont have any sound!!!


Someone please help me, I will be extremely grateful!!

---

### Post by elliott6 on 2007-09-28
Hello there.

I am sort of an Ubuntu noob, so this may not help.  I am going through something simliar and thought I might add two things.  

The first - 

"cannot read device status, Operation not permitted (1)

the last line may be of interest - perhaps this is something to do with permissions?!!"

This is based on permissions, so if you had user sudo with the command, you would not have seen that last line.  I found that out myself.

As for the second - 

You may wish to try the following post - 
Comprehensive Sound Problem Solutions Guide v0.5e
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

This has a bit of what you started, but seems to take it further.  Best of luck!

---

### Post by elliott6 on 2007-10-01
Real quick update on my sound issue, and this (again) may not help...

I found that my sound is in fact working.  I have it connected to my TV (attempting a Mythbuntu Media Centre creation), and could hear no sound, but everything else was fine - alsamixer, hardware, etc.  Cranked the volume up to unacceptable levels on my TV, and lo and behold, sound!

Now I just have to figure out if I can increase the volume output from the PC so the TV doesn't need to be cranked up so loud.  I think it has to do with the internal PC amplifier, but not sure how to enable it, or if it is possible?  I do have all volume levels in alsamixer all of the way up and unmuted.

So my suggestion is that if all seems to be okay, but no sound, try and crank up the volume on your speakers to hear if you are missing something.

Good luck!

---

### Post by sommazzi on 2007-10-01
Hmm, thats interesting! I had a little look around and found these two threads that may help you - although i don't believe there any any workable solutions here . . . ([https://launchpad.net/ubuntu/edgy/+source/alsa-driver/+bug/47755](https://launchpad.net/ubuntu/edgy/+source/alsa-driver/+bug/47755)) 
([https://launchpad.net/ubuntu/+source/alsa-utils/+bug/64356](https://launchpad.net/ubuntu/+source/alsa-utils/+bug/64356)) 

Unfortunately in my case Kubuntu (and also PClinuxOS, which I also tried), simply refused to acknowledge my sound card. my "workaraound" was to install Ubuntu dapper 6.06, becuase i knew that sound had worked in this previous release. I've then installed the K-desktop. I could perhaps have downgraded ther kernel, as some have suggested, in order to rectify this problem.

Good luck with fixing your sound!!

---

