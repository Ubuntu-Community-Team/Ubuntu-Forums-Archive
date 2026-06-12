---
title: "Xubuntu 22,04 PulseAudio disabled my USB DAC, trying to re-enable"
date: 2022-09-26
forum: Multimedia Software
---

### Post by efricha on 2022-09-26
Greetings all,

A week ago I found myself forced to upgrade to 22.04 LTS from 20.04 LTS.  It went largely smoothly.   Sound worked normally through my USB DAC, which has often been cross-threaded with PulseAudio.

Last Friday, another update went out, and my USB DAC was disabled.  So I checked the usual suspects:

/etc/modprobe.d/alsa-base.conf did not disable snd-usb.

aplay -l lists the USB DAC.

pacmd list shows the USB DAC and shows it as the default sink.,

alsamixer has it enabled.

/etc/pulsa/default.pa and system.pa currently don't load suspend-on-idle (because it was showing up as suspended), although I did try getting to it via module-alsa-sink, but that got to a different device.

pavucontrol does _***NOT***_ list the USB DAC as an output device.

So, I'm open to suggestions to get it listed in pavucontrol again.

I'm not a PulseAudio expert.  I've learned what little I know because PulseAudio seems by default hostile to USB sound devices.

---

### Post by &amp;KyT$0P# on 2022-09-26
Can [FONT=Courier New]aplay[/FONT] play sound out of your USB DAC if you explicitly select its device?

To list devices use
```
aplay -L
```
(capital L)

Then replace the red portions in the below command with the appropriate values -
```
aplay -D [COLOR="#FF0000"]<your USB DAC>[/COLOR] [COLOR="#FF0000"]<some wav file>[/COLOR]
```

---

### Post by efricha on 2022-09-26
I don't even have the syntax right:
```

$ aplay -D CARD=Multibit,DEV=0 ~/Music/wwv-wwvh.wav 
ALSA lib pcm.c:2664:(snd_pcm_open_noupdate) Unknown PCM CARD=Multibit,DEV=0
aplay: main:831: audio open error: No such file or directory
$ aplay -D CARD=Multibit ~/Music/wwv-wwvh.wav 
ALSA lib pcm.c:2664:(snd_pcm_open_noupdate) Unknown PCM CARD=Multibit
aplay: main:831: audio open error: No such file or directory
$ aplay -D CARD=Multibit ~/Music/wwv-wwvh.wav 
$ aplay -D CARD=Multibit,DEV=0 ~/Music/wwv-wwvh.wav 
ALSA lib pcm.c:2664:(snd_pcm_open_noupdate) Unknown PCM CARD=Multibit,DEV=0
aplay: main:831: audio open error: No such file or directory
$ aplay -D CARD=Multibit ~/Music/wwv-wwvh.wav 
ALSA lib pcm.c:2664:(snd_pcm_open_noupdate) Unknown PCM CARD=Multibit
aplay: main:831: audio open error: No such file or directory
$ aplay -D Multibit,0 ~/Music/wwv-wwvh.wav 
ALSA lib pcm.c:2664:(snd_pcm_open_noupdate) Unknown PCM Multibit,0
aplay: main:831: audio open error: No such file or directory
$ aplay -D Multibit ~/Music/wwv-wwvh.wav 
ALSA lib pcm.c:2664:(snd_pcm_open_noupdate) Unknown PCM Multibit
aplay: main:831: audio open error: No such file or directory
$ aplay -D usbstream ~/Music/wwv-wwvh.wav 
ALSA lib confmisc.c:160:(snd_config_get_card) Invalid field card
ALSA lib pcm_usb_stream.c:482:(_snd_pcm_usb_stream_open) Invalid card 'card'
aplay: main:831: audio open error: Invalid argument
$ aplay -D usbstream:CARD=Multibit ~/Music/wwv-wwvh.wav 
aplay: main:831: audio open error: No such file or directory
$ aplay -D usbstream:CARD=Multibit ~/Music/wwv-wwvh.wav 
aplay: main:831: audio open error: No such file or directory
$ aplay -D usbstream:CARD=Multibit,DEV=0 /home/eric/Music/wwv-wwvh.wav 
ALSA lib conf.c:5514:(parse_args) Unknown parameter DEV
ALSA lib conf.c:5685:(snd_config_expand) Parse arguments error: No such file or directory
ALSA lib pcm.c:2664:(snd_pcm_open_noupdate) Unknown PCM usbstream:CARD=Multibit,DEV=0
aplay: main:831: audio open error: No such file or directory

```

---

### Post by efricha on 2022-09-27
From looking at exmples,  I came up with this.  What does it tell  you?

```

$ aplay -D usbstream:0 ~/Music/wwv-wwvh.wav 
aplay: main:831: audio open error: Permission denied
$ groups
(me) adm tty dialout fax cdrom floppy sudo audio dip plugdev lpadmin lxd sambashare docker wireshark

```

---

