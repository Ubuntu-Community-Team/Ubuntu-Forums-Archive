---
title: "xawtv failure, BT878 chipset, failed only after installing Zoneminder 1.24.1 source"
date: 2009-06-16
forum: Multimedia Software
---

### Post by Jim March on 2009-06-16
Folks, I'm tearing my hair out here.

xawtv worked when I first started with a clean install of Intrepid 32bit standard desktop.  Got a good signal out of the camera, kewl.

I then followed these instructions for Zoneminder "from source" - note that this does create a .deb file for ZM:

[http://www.zoneminder.com/wiki/index.php/Ubuntu_8.10_Vanilla_32bit_(with_FFmpeg_SVN%2C_ZoneMinder_SVN%2C_jscalendar-1.0%2C_cambozola-0.7)](http://www.zoneminder.com/wiki/index.php/Ubuntu_8.10_Vanilla_32bit_(with_FFmpeg_SVN%2C_ZoneMinder_SVN%2C_jscalendar-1.0%2C_cambozola-0.7))

After much wailing and gnashing of teeth I got all this stuff running.  And no, DO NOT tell me to use standard repo Zoneminder packages, they're completely messed up.  Let's just not go there, m'kay?  "Steaming pile" doesn't even begin.

So OK, everything SHOULD run, but it doesn't. Nothing on the camera.  On a hunch I go back and check Xawtv again and it's massively puked and died.  Here's what it looks like now:

```
zmuser@zmuser-camerastation:~$ xawtv -device /dev/video0
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.27-14-generic)
xinerama 0: 1280x1024+0+0
WARNING: No DGA direct video mode for this display.
WARNING: couldn't find framebuffer base address, try manual
         configuration ("v4l-conf -a <addr>")
v4l2: WARNING: framebuffer base address mismatch
v4l2: me=(nil) v4l=(nil)
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct
ioctl: VIDIOC_QBUF(index=0;type=VIDEO_CAPTURE;bytesused=0;flags=0x0 [];field=ANY;;timecode.type=0;timecode.flags=0;timecode.frames=0;timecode.seconds=0;timecode.minutes=0;timecode.hours=0;timecode.userbits="";sequence=0;memory=MMAP): Device or resource busy
libv4l2: error turning on stream: Device or resource busy
ioctl: VIDIOC_STREAMON(int=1): Device or resource busy
ioctl: VIDIOC_QBUF(index=0;type=VIDEO_CAPTURE;bytesused=0;flags=0x0 [];field=ANY;;timecode.type=0;timecode.flags=0;timecode.frames=0;timecode.seconds=0;timecode.minutes=0;timecode.hours=0;timecode.userbits="";sequence=0;memory=MMAP): Device or resource busy
libv4l2: error dequeuing buf: Invalid argument
ioctl: VIDIOC_DQBUF(index=0;type=VIDEO_CAPTURE;bytesused=0;flags=0x0 [];field=ANY;;timecode.type=0;timecode.flags=0;timecode.frames=0;timecode.seconds=0;timecode.minutes=0;timecode.hours=0;timecode.userbits="";sequence=0;memory=MMAP): Invalid argument
v4l2: read: Device or resource busy
zmuser@zmuser-camerastation:~$
```

OK...I actually have two different BT878 cards, I swap 'em, I try different physical ports on the cards, nothing doing.  Yet everything looks OK under a Xawtv hardware scan:

```
zmuser@zmuser-camerastation:~$ xawtv -hwscan
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.27-14-generic)
looking for available devices
port 355-386
    type : Xvideo, image scaler
    name : NV17 Video Texture

port 387-418
    type : Xvideo, image scaler
    name : NV05 Video Blitter

/dev/video0: OK                         [ -device /dev/video0 ]
    type : v4l2
    name : BT878 video (Hauppauge (bt878))
    flags: overlay capture tuner 

zmuser@zmuser-camerastation:~$
```

And in /var/log/dmesg the BT878 startup stuff looks OK to me at least...

```
[   15.520742] Bt87x 0000:01:0a.1: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
[   15.520764] Bt87x 0000:01:0a.1: setting latency timer to 64
[   15.520948] bt87x0: Using board 1, analog, digital (rate 32000 Hz)
[   15.821931] Linux video capture interface: v2.00
[   15.876181] bttv: driver version 0.9.17 loaded
[   15.876185] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   15.877551] bttv: Bt8xx card found (0).
[   15.877569] bttv 0000:01:0a.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
[   15.877578] bttv0: Bt878 (rev 17) at 0000:01:0a.0, irq: 18, latency: 16, mmio: 0xfdfff000
[   15.877591] bttv0: detected: Hauppauge WinTV [card=10], PCI subsystem ID is 0070:13eb
[   15.877594] bttv0: using: Hauppauge (bt878) [card=10,autodetected]
[   15.877621] bttv0: gpio: en=00000000, out=00000000 in=00ffffff [init]
[   15.880108] bttv0: Hauppauge/Voodoo msp34xx: reset line init [5]
[   15.907234] tveeprom 0-0050: Hauppauge model 64405, rev C1  , serial# 10327899
[   15.907237] tveeprom 0-0050: tuner model is Unspecified (idx 2, type 4)
[   15.907240] tveeprom 0-0050: TV standards UNKNOWN (eeprom 0x01)
[   15.907242] tveeprom 0-0050: audio processor is None (idx 0)
[   15.907245] tveeprom 0-0050: decoder processor is BT878 (idx 14)
[   15.907247] tveeprom 0-0050: has no radio
[   15.907249] bttv0: Hauppauge eeprom indicates model#64405
[   15.907251] bttv0: tuner absent
[   15.907254] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   16.052268] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   16.068140] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   16.080153] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   16.144705] bttv0: registered device video0
[   16.144753] bttv0: registered device vbi0
[   16.144773] bttv0: PLL: 28636363 => 35468950 .. ok
```

Does anybody know why in God's name Xawtv might have broke?  Really need to make this work :(.

---

### Post by r-daneel on 2009-07-11
Hi,

I was having some strange behaviour with quite the same bttv hardware.
Was working fine on ubuntu 8.04 LTS and now I am trying to use it in another pc with a fresh installed ubuntu 9.04.

Nothing on video output.

First, I discovered my user was not part of the "video" group.
This was resolved by going to user and groups management in the system menu and checking the boxe to allow access to tv and webcam video (this is in approximative french locale, couldn't say what exactly it is in english).

Second, I discovered that the /dev/video0 was busy, using "lsof /dev/video0" (lsof seems to be installed by default on ubuntu 9.04 (at least when installed from dvd)).

Killing the running task (in my case xawtv.bin) resolved the problem.

Now it seems to be working again.

For the tests, I used xawtv too.

The hint comes from the message :
v4l2: read: Device or resource busy

Well, hope that helps a bit ...

---

