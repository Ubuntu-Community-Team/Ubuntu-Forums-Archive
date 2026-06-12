---
title: "DVB: ASUS MyCinema U3000 mini stopped working."
date: 2011-12-01
forum: Multimedia Software
---

### Post by negora on 2011-12-01
Hello:

My case is really weird. I've been using an ASUS MyCinema U3000 mini (an USB dongle to watch DVB-T) successfully for a long time. It didn't matter which version of Ubuntu (Ubuntu, Xubuntu and Lubuntu) or architecture I used (32 or 64 bit). Everything was OK and I was a happy user.

It has been so until 3 days ago, when I decided to test Linux Mint (which employs the Ubuntu kernel, of course). I tried to scan for channels, using the programs "scan" and "w_scan", but they didn't find (almost) anything.

Under these circumstances, today I've decided to get back to Xubuntu again. But, surprisingly, I'm being unable to make it work too. I've installed Lubuntu a little later, with the same results exactly.

Firstly, I've thought that the DVB device might be broken. However, it's recognized by the system and, when I scan, it finds out the right TV transponders of my town. Indeed, it detects and tune 5 channels (2 TV's and 3 radio's). I can watch and listen them properly. But the others channels are "lost".

Later I've considered that it might have something to do with the firmware or the drivers included with the kernel 3.0. But the version of Lubuntu which I've installed today is 11.04 (which worked fine 2 months ago) and also fails :S .

When I execute "w_scan", except for one transponder (the one which "contains" those 5 channels), I get many of these errors:

> Info: NIT(other) filter timeout

This could mean that something is wrong with the DVB signal. However I've been able to tune up the signal with an usual TV. Also, I've tested this dongle on a different computer, in a different place (in the same area and town) but, again, it failed the tunning whereas another TV worked without a problem.

Sincerely, I've no idea why it's happening. Any idea?
Thank you very much for your help :) .


TAGS: dvb dib0700 asus mycinema u3000 mini w_scan scan nit

---

### Post by negora on 2011-12-02
I'd like clarifying something which I consider relevant. At home I'm able to get channels for a single transponder (excuse me if the therm is not right). However, at the other place where I've tested my DVB dongle, I get channels for a completely different transponder. :confused: I believe that it's really weird. It's always the same transponder on each place. Both places are in the same area, in the same town.

Apart of this, I remember that, when I was able to tune all TV channels of my area, sometimes I suffered from a problem similar to this one. However, I repeated the channel scan (using w_scan or MythTV) and got all the channels again.

I've no idea about these technologies, but taking into account the messages which I get from w_scan, Could it be that "something" has changed in the TV signal itself?

---

### Post by negora on 2011-12-02
Well, it's not a fault in the TV signal. I've just installed Windows 7 with the official drivers and it works flawless: every channel is tuned.

I'm happy because it discards a problem in the signal or the DVB device. But now, I'm more confused. Why a clean and new installation of Ubuntu/Xubuntu/Lubuntu, that has always worked for me, doesn't work now? :S

I'll keep investigating. By now I'm going to make a copy of this Windows 7 installation with Clonezilla before reinstalling Ubuntu, just in case that I need to take it back temporally.

---

### Post by arisp on 2011-12-02
Could you post the output of w_scan and any relevant parts of dmesg (look for dvb, dib0700, and dvb-usb lines), "lsusb -vv" and "lsmod | grep dvb"
I suppose that you tested windows on the same hardware and same antenna/location etc? (just to rule out simple bad reception)

---

### Post by negora on 2011-12-02
**arisp:** thanks for answering :) .

I think that's the first thing which I should have written before starting to ramble, he he he. This DVB dongle is based on the dib0700 chip. This is part of the "dmesg" output:

```
[  199.852603] dib0700: loaded with support for 20 different device-types
[  199.852891] dvb-usb: found a 'ASUS My Cinema U3000 Mini DVBT Tuner' in warm state.
[  199.853016] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[  199.853298] DVB: registering new adapter (ASUS My Cinema U3000 Mini DVBT Tuner)
[  200.071269] DVB: registering adapter 0 frontend 0 (DiBcom 7000PC)...
[  200.075185] MT2266: successfully identified
[  200.234817] Registered IR keymap rc-dib0700-rc5
[  200.235440] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1d.7/usb1/1-2/rc/rc1/input16
[  200.235761] rc1: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1d.7/usb1/1-2/rc/rc1
[  200.235952] dvb-usb: schedule remote query interval to 50 msecs.
[  200.235971] dvb-usb: ASUS My Cinema U3000 Mini DVBT Tuner successfully initialized and connected.
[  200.236414] dib0700: rc submit urb failed
[  200.236423] 
[  200.236574] usbcore: registered new interface driver dvb_usb_dib0700

```