### Post by &amp;KyT$0P# on 2022-09-27
It tells me that there is likely an issue at the ALSA layer, which is deeper than PulseAudio, so you'll need to fix that first.  Sorry I don't know how to troubleshoot that further :(

---

### Post by efricha on 2022-09-27
```

$ sudo aplay -D usbstream:0 ~/Music/The\ Alan\ Parsons\ Project/pauls.wav 
Playing WAVE '/home/eric/Music/The Alan Parsons Project/pauls.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
aplay: set_params:1347: Access type not available

```


All the device files in /dev/snd look right, /dev/snd itself looks right.

---

### Post by #&amp;thj^% on 2022-09-27
I might not be of help here, I don't use Pulseaudio.
but this may or may not shed something of use:
```
sudo lsusb -v -s 004:003

```
I'm very opinionated with pulse, so keep that in mind here. ;)
```
inxi -Az
Audio:
  Device-1: AMD ACP/ACP3X/ACP6x Audio Coprocessor driver: N/A
  Device-2: AMD Family 17h/19h HD Audio driver: snd_hda_intel
  Device-3: DisplayLink UOEOS Laptop Dock type: USB
    driver: cdc_ncm,snd-usb-audio
  Sound Server-1: ALSA v: k5.19.10-1-default running: yes
  Sound Server-2: PipeWire v: 0.3.58 running: yes


```
Also I'm not suggesting to dump pulseaudio at this time for you.
But I've never been happier with my set-up.
```
wpctl status
PipeWire 'pipewire-0' [0.3.58, me@localhost.localdomain, cookie:<snip>]
 &#9492;&#9472; Clients:
        31. xfwm4                               [0.3.58, me@localhost.localdomain, pid:3107]
        33. pipewire-pulse                      [0.3.58, me@localhost.localdomain, pid:3119]
        34. WirePlumber                         [0.3.58, me@localhost.localdomain, pid:3118]
        35. WirePlumber [export]                [0.3.58, me@localhost.localdomain, pid:3118]
        62. xfce4-pulseaudio-plugin             [0.3.58, me@localhost.localdomain, pid:3237]
        63. xdg-desktop-portal                  [0.3.58, me@localhost.localdomain, pid:19638]
        64. wpctl                               [0.3.58, me@localhost.localdomain, pid:21936]

Audio
 &#9500;&#9472; Devices:
 &#9474;      43. UOEOS Laptop Dock                   [alsa]
 &#9474;      44. Family 17h/19h HD Audio Controller  [alsa]
 &#9474;  
 &#9500;&#9472; Sinks:
 &#9474;  *   51. UOEOS Laptop Dock Digital Stereo (IEC958) [vol: 0.74]
 &#9474;      53. Family 17h/19h HD Audio Controller Pro [vol: 1.00]
 &#9474;  
 &#9500;&#9472; Sink endpoints:
 &#9474;  
 &#9500;&#9472; Sources:
 &#9474;      52. UOEOS Laptop Dock Digital Stereo (IEC958) [vol: 0.74 MUTED]
 &#9474;  *   54. Family 17h/19h HD Audio Controller Pro [vol: 1.00]
 &#9474;  
 &#9500;&#9472; Source endpoints:
 &#9474;  
 &#9492;&#9472; Streams:

Video
 &#9500;&#9472; Devices:
 &#9474;      41. Integrated Camera                   [v4l2]
 &#9474;      42. Integrated Camera                   [v4l2]
 &#9474;  
 &#9500;&#9472; Sinks:
 &#9474;  
 &#9500;&#9472; Sink endpoints:
 &#9474;  
 &#9500;&#9472; Sources:
 &#9474;  *   45. Integrated Camera (V4L2)           
 &#9474;  
 &#9500;&#9472; Source endpoints:
 &#9474;  
 &#9492;&#9472; Streams:

Settings
 &#9492;&#9472; Default Configured Node Names:
         0. Audio/Sink    alsa_output.usb-DisplayLink_UOEOS_Laptop_Dock_4307293310436-02.iec958-stereo
         1. Audio/Source  alsa_input.pci-0000_05_00.6.pro-input-0


```

---

### Post by efricha on 2022-09-29
> **1fallen said:**
> I might not be of help here, I don't use Pulseaudio.
but this may or may not shed something of use:
```
sudo lsusb -v -s 004:003

```
I'm very opinionated with pulse, so keep that in mind here. ;)
```
inxi -Az
Audio:
  Device-1: AMD ACP/ACP3X/ACP6x Audio Coprocessor driver: N/A
  Device-2: AMD Family 17h/19h HD Audio driver: snd_hda_intel
  Device-3: DisplayLink UOEOS Laptop Dock type: USB
    driver: cdc_ncm,snd-usb-audio
  Sound Server-1: ALSA v: k5.19.10-1-default running: yes
  Sound Server-2: PipeWire v: 0.3.58 running: yes


```
Also I'm not suggesting to dump pulseaudio at this time for you.
But I've never been happier with my set-up.


In my case, it was as follows:
```

$ sudo lsusb -v -s 2:2

Bus 002 Device 002: ID 0d8c:0004 C-Media Electronics, Inc. CM6631A Audio Processor
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          239 Miscellaneous Device
  bDeviceSubClass         2 
  bDeviceProtocol         1 Interface Association
  bMaxPacketSize0        64
  idVendor           0x0d8c C-Media Electronics, Inc.
  idProduct          0x0004 CM6631A Audio Processor
  bcdDevice            1.02
  iManufacturer           1 Schiit Audio
  iProduct                2 Modi Multibit
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength       0x012a
    bNumInterfaces          3
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower              100mA
    Interface Association:
      bLength                 8
      bDescriptorType        11
      bFirstInterface         0
      bInterfaceCount         2
      bFunctionClass          1 Audio
      bFunctionSubClass       0 
      bFunctionProtocol      32 
      iFunction               0 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         1 Audio
      bInterfaceSubClass      1 Control Device
      bInterfaceProtocol     32 
      iInterface              0 
      AudioControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      1 (HEADER)
        bcdADC               2.00
        bCategory              10
        wTotalLength       0x0100
        bmControls           0x00
      AudioControl Interface Descriptor:
        bLength                17
        bDescriptorType        36
        bDescriptorSubtype      2 (INPUT_TERMINAL)
        bTerminalID             1
        wTerminalType      0x0101 USB Streaming
        bAssocTerminal          0
        bCSourceID             18
        bNrChannels             0
        bmChannelConfig    0x00000000
        iChannelNames           0 
        bmControls         0x0040
          Cluster Control (read-only)
        iTerminal               0 
      AudioControl Interface Descriptor:
        bLength                12
        bDescriptorType        36
        bDescriptorSubtype      3 (OUTPUT_TERMINAL)
        bTerminalID             7
        wTerminalType      0x0301 Speaker
        bAssocTerminal          0
        bSourceID              13
        bCSourceID             18
        bmControls         0x0004
          Connector Control (read-only)
        iTerminal               0 
      AudioControl Interface Descriptor:
        bLength                18
        bDescriptorType        36
        bDescriptorSubtype      6 (FEATURE_UNIT)
        bUnitID                13
        bSourceID               1
        bmaControls(0)     0x00000003
          Mute Control (read/write)
        bmaControls(1)     0x00000000
        bmaControls(2)     0x00000000
        iFeature                0 
      AudioControl Interface Descriptor:
        bLength                 8
        bDescriptorType        36
        bDescriptorSubtype     10 (CLOCK_SOURCE)
        bClockID               18
        bmAttributes            3 Internal programmable clock 
        bmControls           0x07
          Clock Frequency Control (read/write)
          Clock Validity Control (read-only)
        bAssocTerminal          0
        iClockSource            0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x8f  EP 15 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0006  1x 6 bytes
        bInterval               4
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol     32 
      iInterface              0 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       1
      bNumEndpoints           2
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol     32 
      iInterface              0 
      AudioStreaming Interface Descriptor:
        bLength                16
        bDescriptorType        36
        bDescriptorSubtype      1 (AS_GENERAL)
        bTerminalLink           1
        bmControls           0x05
          Active Alternate Setting Control (read-only)
          Valid Alternate Setting Control (read-only)
        bFormatType             1
        bmFormats          0x00000001
          PCM
        bNrChannels             2
        bmChannelConfig    0x00000003
          Front Left (FL)
          Front Right (FR)
        iChannelNames           0 
      AudioStreaming Interface Descriptor:
        bLength                 6
        bDescriptorType        36
        bDescriptorSubtype      2 (FORMAT_TYPE)
        bFormatType             1 (FORMAT_TYPE_I)
        bSubslotSize            2
        bBitResolution         16
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x05  EP 5 OUT
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x00c4  1x 196 bytes
        bInterval               1
        AudioStreaming Endpoint Descriptor:
          bLength                 8
          bDescriptorType        37
          bDescriptorSubtype      1 (EP_GENERAL)
          bmAttributes         0x00
          bmControls           0x00
          bLockDelayUnits         0 Undefined
          wLockDelay         0x0000
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x85  EP 5 IN
        bmAttributes           17
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Feedback
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval               4
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       2
      bNumEndpoints           2
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol     32 
      iInterface              0 
      AudioStreaming Interface Descriptor:
        bLength                16
        bDescriptorType        36
        bDescriptorSubtype      1 (AS_GENERAL)
        bTerminalLink           1
        bmControls           0x05
          Active Alternate Setting Control (read-only)
          Valid Alternate Setting Control (read-only)
        bFormatType             1
        bmFormats          0x00000001
          PCM
        bNrChannels             2
        bmChannelConfig    0x00000003
          Front Left (FL)
          Front Right (FR)
        iChannelNames           0 
      AudioStreaming Interface Descriptor:
        bLength                 6
        bDescriptorType        36
        bDescriptorSubtype      2 (FORMAT_TYPE)
        bFormatType             1 (FORMAT_TYPE_I)
        bSubslotSize            3
        bBitResolution         24
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x05  EP 5 OUT
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0126  1x 294 bytes
        bInterval               1
        AudioStreaming Endpoint Descriptor:
          bLength                 8
          bDescriptorType        37
          bDescriptorSubtype      1 (EP_GENERAL)
          bmAttributes         0x00
          bmControls           0x00
          bLockDelayUnits         0 Undefined
          wLockDelay         0x0000
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x85  EP 5 IN
        bmAttributes           17
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Feedback
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval               4
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       3
      bNumEndpoints           2
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol     32 
      iInterface              0 
      AudioStreaming Interface Descriptor:
        bLength                16
        bDescriptorType        36
        bDescriptorSubtype      1 (AS_GENERAL)
        bTerminalLink           1
        bmControls           0x05
          Active Alternate Setting Control (read-only)
          Valid Alternate Setting Control (read-only)
        bFormatType             1
        bmFormats          0x00000001
          PCM
        bNrChannels             2
        bmChannelConfig    0x00000003
          Front Left (FL)
          Front Right (FR)
        iChannelNames           0 
      AudioStreaming Interface Descriptor:
        bLength                 6
        bDescriptorType        36
        bDescriptorSubtype      2 (FORMAT_TYPE)
        bFormatType             1 (FORMAT_TYPE_I)
        bSubslotSize            4
        bBitResolution         32
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x05  EP 5 OUT
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0188  1x 392 bytes
        bInterval               1
        AudioStreaming Endpoint Descriptor:
          bLength                 8
          bDescriptorType        37
          bDescriptorSubtype      1 (EP_GENERAL)
          bmAttributes         0x00
          bmControls           0x00
          bLockDelayUnits         0 Undefined
          wLockDelay         0x0000
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x85  EP 5 IN
        bmAttributes           17
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Feedback
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval               4
    Interface Association:
      bLength                 8
      bDescriptorType        11
      bFirstInterface         2
      bInterfaceCount         1
      bFunctionClass          3 Human Interface Device
      bFunctionSubClass       0 
      bFunctionProtocol       0 
      iFunction               0 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.00
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      50
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               4
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass          239 Miscellaneous Device
  bDeviceSubClass         2 
  bDeviceProtocol         1 Interface Association
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000

```

And the following:

```

$ inxi -Az
Audio:
  Device-1: AMD Oland/Hainan/Cape Verde/Pitcairn HDMI Audio [Radeon HD 7000
  Series]
    driver: snd_hda_intel
  Device-2: VIA ICE1712 [Envy24] PCI Multi-Channel I/O driver: snd_ice1712
  Device-3: C-Media CM6631A Audio Processor type: USB
    driver: hid-generic,snd-usb-audio,usbhid
  Sound Server-1: ALSA v: k5.15.0-48-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes

```

As you see, PipeWire is installed, but I'm not using it, nor is wpctl installed on my system.   I'm not sure if this brings any new light to the subject at hand.

I have an opinion or two about PulseAudio myself, but my goal is getting it to work at all.  When I'm done with work for the day I'll try substituting different hardware in the off chance that it's a hardware failure, given that error from aplay further up in the thread.  I think that **that** is shedding light on the issue.

There is also a suspicious UNAVAILABLE in the lsusb above.

---

### Post by #&amp;thj^% on 2022-09-29
> **efricha said:**
> In my case, 
 given that error from aplay further up in the thread.  I think that **that** is shedding light on the issue.

There is also a suspicious UNAVAILABLE in the lsusb above.
I'm not sure I'd call suspicious but I'd check why:
>>>```
"ALSA lib pcm.c:2664:(snd_pcm_open_noupdate) Unknown PCM CARD=Multibit,DEV=0
aplay: main:831: audio open error: No such file or directory
$ aplay -D CARD=Multibit ~/Music/wwv-wwvh.wav 
ALSA lib pcm.c:2664:(snd_pcm_open_noupdate) Unknown PCM CARD=Multibit"
```
Has this DAC worked in Ubuntu ever?
Also is MVP installed on this system?

---

### Post by efricha on 2022-09-29
**UPDATE: **A different DAC had _exactly_ the same results. Different brand, different everything.  It does not appear to be hardware.

---

### Post by efricha on 2022-09-29
> **1fallen said:**
> I'm not sure I'd call suspicious but I'd check why:
>>>```
"ALSA lib pcm.c:2664:(snd_pcm_open_noupdate) Unknown PCM CARD=Multibit,DEV=0
aplay: main:831: audio open error: No such file or directory
$ aplay -D CARD=Multibit ~/Music/wwv-wwvh.wav 
ALSA lib pcm.c:2664:(snd_pcm_open_noupdate) Unknown PCM CARD=Multibit"
```
Has this DAC worked in Ubuntu ever?
Also is MVP installed on this system?

Yes.  It even worked on this release/issue, last Thursday (exactly one week ago at this writing).

Another USB DAC has been tried, from a different manufacturer.  All three work, stil on Xubuntu 20.04 LTS on my laptop.

---

### Post by #&amp;thj^% on 2022-09-29
> **efricha said:**
> **UPDATE: **A different DAC had _exactly_ the same results. Different brand, different everything.  It does not appear to be hardware.

Well I was going to ask on the first device shown here, is there a "/etc/oss4/conf/oss_envy24.conf" file?
Asking a lot of questions is the only way I can trouble shoot from another person's machine.

---

### Post by #&amp;thj^% on 2022-09-29
> **efricha said:**
> Yes.  It even worked on this release/issue, last Thursday (exactly one week ago at this writing).

Another USB DAC has been tried, from a different manufacturer.  All three work, stil on Xubuntu 20.04 LTS on my laptop.

Good to know, I hate doing all this work, only to end-up down the rabbit hole. (I'm sure you understand that)
Can we start again with the fist DAC mentioned here?
Maybe see if this is found:
```
cat /etc/oss4/conf/oss_envy24.conf
```

---

### Post by efricha on 2022-09-29
> **1fallen said:**
> Good to know, I hate doing all this work, only to end-up down the rabbit hole. (I'm sure you understand that)
Can we start again with the fist DAC mentioned here?
Maybe see if this is found:
```
cat /etc/oss4/conf/oss_envy24.conf
```

No such directory /etc/oss4

---

### Post by efricha on 2022-09-29
> **1fallen said:**
> I'm not sure I'd call suspicious but I'd check why:
>>>```
"ALSA lib pcm.c:2664:(snd_pcm_open_noupdate) Unknown PCM CARD=Multibit,DEV=0
aplay: main:831: audio open error: No such file or directory
$ aplay -D CARD=Multibit ~/Music/wwv-wwvh.wav 
ALSA lib pcm.c:2664:(snd_pcm_open_noupdate) Unknown PCM CARD=Multibit"
```
Has this DAC worked in Ubuntu ever?
Also is MVP installed on this system?

The fragment you **should** pay attention to is this one.

```

$ sudo aplay -D usbstream:0 ~/Music/The\ Alan\ Parsons\ Project/pauls.wav
Playing WAVE '/home/eric/Music/The Alan Parsons Project/pauls.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
aplay: set_params:1347: Access type not available

```

---

### Post by efricha on 2022-09-29
I did more playing around on the working 20.04 LTS system. 
```

$ aplay -L

```
lists many interfaces for the USB DAC, and usbstream:0 is not the acceptable one to use:  "plughw:" appears to be the right one to use, but 'aplay' cannot access it because it is currently busy... in use by PulseAudio.
So I think without killing off PulseAudio, I couldn't test with aplay over there. 'pavucontrol' lists the USB DAC as one of those available while on 22.04 it is no longer listed and appears to be permissions related... but the device files in /dev/snd all look to be correct, as does the directory snd, itself.

It certainly seems that ALSA is blocked from getting at the devices, but I don't know how or why.

---

### Post by efricha on 2022-10-01
Okay, guys, I'm seriously stuck here.  It appears to be a "simple" permissions problem, but it's not on a device file.
```

$ ls -al /dev/snd
total 0
drwxr-xr-x   4 root root      300 Sep 29 13:01 .
drwxr-xr-x  21 root root     4960 Sep 29 13:01 ..
drwxr-xr-x   2 root root       60 Sep 29 13:01 by-id
drwxr-xr-x   2 root root      100 Sep 29 13:01 by-path
crw-rw----+  1 root audio 116,  6 Sep 29 11:56 controlC0
crw-rw----+  1 root audio 116,  3 Sep 29 13:01 controlC1
crw-rw----+  1 root audio 116, 10 Sep 29 11:56 controlC2
crw-rw----+  1 root audio 116,  5 Sep 29 11:56 hwC0D0
crw-rw----+  1 root audio 116,  9 Sep 29 11:56 midiC2D0
crw-rw----+  1 root audio 116,  4 Sep 29 11:56 pcmC0D3p
crw-rw----+  1 root audio 116,  2 Oct  1 10:59 pcmC1D0p
crw-rw----+  1 root audio 116,  8 Sep 29 11:56 pcmC2D0c
crw-rw----+  1 root audio 116,  7 Sep 29 11:56 pcmC2D0p
crw-rw----+  1 root audio 116,  1 Sep 29 11:56 seq
crw-rw----+  1 root audio 116, 33 Sep 29 11:56 timer
$ groups
(me) adm tty dialout fax cdrom floppy tape sudo audio dip video plugdev netdev lpadmin scanner lxd sambashare docker wireshark

```
I don't want to reinstall from distro.  Something went wrong, and I'm  trying to undo it without using a sledgehammer and rebuilding everything  from scratch.

---

### Post by #&amp;thj^% on 2022-10-01
> **efricha said:**
> The fragment you **should** pay attention to is this one.


Should I now? We all have our own methods I suppose.
Mine Looks like:
```
ls -al /dev/snd
total 0
drwxr-xr-x   4 root root      400 Oct  1 09:10 .
drwxr-xr-x  21 root root     4840 Oct  1 11:54 ..
drwxr-xr-x   2 root root       60 Oct  1 09:10 by-id
drwxr-xr-x   2 root root      100 Oct  1 09:10 by-path
crw-rw----+  1 root audio 116,  8 Oct  1 09:10 controlC0
crw-rw----+  1 root audio 116, 12 Oct  1 09:10 controlC1
crw-rw----+  1 root audio 116, 15 Oct  1 09:10 controlC2
crw-rw----+  1 root audio 116,  7 Oct  1 09:10 hwC0D0
crw-rw----+  1 root audio 116, 11 Oct  1 09:10 hwC1D0
crw-rw----+  1 root audio 116,  6 Oct  1 09:10 pcmC0D10p
crw-rw----+  1 root audio 116,  2 Oct  1 09:10 pcmC0D3p
crw-rw----+  1 root audio 116,  3 Oct  1 09:10 pcmC0D7p
crw-rw----+  1 root audio 116,  4 Oct  1 09:10 pcmC0D8p
crw-rw----+  1 root audio 116,  5 Oct  1 09:10 pcmC0D9p
crw-rw----+  1 root audio 116, 10 Oct  1 09:10 pcmC1D0c
crw-rw----+  1 root audio 116,  9 Oct  1 09:10 pcmC1D0p
crw-rw----+  1 root audio 116, 14 Oct  1 09:10 pcmC2D0c
crw-rw----+  1 root audio 116, 13 Oct  1 09:10 pcmC2D0p
crw-rw----+  1 root audio 116,  1 Oct  1 09:10 seq
crw-rw----+  1 root audio 116, 33 Oct  1 09:10 timer


```
Non Debian OS shown here:
```
groups
users firejail nordvpn
```

**Pull up alsamixer and check nothing is Muted.**
Also:
```
systemctl list-unit-files --type service --all | grep alsa
alsa-restore.service                         static          -
alsa-state.service                           static          -
alsasound.service                         alias           -

```

---

### Post by efricha on 2022-10-01
> **1fallen said:**
> Should I now? We all have our own methods I suppose.


Well, until I knew better.

> **1fallen said:**
> Mine Looks like:

**Pull up alsamixer and check nothing is Muted.**
Also:
```
systemctl list-unit-files --type service --all | grep alsa
alsa-restore.service                         static          -
alsa-state.service                           static          -
alsasound.service                         alias           -

```

Nothing muted, however,

```

$ sudo systemctl list-unit-files --type service --all | grep alsa
alsa-restore.service                       static          -
alsa-state.service                         static          -
alsa-utils.service                         masked          enabled
$ 

```

...FWIW.  Nothing muted in alsamixer.

---

### Post by #&amp;thj^% on 2022-10-02
This is what sticks out for me here "alsa-utils.service                       **_  masked  _**        enabled"
Is that change made by you?
1st EDIT: I had forgotten that alsa-restore.service is now used from 20.04 through 22.04 instead of alsa-utils.service, so that's probably set by the Devs.
I need to do an install of Xubuntu to run some test's before I can wisely offer any more suggestions.

**2nd EDIT I remember now that from time to time, Killing pipewire and then restarting pulseaudio fixed the problem:**
```

systemctl --user stop pipewire.service
systemctl --user restart pulseaudio.service
```

It appears to be a race between pipewire and pulseaudio. sometimes seems to grab a lock on the USB audio device before pulseaudio can access it.
Give it a try.

---

### Post by efricha on 2022-10-02
> **1fallen said:**
> This is what sticks out for me here "alsa-utils.service                       **_  masked  _**        enabled"
Is that change made by you?
1st EDIT: I had forgotten that alsa-restore.service is now used from 20.04 through 22.04 instead of alsa-utils.service, so that's probably set by the Devs.
I need to do an install of Xubuntu to run some test's before I can wisely offer any more suggestions.

**2nd EDIT I remember now that from time to time, Killing pipewire and then restarting pulseaudio fixed the problem:**
```

systemctl --user stop pipewire.service
systemctl --user restart pulseaudio.service
```

It appears to be a race between pipewire and pulseaudio. sometimes seems to grab a lock on the USB audio device before pulseaudio can access it.
Give it a try.

No dice.  Same same.

**EDIT: **where does syslog stick logging information?  maybe it left breadcrumbs that I can't find.  (none in dmesg, I looked.)

---

### Post by #&amp;thj^% on 2022-10-02
> **efricha said:**
> No dice.  Same same.

one more before I install, 
```
systemctl status alsa-restore
&#9679; alsa-restore.service - Save/Restore Sound Card State
     Loaded: loaded (/usr/lib/systemd/system/alsa-restore.service; static)
     Active: active (exited) since Sun 2022-10-02 12:10:28 MDT; 2h 45min ago
   Main PID: 1390 (code=exited, status=0/SUCCESS)
        CPU: 2ms

```

---

### Post by efricha on 2022-10-02
> **1fallen said:**
> one more before I install, 
```
systemctl status alsa-restore
&#9679; alsa-restore.service - Save/Restore Sound Card State
     Loaded: loaded (/usr/lib/systemd/system/alsa-restore.service; static)
     Active: active (exited) since Sun 2022-10-02 12:10:28 MDT; 2h 45min ago
   Main PID: 1390 (code=exited, status=0/SUCCESS)
        CPU: 2ms

```

```

$ sudo systemctl status alsa-restore
&#9679; alsa-restore.service - Save/Restore Sound Card State
     Loaded: loaded (/lib/systemd/system/alsa-restore.service; static)
     Active: active (exited) since Sun 2022-10-02 14:33:56 MDT; 27min ago
       Docs: man:alsactl(1)
    Process: 993 ExecStartPre=/bin/mkdir -p /run/alsa (code=exited, status=0/SU>
    Process: 1000 ExecStart=/usr/sbin/alsactl -E HOME=/run/alsa -E XDG_RUNTIME_>
   Main PID: 1000 (code=exited, status=0/SUCCESS)
        CPU: 9ms

Oct 02 14:33:56 patchwork systemd[1]: Starting Save/Restore Sound Card State...
Oct 02 14:33:56 patchwork systemd[1]: Finished Save/Restore Sound Card State.
Oct 02 14:33:56 patchwork alsactl[1000]: alsa-lib main.c:1412:(snd_use_case_mgr>
eric@patchwork:~$ sudo systemctl status alsa-restore
&#9679; alsa-restore.service - Save/Restore Sound Card State
     Loaded: loaded (/lib/systemd/system/alsa-restore.service; static)
     Active: active (exited) since Sun 2022-10-02 14:33:56 MDT; 29min ago
       Docs: man:alsactl(1)
    Process: 993 ExecStartPre=/bin/mkdir -p /run/alsa (code=exited, status=0/SUCCESS)
    Process: 1000 ExecStart=/usr/sbin/alsactl -E HOME=/run/alsa -E XDG_RUNTIME_DIR=/run/alsa/runtime restore (code=exited, status=0/SUCCESS)
   Main PID: 1000 (code=exited, status=0/SUCCESS)
        CPU: 9ms

Oct 02 14:33:56 patchwork systemd[1]: Starting Save/Restore Sound Card State...
Oct 02 14:33:56 patchwork systemd[1]: Finished Save/Restore Sound Card State.
Oct 02 14:33:56 patchwork alsactl[1000]: alsa-lib main.c:1412:(snd_use_case_mgr_open) error: failed to import hw:1 use case configuration -2

```

That last line looks interesting.

---

### Post by #&amp;thj^% on 2022-10-02
Sure looks as if you maybe right, a permission problem.
Why?:
```
Process: 993 ExecStartPre=/bin/mkdir -p /run/alsa (code=exited, status=0/SU>
    Process: 1000 ExecStart=/usr/sbin/alsactl -E HOME=/run/alsa -E XDG_RUNTIME_>[
###  And This
alsa-lib main.c:1412:(snd_use_case_mgr_open) error: failed to import hw:1 use case configuration -2
```
and a sample from mine:
```
sudo systemctl status alsa-restore
[sudo] password for root: 
Sorry, try again.
[sudo] password for root: 
&#9679; alsa-restore.service - Save/Restore Sound Card State
     Loaded: loaded (/usr/lib/systemd/system/alsa-restore.service; static)
     Active: active (exited) since Sun 2022-10-02 12:10:28 MDT; 2h 58min ago
   Main PID: 1390 (code=exited, status=0/SUCCESS)
        CPU: 2ms

Oct 02 12:10:28 localhost systemd[1]: Starting Save/Restore Sound Card State...
Oct 02 12:10:28 localhost systemd[1]: Finished Save/Restore Sound Card State.


```
It shows start and finish, as expected....hmmm?
This isn't normal outputs shown from your replys.
with your Best Recall have you altered anything with /etc/pulse or Pipewire?

---

### Post by efricha on 2022-10-02
> **1fallen said:**
> Sure looks as if you maybe right, a permission problem.
Why?:
[...]
This isn't normal outputs shown from your replys.
with your Best Recall have you altered anything with /etc/pulse or Pipewire?

Yeah, we knew that.  Okay, permission on ***_what?_*** I don't know what else might have permissions screwed up beyond the device files, and they're good.  So, a UDEV setting?  alsamixer certainly sees it's there, as does parts of pulseaudio.  (See previous output snippets for details.)

---

### Post by #&amp;thj^% on 2022-10-02
Also can I have a look at this please:
```
dmesg | egrep -i "snd|firmware"
```
Sample of mine:
```
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-5.19.12-1-default root=/dev/mapper/system-root splash=silent resume=/dev/disk/by-uuid/6b660db4-36b8-49b7-bc9c-1e5d2aac2c23 preempt=full mitigations=auto quiet ipv6.disable=1 i2c-hid.polling_mode=1 nosimplefb=1 security=apparmor snd-acp6x-pdm-dma
[    0.019392] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-5.19.12-1-default root=/dev/mapper/system-root splash=silent resume=/dev/disk/by-uuid/6b660db4-36b8-49b7-bc9c-1e5d2aac2c23 preempt=full mitigations=auto quiet ipv6.disable=1 i2c-hid.polling_mode=1 nosimplefb=1 security=apparmor snd-acp6x-pdm-dma
[    0.019862] Unknown kernel command line parameters "snd-acp6x-pdm-dma BOOT_IMAGE=/boot/vmlinuz-5.19.12-1-default splash=silent", will be passed to user space.
[    0.087356] Spectre V2 : Enabling Speculation Barrier for firmware calls
[    0.241944] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    0.294945] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
[    0.996244]     snd-acp6x-pdm-dma
[    1.255666] ACPI: video: [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
[    8.703418] snd_rn_pci_acp3x 0000:05:00.5: enabling device (0000 -> 0002)
[    8.844812] snd_hda_intel 0000:01:00.1: enabling device (0000 -> 0002)
[    8.844894] snd_hda_intel 0000:01:00.1: Disabling MSI
[    8.844898] snd_hda_intel 0000:01:00.1: Handle vga_switcheroo audio client
[    8.844971] snd_hda_intel 0000:05:00.6: enabling device (0000 -> 0002)
[    8.879671] iwlwifi 0000:04:00.0: loaded firmware version 71.058653f6.0 cc-a0-71.ucode op_mode iwlmvm
[    8.943129] snd_hda_codec_realtek hdaudioC1D0: autoconfig for ALC257: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[    8.943146] snd_hda_codec_realtek hdaudioC1D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    8.943148] snd_hda_codec_realtek hdaudioC1D0:    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[    8.943149] snd_hda_codec_realtek hdaudioC1D0:    mono: mono_out=0x0
[    8.943151] snd_hda_codec_realtek hdaudioC1D0:    inputs:
[    8.943152] snd_hda_codec_realtek hdaudioC1D0:      Mic=0x19
[    8.943153] snd_hda_codec_realtek hdaudioC1D0:      Internal Mic=0x12
[   10.420128] Bluetooth: hci0: Found device firmware: intel/ibt-20-1-3.sfi
[   10.420194] Bluetooth: hci0: Firmware Version: 20-28.22
[   10.420195] Bluetooth: hci0: Firmware already loaded
[   11.073573] usbcore: registered new interface driver snd-usb-audio



```

---

### Post by efricha on 2022-10-02
```

./client.conf.d:
total 8
drwxr-xr-x 2 root root 4096 Sep 17 14:10 .
drwxr-xr-x 4 root root 4096 Sep 24 16:26 ..
lrwxrwxrwx 1 root root   32 Feb 24  2022 01-enable-autospawn.conf -> /run/pulseaudio-enable-autospawn

```

That's a dangling link.

---

### Post by #&amp;thj^% on 2022-10-02
> **efricha said:**
> Yeah, we knew that.  Okay, permission on ***_what?_*** 

That is the million dollar question now isn't it. ;)
Slow and steady here, you warned no sludge hammer wanted here, so your patience is required.

---

### Post by #&amp;thj^% on 2022-10-02
> **efricha said:**
> ```

./client.conf.d:
total 8
drwxr-xr-x 2 root root 4096 Sep 17 14:10 .
drwxr-xr-x 4 root root 4096 Sep 24 16:26 ..
lrwxrwxrwx 1 root root   32 Feb 24  2022 01-enable-autospawn.conf -> /run/pulseaudio-enable-autospawn

```

That's a dangling link.

To what??
I asked to see this:
```
dmesg | egrep -i "snd|firmware"

```
I hope that's not the return...

---

### Post by #&amp;thj^% on 2022-10-02
One more for tonite, I'm going offline shortly:
```
sudo touch /usr/share/pipewire/media-session.d/with-pulseaudio
systemctl --user restart pipewire-session-manager
```
pipewire-media-session I'm guessing is no longer picking up /etc/pipewire/media-session.d/with-pulseaudio. (could be the permissions we are looking for)

---

### Post by efricha on 2022-10-02
> **1fallen said:**
> One more for tonite, I'm going offline shortly:
```
sudo touch /usr/share/pipewire/media-session.d/with-pulseaudio
systemctl --user restart pipewire-session-manager
```
pipewire-media-session I'm guessing is no longer picking up /etc/pipewire/media-session.d/with-pulseaudio. (could be the permissions we are looking for)

Nothing interesting.

However,
```

# dmesg | egrep -i "snd|firmware"
[    0.426693] pci 0000:00:00.0: [Firmware Bug]: reg 0x1c: invalid BAR (can't size)
[    1.937835] ata1.00: Features: NCQ-sndrcv NCQ-prio
[   13.237563] snd_hda_intel 0000:01:00.1: Force to non-snoop mode
[   13.398447] usbcore: registered new interface driver snd-usb-audio
[   13.499098] usbserial: USB Serial support registered for Keyspan - (without firmware)

```

This device does not need firmware, btw.

---

### Post by #&amp;thj^% on 2022-10-03
> **efricha said:**
> 

**EDIT: **where does syslog stick logging information?  maybe it left breadcrumbs that I can't find.  (none in dmesg, I looked.)
Doubtful but look in:
```
cd /var/log

```
I can't for the life of me recreate your problem..
Not what you want to hear but a fresh clean install, will be my last suggestion for you.

---

### Post by efricha on 2022-10-03
> **1fallen said:**
> Doubtful but look in:
```
cd /var/log

```
I can't for the life of me recreate your problem..
Not what you want to hear but a fresh clean install, will be my last suggestion for you.

It'd be nice to know what that exact line is.  There is a human readable syslog file, much to my surprise, but no useful context.

---

### Post by #&amp;thj^% on 2022-10-03
> **efricha said:**
> It'd be nice to know what that exact line is.
Simply the reply to this: "EDIT: where does syslog stick logging information? "
Your Upgrade doesn't seem to mesh well with Jammy, at least at this level.
my dac:
```
Settings
 &#9492;&#9472; Default Configured Node Names:
         0. Audio/Sink    alsa_output.usb-DisplayLink_UOEOS_Laptop_Dock_4307293310436-02.analog-surround-21
         1. Audio/Source  alsa_input.pci-0000_05_00.6.pro-input-0


```

---

### Post by efricha on 2022-10-05
> **1fallen said:**
> Simply the reply to this: "EDIT: where does syslog stick logging information? "
Your Upgrade doesn't seem to mesh well with Jammy, at least at this level.
my dac:
```
Settings
 &#9492;&#9472; Default Configured Node Names:
         0. Audio/Sink    alsa_output.usb-DisplayLink_UOEOS_Laptop_Dock_4307293310436-02.analog-surround-21
         1. Audio/Source  alsa_input.pci-0000_05_00.6.pro-input-0


```

There's a lot of machine readable stuff that you need journalctl to get to.  I didn't know that until today.

Anyway... I wanted to thank you for all the effort you put in.  I've got a distro ISO ready for nuking the / partition (but not /home).  I don't think it will fix it from what I'm seeing in alsa forums, but I have to give it a shot.

---

### Post by efricha on 2022-10-05
> **1fallen said:**
> Simply the reply to this: "EDIT: where does syslog stick logging information? "
Your Upgrade doesn't seem to mesh well with Jammy, at least at this level.
my dac:
```
Settings
 &#9492;&#9472; Default Configured Node Names:
         0. Audio/Sink    alsa_output.usb-DisplayLink_UOEOS_Laptop_Dock_4307293310436-02.analog-surround-21
         1. Audio/Source  alsa_input.pci-0000_05_00.6.pro-input-0


```

And the verdict is...
...no dice.  Still the same issue.

---

### Post by efricha on 2022-10-06
Apparently the problem is an ALSA/Pulseaudio interaction, and known (+/-)

Now,
```

/etc/modprobe.d/alsa-base.conf

```
Is known for having the lines
```

options snd-usb-audio index=-2

```
(note the dashes)
...and notorious for putting it in more than one place when people commented it out (because they liked USB sound).  The "index=-2" makes it unavailable to PulseAudio.  So the trick is to comment it out.

Until now.
I tried to attach the output of alsa-info to this posting, but for some reason, it wouldn't let me (or I'm too dumb to figure out the interface).  The important things are that the library version is 1.2.6.1 and the line "snd_usb_audio: index=-2" (note the underscores) in the modprobe section.  Now, there is no setting on the root partition that contains that string, so I'm assuming that it defaults to -2 in the modprobe code of alsa now, in other words, it's hardcoded.

Now, [https://www.linuxquestions.org/questions/slackware-14/alsa-lib-1-2-5-broke-hdmi-and-displayport-audio-4175695880/](https://www.linuxquestions.org/questions/slackware-14/alsa-lib-1-2-5-broke-hdmi-and-displayport-audio-4175695880/) talks about a number of interfaces (including USB) broken in 1.2.5.  Their solution is to revert to a previous version of alsa.

So, now, are there any ALSA gurus out there?  Mods, can you change my tags to include ALSA?  Ubuntu gurus, how do you revert a single package and hold it at the previous version?  I;'m not that apt-literate.

---

### Post by #&amp;thj^% on 2022-10-06
before getting off track here, Please try this first:
```
systemctl --user unmask pulseaudio
systemctl --user --now enable pulseaudio.service pulseaudio.socket
```
EDIT: Dang I keep forgetting to ask for this as well:
```
cat -n /etc/modprobe.d/blacklist.conf
```
If none of the above leads us to a solution, I have a replacement for audio, the suspense grows...:D

---

### Post by efricha on 2022-10-06
> **1fallen said:**
> before getting off track here, Please try this first:
```
systemctl --user unmask pulseaudio
systemctl --user --now enable pulseaudio.service pulseaudio.socket
```
EDIT: Dang I keep forgetting to ask for this as well:
```
cat -n /etc/modprobe.d/blacklist.conf
```
If none of the above leads us to a solution, I have a replacement for audio, the suspense grows...:D

```

$ systemctl --user unmask pulseaudio
$ systemctl --user --now enable pulseaudio.service pulseaudio.socket
Created symlink (me)/.config/systemd/user/default.target.wants/pulseaudio.service &#8594; /usr/lib/systemd/user/pulseaudio.service.
Created symlink (me)/.config/systemd/user/sockets.target.wants/pulseaudio.socket &#8594; /usr/lib/systemd/user/pulseaudio.socket.
$ 

```
And, this is pure vanilla.  Remember, I wiped the root partition.
```

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

$

```

If you already mentioned your alternative a couple pages back, I'm leaning that way, too, knowing that it was loaded -- at least then, it was.

---

### Post by efricha on 2022-10-06
> **1fallen said:**
> before getting off track here, Please try this first:
```
systemctl --user unmask pulseaudio
systemctl --user --now enable pulseaudio.service pulseaudio.socket
```
EDIT: Dang I keep forgetting to ask for this as well:
```
cat -n /etc/modprobe.d/blacklist.conf
```
If none of the above leads us to a solution, I have a replacement for audio, the suspense grows...:D

Are you thinking This? [https://ubuntuhandbook.org/index.php/2022/04/pipewire-replace-pulseaudio-ubuntu-2204/](https://ubuntuhandbook.org/index.php/2022/04/pipewire-replace-pulseaudio-ubuntu-2204/)

---

### Post by #&amp;thj^% on 2022-10-07
> **efricha said:**
> Are you thinking This? [https://ubuntuhandbook.org/index.php/2022/04/pipewire-replace-pulseaudio-ubuntu-2204/](https://ubuntuhandbook.org/index.php/2022/04/pipewire-replace-pulseaudio-ubuntu-2204/)

My formula differs just slightly from your link shown, but I can see no problems following that link.
EDIT: I can confirm the validity of that link:
```
System:
  Host: me-Standard-PC-Q35-ICH9-2009 Kernel: 5.15.0-48-generic x86_64
    bits: 64 Desktop: Xfce 4.16.0 Distro: Ubuntu 22.04.1 LTS (Jammy Jellyfish)

```
&&
```
 pactl info
Server String: /run/user/1000/pulse/native
Library Protocol Version: 35
Server Protocol Version: 35
Is Local: yes
Client Index: 58
Tile Size: 65472
User Name: me
Host Name: me-Standard-PC-Q35-ICH9-2009
Server Name: PulseAudio (on PipeWire 0.3.48)
Server Version: 15.0.0
Default Sample Specification: float32le 2ch 48000Hz
Default Channel Map: front-left,front-right
Default Sink: alsa_output.pci-0000_00_1b.0.analog-stereo
Default Source: alsa_input.pci-0000_00_1b.0.analog-stereo
Cookie: ffed:92aa

```
&&
```
inxi -A
Audio:
  Device-1: Intel 82801I HD Audio driver: snd_hda_intel
  Sound Server-1: ALSA v: k5.15.0-48-generic running: yes
  Sound Server-2: PipeWire v: 0.3.48 running: yes

```
I'm hoping this will yield good results for you.

---

### Post by efricha on 2022-10-09
> **1fallen said:**
> My formula differs just slightly from your link shown, but I can see no problems following that link.
EDIT: I can confirm the validity of that link:
```
System:
  Host: me-Standard-PC-Q35-ICH9-2009 Kernel: 5.15.0-48-generic x86_64
    bits: 64 Desktop: Xfce 4.16.0 Distro: Ubuntu 22.04.1 LTS (Jammy Jellyfish)

```
&&
```
 pactl info
Server String: /run/user/1000/pulse/native
Library Protocol Version: 35
Server Protocol Version: 35
Is Local: yes
Client Index: 58
Tile Size: 65472
User Name: me
Host Name: me-Standard-PC-Q35-ICH9-2009
Server Name: PulseAudio (on PipeWire 0.3.48)
Server Version: 15.0.0
Default Sample Specification: float32le 2ch 48000Hz
Default Channel Map: front-left,front-right
Default Sink: alsa_output.pci-0000_00_1b.0.analog-stereo
Default Source: alsa_input.pci-0000_00_1b.0.analog-stereo
Cookie: ffed:92aa

```
&&
```
inxi -A
Audio:
  Device-1: Intel 82801I HD Audio driver: snd_hda_intel
  Sound Server-1: ALSA v: k5.15.0-48-generic running: yes
  Sound Server-2: PipeWire v: 0.3.48 running: yes

```
I'm hoping this will yield good results for you.

And I get... nada.
```

 pactl info
Server String: /run/user/1000/pulse/native
Library Protocol Version: 35
Server Protocol Version: 35
Is Local: yes
Client Index: 62
Tile Size: 65472
User Name: eric
Host Name: leftover
Server Name: PulseAudio (on PipeWire 0.3.48)
Server Version: 15.0.0
Default Sample Specification: float32le 2ch 48000Hz
Default Channel Map: front-left,front-right
Default Sink: alsa_output.usb-Schiit_Audio_Modi_Multibit-00.analog-stereo
Default Source: alsa_input.pci-0000_04_06.0.analog-stereo
Cookie: 064b:6f52

```

The default sink is exactly what I want it to be, but it still doesn't work.

```

$ inxi -A
Audio:
  Device-1: AMD Oland/Hainan/Cape Verde/Pitcairn HDMI Audio [Radeon HD 7000
  Series]
    driver: snd_hda_intel
  Device-2: VIA ICE1712 [Envy24] PCI Multi-Channel I/O driver: snd_ice1712
  Device-3: C-Media CM6631A Audio Processor type: USB
    driver: hid-generic,snd-usb-audio,usbhid
  Sound Server-1: ALSA v: k5.15.0-48-generic running: yes
  Sound Server-2: PipeWire v: 0.3.48 running: yes

```

Device 3 is the one I want.  

Interestingly enough, I sort of got alsa to acknowledge the index properly by forcing it:
```

options snd-usb-audio index=2

```
Which had alsa-info index snd_usb_audio in -2 AND in 2.  Still no availability, though, either way.

---

### Post by #&amp;thj^% on 2022-10-09
I assuming here, a fresh install then the audio session change, but did the sound work from the Live Installer?

---

### Post by efricha on 2022-10-09
> **1fallen said:**
> I assuming here, a fresh install then the audio session change, but did the sound work from the Live Installer?

I didn't try.  Since I've now taken all my addon packages and set them up in a script, I reverted to 20.04 LTS.  *Voila! * Sound.

Alsa library version 1.2.2


Oh, BTW, I suspect that the live CD wouldn't have worked, just because of the /etc/modprobe.d/alsa-base.conf settings on it.  I know I could jump through the hoops of making an ISO with a modified alsa-base.conf, my 22.04 install **_DID_** work for a week until the update got pushed.

---

### Post by efricha on 2022-10-10
I don't want to walk away and call this [SOLVED] or even [RESOLVED].   As it stands, the tip of Ubuntu 22.04 LTS distros doesn't work with USB audio.  From linuxquestions, it's clearly not a unique problem to me.  Over on the ALSA home page, they seem unaware of the problem, or of the interaction with PulseAudio.  I suspect that if I file a bug, everyone will point the finger at someone else.

So:
* Any way to bring this issue up with the folks behind Ubuntu?  They might be able to use their influence.
* Any thoughts on getting ALSA to pay attention?

---

### Post by #&amp;thj^% on 2022-10-10
> **efricha said:**
>  I suspect that if I file a bug, everyone will point the finger at someone else.

So:
* Any way to bring this issue up with the folks behind Ubuntu?  They might be able to use their influence.

I think a bug should be filed. at least the legwork will be started.
> **efricha said:**
> 
* Any thoughts on getting ALSA to pay attention?
Out of curiosity have you tried to **copy **or **link **"/usr/share/doc/pipewire/examples/alsa.conf.d/99-pipewire-default.conf" to "/etc/alsa/conf.d"
Providing that no Pulseaudio enabled and pipewire-audio-client is installed and being used.
BTW Thanks for you willingness and effort to try to get to bottom of this problem.

---

### Post by efricha on 2022-10-10
> **1fallen said:**
> Out of curiosity have you tried to **copy **or **link **"/usr/share/doc/pipewire/examples/alsa.conf.d/99-pipewire-default.conf" to "/etc/alsa/conf.d"
Providing that no Pulseaudio enabled and pipewire-audio-client is installed and being used.
BTW Thanks for you willingness and effort to try to get to bottom of this problem.

Yes.  No dice.  Dinked around with it a little, too.

Note that this is a problem seen exclusively with USB devices.  My on-board sound -- which sucks -- was working happily even as PulseAudio was pointing to the USB DAC as the default sink.

---