I'll try to send a more complete output tomorrow, since I'm accessing the computer remotely and can't unplug and plug the USB device to catch a "clean" trace.

And this is the result of executing "w_scan -c ES". Curiously, just now it hasn't found any channel :S :

```
w_scan version 20110616 (compiled for DVB API 5.3)
using settings for SPAIN
DVB aerial
DVB-T Europe
frontend_type DVB-T, channellist 4
output format vdr-1.6
WARNING: could not guess your codepage. Falling back to 'UTF-8'
output charset 'UTF-8', use -C <charset> to override
Info: using DVB adapter auto detection.
	/dev/dvb/adapter0/frontend0 -> DVB-T "DiBcom 7000PC": good :-)
Using DVB-T frontend (adapter /dev/dvb/adapter0/frontend0)
-_-_-_-_ Getting frontend capabilities-_-_-_-_ 
Using DVB API 5.3
frontend 'DiBcom 7000PC' supports
INVERSION_AUTO
QAM_AUTO
TRANSMISSION_MODE_AUTO
GUARD_INTERVAL_AUTO
HIERARCHY_AUTO
FEC_AUTO
FREQ (174.00MHz ... 862.00MHz)
-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_ 
Scanning 7MHz frequencies...
177500: (time: 00:00) 
184500: (time: 00:03) 
191500: (time: 00:06) 
198500: (time: 00:09) 
205500: (time: 00:12) 
212500: (time: 00:15) 
219500: (time: 00:18) 
226500: (time: 00:21) 
Scanning 8MHz frequencies...
474000: (time: 00:25) (time: 00:26) signal ok:
	QAM_AUTO f = 474000 kHz I999B8C999D999T999G999Y999
Info: NIT(actual) filter timeout
482000: (time: 00:40) (time: 00:41) signal ok:
	QAM_AUTO f = 482000 kHz I999B8C999D999T999G999Y999
Info: NIT(actual) filter timeout
490000: (time: 00:56) 
498000: (time: 00:59) 
506000: (time: 01:02) 
514000: (time: 01:05) 
522000: (time: 01:08) (time: 01:09) signal ok:
	QAM_AUTO f = 522000 kHz I999B8C999D999T999G999Y999
Info: NIT(actual) filter timeout
530000: (time: 01:24) 
538000: (time: 01:28) 
546000: (time: 01:31) 
554000: (time: 01:34) 
562000: (time: 01:37) 
570000: (time: 01:40) 
578000: (time: 01:43) 
586000: (time: 01:46) 
594000: (time: 01:49) 
602000: (time: 01:52) 
610000: (time: 01:55) 
618000: (time: 01:58) 
626000: (time: 02:01) 
634000: (time: 02:05) 
642000: (time: 02:08) 
650000: (time: 02:11) 
658000: (time: 02:14) 
666000: (time: 02:17) (time: 02:18) signal ok:
	QAM_AUTO f = 666000 kHz I999B8C999D999T999G999Y999
Info: NIT(actual) filter timeout
674000: (time: 02:33) 
682000: (time: 02:36) 
690000: (time: 02:39) 
698000: (time: 02:42) 
706000: (time: 02:45) 
714000: (time: 02:48) 
722000: (time: 02:51) 
730000: (time: 02:54) 
738000: (time: 02:57) 
746000: (time: 03:00) 
754000: (time: 03:03) 
762000: (time: 03:06) (time: 03:07) signal ok:
	QAM_AUTO f = 762000 kHz I999B8C999D999T999G999Y999
Info: NIT(actual) filter timeout
770000: (time: 03:22) (time: 03:23) signal ok:
	QAM_AUTO f = 770000 kHz I999B8C999D999T999G999Y999
Info: NIT(actual) filter timeout
778000: (time: 03:38) 
786000: (time: 03:41) 
794000: (time: 03:44) 
802000: (time: 03:47) 
810000: (time: 03:50) 
818000: (time: 03:53) 
826000: (time: 03:56) 
834000: (time: 03:59) 
842000: (time: 04:02) (time: 04:03) signal ok:
	QAM_AUTO f = 842000 kHz I999B8C999D999T999G999Y999
Info: NIT(actual) filter timeout
850000: (time: 04:18) (time: 04:19) signal ok:
	QAM_AUTO f = 850000 kHz I999B8C999D999T999G999Y999
Info: NIT(actual) filter timeout
858000: (time: 04:34) (time: 04:35) signal ok:
	QAM_AUTO f = 858000 kHz I999B8C999D999T999G999Y999
Info: NIT(actual) filter timeout
tune to: QAM_AUTO f = 474000 kHz I999B8C999D999T999G999Y999 
(time: 04:49) Info: PAT filter timeout
Info: SDT(actual) filter timeout
Info: NIT(actual) filter timeout
tune to: QAM_AUTO f = 482000 kHz I999B8C999D999T999G999Y999 
(time: 05:04) Info: PAT filter timeout
Info: SDT(actual) filter timeout
Info: NIT(actual) filter timeout
tune to: QAM_AUTO f = 522000 kHz I999B8C999D999T999G999Y999 
(time: 05:19) Info: PAT filter timeout
Info: SDT(actual) filter timeout
Info: NIT(actual) filter timeout
tune to: QAM_AUTO f = 666000 kHz I999B8C999D999T999G999Y999 
(time: 05:34) Info: PAT filter timeout
Info: SDT(actual) filter timeout
Info: NIT(actual) filter timeout
tune to: QAM_AUTO f = 762000 kHz I999B8C999D999T999G999Y999 
(time: 05:49) Info: PAT filter timeout
Info: SDT(actual) filter timeout
Info: NIT(actual) filter timeout
tune to: QAM_AUTO f = 770000 kHz I999B8C999D999T999G999Y999 
(time: 06:04) Info: PAT filter timeout
Info: SDT(actual) filter timeout
Info: NIT(actual) filter timeout
tune to: QAM_AUTO f = 842000 kHz I999B8C999D999T999G999Y999 
(time: 06:19) Info: PAT filter timeout
Info: SDT(actual) filter timeout
Info: NIT(actual) filter timeout
tune to: QAM_AUTO f = 850000 kHz I999B8C999D999T999G999Y999 
(time: 06:33) ----------no signal----------
tune to: QAM_AUTO f = 850000 kHz I999B8C999D999T999G999Y999  (no signal)
(time: 06:35) Info: PAT filter timeout
Info: SDT(actual) filter timeout
Info: NIT(actual) filter timeout
tune to: QAM_AUTO f = 858000 kHz I999B8C999D999T999G999Y999 
(time: 06:50) Info: PAT filter timeout
Info: SDT(actual) filter timeout
Info: NIT(actual) filter timeout
dumping lists (0 services)
Done.


```

There's something interesting too. I'm not sure if it happened on previous versions of Ubuntu, but I've found that in the default installation there's a firmware file called /lib/firmware/dvb-usb-dib0700-1.20.fw . If I install the package "linux-firmware-nonfree", it stores a new firmware called "/lib/firmware/dvb-usb-dib0700-1.10.fw". When I was able to make the dongle work in the past, I always installed this package. However, I've realized that although I install this pack, the driver always use the version 1.20. Yesterday I tried to move this file to another place and make a soft link which points to the version 1.10 (to trick the driver) but the results were exactly the same.

It's an absolute mess :S .

---

### Post by negora on 2011-12-02
This is the "lsmod" output (filtered using "sort"):

```
ahci                   26002  2 
arc4                   12529  2 
asus_wmi               20035  1 eeepc_wmi
atl1c                  41643  0 
bcma                   20219  0 
binfmt_misc            17540  1 
bluetooth             166112  10 rfcomm,bnep
bnep                   18436  2 
brcmsmac              631693  0 
brcmutil               17837  1 brcmsmac
cfg80211              199587  2 brcmsmac,mac80211
crc_ccitt              12667  1 brcmsmac
dib0070                18434  1 dvb_usb_dib0700
dib0090                33392  1 dvb_usb_dib0700
dib3000mc              23392  1 dvb_usb_dib0700
dib7000m               23415  1 dvb_usb_dib0700
dib7000p               39109  2 dvb_usb_dib0700
dib8000                43019  1 dvb_usb_dib0700
dibx000_common         14574  5 dvb_usb_dib0700,dib7000p,dib7000m,dib8000,dib3000mc
dvb_core              110616  3 dib7000p,dvb_usb,dib8000
dvb_usb                24444  1 dvb_usb_dib0700
dvb_usb_dib0700       114669  0 
eeepc_wmi              12826  0 
ir_jvc_decoder         12546  0 
ir_lirc_codec          12898  0 
ir_nec_decoder         12546  0 
ir_rc5_decoder         12546  0 
ir_rc6_decoder         12546  0 
ir_sony_decoder        12549  0 
joydev                 17693  0 
lib80211               14991  1 wl
libahci                26861  1 ahci
lirc_dev               19204  1 ir_lirc_codec
lp                     17799  0 
mac80211              310872  1 brcmsmac
Module                  Size  Used by
mt2266                 13377  1 
nvidia              11713772  33 
parport                46562  3 parport_pc,ppdev,lp
parport_pc             36962  0 
ppdev                  17113  0 
psmouse                73882  0 
rc_core                26963  10 rc_dib0700_rc5,ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,dvb_usb_dib0700,dvb_usb
rc_dib0700_rc5         12508  0 
rfcomm                 47946  0 
serio_raw              13166  0 
snd                    68266  22 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hda_codec_hdmi     32040  4 
snd_hda_codec_realtek   330769  1 
snd_hda_intel          33390  6 
snd_hwdep              13668  1 snd_hda_codec
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
snd_pcm                96755  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_rawmidi            30547  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_timer              29991  2 snd_pcm,snd_seq
soundcore              12680  1 snd
sparse_keymap          13890  1 asus_wmi
uvcvideo               72711  0 
v4l2_compat_ioctl32    17083  1 videodev
vesafb                 13809  1 
video                  19412  0 
videodev               93004  1 uvcvideo
wl                   2568210  0 
wmi                    19256  1 asus_wmi

```

And the "lsusb -vv" output:

```
Bus 001 Device 002: ID 0b05:171f ASUSTek Computer, Inc. My Cinema U3000 Mini [DiBcom DiB7700P]
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0b05 ASUSTek Computer, Inc.
  idProduct          0x171f My Cinema U3000 Mini [DiBcom DiB7700P]
  bcdDevice            1.00
  iManufacturer           1 DIBCOM
  iProduct                2 STK7700
  iSerial                 3 6A00204179
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
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval              10
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)

```

---

### Post by arisp on 2011-12-03
Everything looks ok on what you posted and w_scan finds the transponders. It just can't get the services.
Have you tried using kaffeine to tune the channels?

---

### Post by negora on 2011-12-03
Hello again :) .

I've just installed Kaffeine and the result is exactly the same: it only gets channels for 1 transponder.

By the way, I've tried to play the found channels and, surprisingly, they don't work. So the practical difference between finding nothing and this single transponder is none. It's useless.

This noon I'm going to do a clean install of Lubuntu 11.04 again (not the version 11.10), because it was the one which I was using when everything worked fine. I'm going to insist and do every kind of test. If this doesn't work either, definitively I'm considering this a X file :P .

---

### Post by negora on 2011-12-03
It's really depressing. I've not had any luck with a fresh install of Lubuntu 11.04. This version was the one which was I was using successfully before installing the others.

In my opinion, the only possible reason is that the package "linux-firmware-nonfree" or "w-scan" (which I'm forced to download from the repositories for not being included in the disc) has been replaced with a faulty version.

---

### Post by negora on 2011-12-03
I've interesting news. Checking my portable disk, where I save disk images from time to time to avoid reinstalling, I've found one of Linux Mint 12 RC (which uses the kernel 3.0.12). **This was for one test which I did when everything still worked.**

I've recovered this disk image using Clonezilla and I've got shocked, because I've checked that, when I run this OS in the past, MythTV was able to get channels. Not all, but many of them are there. However, when I've tried to watch the TV, these channels failed.

So, definitively, this changes my last considerations. Summarising:

1.  The OS versions which worked time ago don't work now. Even old installations which worked in the past and have not been modified since then. So, it's very probably that Linux is not the responsible. Right?

2. Windows 7 is able to scan channels.

3. The device worked in Linux and works in Windows now, so it's not faulty or defective. Nothing has changed inside of it.

4. The only remaining suspect would be the signal. But why and how?

I'm going to reinstall Windows 7 and check if I can check the tuning parameters which Windows Media Center employs.

---

### Post by askandres on 2012-01-09
Hi, I just bought the u3000 mini but have been in troubles trying to get it to work on win7. Do you have any special way to install it? is there any driver available for win7? I would really appreciate if you could tell me how did you made it work on win7.

Thanks

---

### Post by askandres on 2012-01-09
Hi

I bought a my cinema u3000 mini but can not get it work in win7, I would appreciate if I could get some guidance regarding this issue. Are there any drivers compatible with win7? 

If anyone have managed to get the u3000 mini working on win7 I would appreciate some advise.

Thanks!

---

### Post by TheLittleDeath on 2012-04-14
I solved the problem by buying a new DVB-T stick. But it took me ages to figure out it was broken. Because it was working from time to time. All I had was that error message and no solution on the web.

---

