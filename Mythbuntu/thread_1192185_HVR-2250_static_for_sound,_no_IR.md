---
title: "HVR-2250 static for sound, no IR"
date: 2009-06-19
forum: Mythbuntu
---

### Post by juicedM3 on 2009-06-19
I'm currently having problems with the HVR-2250 card I recently purchased.  I followed LowSky's guide to install it and things looked great.  The guide definitely saved me a lot of time so thanks for posting it LowSky!

I am able to watch TV but the sound is all static.  I'm not sure where to start there.  I currently run all video and audio over HDMI.

Then I have a secondary problem that the IR receiver doesn't work.  The newer HVR-2250s (rev C3F2) have an IR receiver that you plug into the card.  It's no longer the separate USB module.  I see some messages about errors with i2c and I think that's related.

Here's a bunch of info about my system:

Hardware:

Asus M3N78 PRO mobo
Realtek ALC1200 audio
NVIDIA GeForce 8300
Hauppauge HVR-2250 rev C3F2

OS:

Mythbuntu 8.10
Kernel 2.6.27-14

Drivers:

ALSA 1.0.20
NVidia 180.11.02
SAA7164 stable

From dmesg:

```

[   10.591494] saa7164 driver loaded
[   10.591553] saa7164 0000:05:00.0: PCI INT A -> Link[AE3A] -> GSI 16 (level, low) -> IRQ 16
[   10.591899] CORE saa7164[0]: dev->lmmio  = 0xffffc20005180000
[   10.591901] CORE saa7164[0]: dev->lmmio2 = 0xffffc20005600000
[   10.591903] CORE saa7164[0]: dev->bmmio  = 0xffffc20005180000
[   10.591904] CORE saa7164[0]: dev->bmmio2 = 0xffffc20005600000
[   10.591907] CORE saa7164[0]: subsystem: 0070:8891, board: Hauppauge WinTV-HVR2250 [card=7,autodetected]
[   10.591912] saa7164[0]/0: found at 0000:05:00.0, rev: 129, irq: 16, latency: 0, mmio: 0xfd000000
[   10.591917] saa7164 0000:05:00.0: setting latency timer to 64
[   10.748018] saa7164_downloadfirmware() no first image
[   10.748084] saa7164_downloadfirmware() Waiting for firmware upload (v4l-saa7164-1.0.3.fw)
[   10.748087] firmware: requesting v4l-saa7164-1.0.3.fw
[   10.939017] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 20
[   10.939022] HDA Intel 0000:00:07.0: PCI INT A -> Link[AAZA] -> GSI 20 (level, low) -> IRQ 20
[   10.939040] HDA Intel 0000:00:07.0: setting latency timer to 64
[   11.573986] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:07.0/input/input4
[   12.374816] saa7164_downloadfirmware() firmware read 3978608 bytes.
[   12.374819] saa7164_downloadfirmware() firmware loaded.
[   12.374821] Firmware file header part 1:
[   12.374823]  .FirmwareSize = 0x0
[   12.374824]  .BSLSize = 0x0
[   12.374825]  .Reserved = 0x3cb57
[   12.374826]  .Version = 0x3
[   12.374827] saa7164_downloadfirmware() SecBootLoader.FileSize = 3978608
[   12.374833] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[   12.374834] saa7164_downloadfirmware() BSLSize = 0x0
[   12.374835] saa7164_downloadfirmware() Reserved = 0x0
[   12.374837] saa7164_downloadfirmware() Version = 0x51cc1
[   19.228018] saa7164_downloadimage() Image downloaded, booting...
[   19.332018] saa7164_downloadimage() Image booted successfully.
[   19.332039] starting firmware download(2)
[   21.376017] saa7164_downloadimage() Image downloaded, booting...
[   23.040019] saa7164_downloadimage() Image booted successfully.
[   23.040048] firmware download complete.
[   23.041156] saa7164[0]: i2c bus 0 registered
[   23.041179] saa7164[0]: i2c bus 1 registered
[   23.041201] saa7164[0]: i2c bus 2 registered
[   23.077969] tveeprom 0-0000: Hauppauge model 88061, rev C3F2, serial# 6224574
[   23.077972] tveeprom 0-0000: MAC address is 00-0D-FE-5E-FA-BE
[   23.077974] tveeprom 0-0000: tuner model is NXP 18271C2_716x (idx 152, type 4)
[   23.077977] tveeprom 0-0000: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[   23.077979] tveeprom 0-0000: audio processor is SAA7164 (idx 43)
[   23.077981] tveeprom 0-0000: decoder processor is SAA7164 (idx 40)
[   23.077982] tveeprom 0-0000: has radio, has IR receiver, has no IR transmitter
[   23.077984] saa7164[0]: Hauppauge eeprom: model=88061
[   23.486401] tda18271 1-0060: creating new instance
[   23.490510] TDA18271HD/C2 detected @ 1-0060
[   23.740722] DVB: registering new adapter (saa7164)
[   23.740727] DVB: registering adapter 0 frontend 0 (Samsung S5H1411 QAM/8VSB Frontend)...
[   24.021980] tda18271 2-0060: creating new instance
[   24.026015] TDA18271HD/C2 detected @ 2-0060
[   24.276800] DVB: registering new adapter (saa7164)
[   24.276804] DVB: registering adapter 1 frontend 0 (Samsung S5H1411 QAM/8VSB Frontend)...

[   48.225643] tda18271: RF tracking filter calibration complete
[   49.051966] lirc_dev: IR Remote Control driver registered, major 61
[   49.063613] tda18271: performing RF tracking filter calibration
[   49.079639]
[   49.079647] lirc_mceusb2: Philips eHome USB IR Transceiver and Microsoft MCE 2005 Remote Control driver for LIRC $Re
vision: 1.44 $
[   49.079650] lirc_mceusb2: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>
[   49.081951] usbcore: registered new interface driver lirc_mceusb2
[   52.417338] tda18271: RF tracking filter calibration complete

[  127.532046] Event timed out
[  127.532055] saa7164_api_i2c_read() error, ret(1) = 0x32
[  127.532057] s5h1411_readreg: readreg error (ret == -5)
[  127.532461] found timed out command on the bus
[  127.532483] ret = 0
[  127.532485]  timeout continue

```

```

$ lsusb
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

```

$ cat /proc/modules | grep lirc
lirc_mceusb2 21764 0 - Live 0xffffffffa0c89000
lirc_dev 22216 1 lirc_mceusb2, Live 0xffffffffa0c82000
usbcore 175760 5 usbhid,lirc_mceusb2,ehci_hcd,ohci_hcd, Live 0xffffffffa004d000

```

```

$ lsmod | grep lirc
lirc_mceusb2           21764  0
lirc_dev               22216  1 lirc_mceusb2
usbcore               175760  5 usbhid,lirc_mceusb2,ehci_hcd,ohci_hcd

```

```

$ ls /dev/lirc*
/dev/lircd

```

```

$ sudo cat /proc/bus/input/devices
I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input0
U: Uniq=
H: Handlers=mouse0 event0
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=3

I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
U: Uniq=
H: Handlers=kbd event1
B: EV=3
B: KEY=10000000000000 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
U: Uniq=
H: Handlers=kbd event2
B: EV=3
B: KEY=10000000000000 0

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/devices/platform/pcspkr/input/input3
U: Uniq=
H: Handlers=kbd event3
B: EV=40001
B: SND=6

I: Bus=0001 Vendor=10ec Product=0888 Version=0001
N: Name="HDA Digital PCBeep"
P: Phys=card0/codec#0/beep0
S: Sysfs=/devices/pci0000:00/0000:00:07.0/input/input4
U: Uniq=
H: Handlers=kbd event4
B: EV=40001
B: SND=6

I: Bus=0003 Vendor=046d Product=c517 Version=0110
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:04.0-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:04.0/usb2/2-2/2-2:1.0/input/input5
U: Uniq=
H: Handlers=kbd event5
B: EV=120013
B: KEY=1000000000007 ff800000000007ff febeffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=1f

I: Bus=0003 Vendor=046d Product=c517 Version=0110
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:04.0-2/input1
S: Sysfs=/devices/pci0000:00/0000:00:04.0/usb2/2-2/2-2:1.1/input/input6
U: Uniq=
H: Handlers=kbd mouse1 event6
B: EV=1f
B: KEY=837fff042c332f bf08444400000000 ff0001 1f848a37cc00 667bfadd71dfed 9e000000000000 0
B: REL=1c3
B: ABS=100000000
B: MSC=10

```

I know the device is not located at /dev/lirc0.  For now, it's not located anywhere but here's the failure in the daemon.log.

```

Jun 19 19:52:10 mythzilla lircd-0.8.3[8255]: lircd(userspace) ready
Jun 19 19:52:16 mythzilla lircd-0.8.3[8255]: accepted new client on /dev/lircd
Jun 19 19:52:16 mythzilla lircd-0.8.3[8255]: could not get file information for /dev/lirc0
Jun 19 19:52:16 mythzilla lircd-0.8.3[8255]: default_init(): No such file or directory
Jun 19 19:52:16 mythzilla lircd-0.8.3[8255]: caught signal

```

```

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

```

$ cat /etc/asound.conf
defaults.pcm.device 3

```

From my mythfrontend.log when I try to watch TV:

```

2009-06-19 20:06:57.600 TV: Attempting to change from None to WatchingLiveTV
2009-06-19 20:06:57.600 Using protocol version 40
2009-06-19 20:06:58.800 NVP: Disabling Audio, params(-1,2,44100)
2009-06-19 20:06:58.801 DPMS Deactivated
2009-06-19 20:06:58.811 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-06-19 20:06:58.834 OSD Theme Dimensions W: 640 H: 480
2009-06-19 20:06:59.009 Realtime priority would require SUID as root.
2009-06-19 20:06:59.009 TV: Changing from None to WatchingLiveTV
2009-06-19 20:06:59.109 Video timing method: USleep with busy wait
2009-06-19 20:07:03.004 NVP: Prebuffer wait timed out 10 times.
2009-06-19 20:07:04.704 VideoOutputXv Error: XvMC output requested, but is not supported by display.
Xlib:  extension "XVideo-MotionCompensation" missing on display ":0.0".
2009-06-19 20:07:04.709 VideoOutputXv: Desired video renderer 'xvmc-blit' not available.
                        codec 'MPEG2' makes 'xv-blit,xshm,opengl,xlib,' available, using 'xv-blit' instead.
2009-06-19 20:07:04.711 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-06-19 20:07:04.924 AFD: Opened codec 0x7f9187c3ded0, id(MPEG2VIDEO) type(Video)
2009-06-19 20:07:04.925 AFD: codec AC3 has 6 channels
2009-06-19 20:07:04.925 AFD: Opened codec 0x7f9187c267e0, id(AC3) type(Audio)
2009-06-19 20:07:04.925 AFD: codec AC3 has 1 channels
2009-06-19 20:07:04.926 AFD: Opened codec 0x7f9187af0f00, id(AC3) type(Audio)
2009-06-19 20:07:04.931 AFD: Opened codec 0x7f918411f9a0, id(MPEG2VIDEO) type(Video)
2009-06-19 20:07:05.064 Opening audio device 'default'. ch 6(2) sr 48000
2009-06-19 20:07:05.064 Opening ALSA audio device 'default'.
2009-06-19 20:07:05.071 NVP: Prebuffer wait timed out 10 times.
2009-06-19 20:07:05.075 Mixer unable to find control PCM 2
2009-06-19 20:07:05.075 Mixer unable to find control PCM 3
2009-06-19 20:07:05.075 Mixer unable to find control PCM 4
2009-06-19 20:07:05.075 Mixer unable to find control PCM 5
2009-06-19 20:07:05.075 mixer unable to find control Master 1
2009-06-19 20:07:05.076 NVP: Enabling Audio
2009-06-19 20:07:05.079 Opening audio device 'default'. ch 2(2) sr 48000
2009-06-19 20:07:05.079 Opening ALSA audio device 'default'.
2009-06-19 20:07:05.087 mixer unable to find control Master 1

```

Hmm.. that's the first time I looked at the logs about my TV sound.  I'm surprised it can't find the default ALSA audio device but my videos and music can.  I've also tested DD & DTS and both of those formats work.

When I listen to music, similar output except for a few things:

```

2009-06-19 20:11:30.052 Opening audio device 'default'. ch 6(2) sr 44100
2009-06-19 20:11:30.052 Opening ALSA audio device 'default'.
2009-06-19 20:11:30.063 Mixer unable to find control PCM 2
2009-06-19 20:11:30.064 Mixer unable to find control PCM 3
2009-06-19 20:11:30.064 Mixer unable to find control PCM 4
2009-06-19 20:11:30.064 Mixer unable to find control PCM 5
2009-06-19 20:11:30.064 mixer unable to find control Master 1

```

Any help will be appreciated.  Let me know if you need any other information.  I'm going to keep looking around.

---

### Post by juicedM3 on 2009-06-20
I got the audio to work.  Sort of... I need to test if DD will work.  It's late on the east coast and not may stations play HD shows w/ AC3 at this hour.

Running my DD & DTS tests, it should still work.  I'd just like to see some DD from OTA.

I first tried the development branch of the saa7164 drivers.  But I was getting the same results.  I may just leave them installed unless they truly are unstable.

What did I do to get the audio to work through the HVR-2250?

I had to go to "Utilities/Setup" -> "Setup" -> "General" and then navigate over to the "Audio" screen.  I changed my Passthrough output device: to ALSA:iec958:{ AES0 0x02 }.  It was set to Default before.

So my settings are as follows (remember I'm running my audio and video through HDMI):

Audio output device: ALSA:default
Passthrough output device: ALSA:iec958:{AES0 0x02}
Max Audio Channels: 5.1

The other settings don't seem to make a difference for me.  It was that Passthrough setting that was killing my OTA audio.  But it has screwed with the audio in some of my video files.  I have a couple of video files that have the following errors:

```

[AO_ALSA] alsa-lib: pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM iec958
[AO_ALSA] Playback open error: No such file or directory
[AO OSS] Can't set audio device /dev/dsp to ac3 output, trying s16le...
AO: [oss] 48000Hz 2ch s16le (2 bytes per sample)
[format] Sample format big-endian AC3 not yet supported

```

At least it's a only couple for now.

Now to solve my IR problems...

---

### Post by juicedM3 on 2009-06-20
I just discovered that my statement "the other settings don't seem to make a difference for me" was a lie.  The setting "Enable AC3 to SPDIF passthrough" was the culprit.  I can set my Passthrough output device back to default after making sure the AC3 SPDIF passthrough is not selected.

I still haven't found any TV shows in DD.  Or at least my receiver hasn't recognized anything.  Maybe I should grab a coax cable and try the SPDIF passthrough for S&G.

I'm still (slowly) poking around to see if the on-board IR receiver will work.  Still looking for suggestions there.  Almost thinking of going out and buying a $20 remote w/ a USB IR receiver.

---

### Post by Levander on 2009-08-24
juicedM3, did you ever get the on-board IR receiver to work?  

I'm looking at buying an HVR-2250 now and can save twenty bucks if I get the version without all the IR stuff.

---

### Post by juicedM3 on 2009-08-26
> **Levander said:**
> juicedM3, did you ever get the on-board IR receiver to work?  

I'm looking at buying an HVR-2250 now and can save twenty bucks if I get the version without all the IR stuff.

Nope.  I never got it to work.  My C is too rusty and I started screwing things up.  I have some down time coming up so I might take a crack at it again.

Justin

---

### Post by juicedM3 on 2009-08-26
> **juicedM3 said:**
> I got the audio to work.  Sort of... I need to test if DD will work.  It's late on the east coast and not may stations play HD shows w/ AC3 at this hour.

Running my DD & DTS tests, it should still work.  I'd just like to see some DD from OTA.

...

Just an update to this, I now have DD w/ OTA HDTV.  I recently added an NVIDIA 9500GT card.  I documented that install here: [http://ubuntuforums.org/showthread.php?t=1249725](http://ubuntuforums.org/showthread.php?t=1249725).

I'm not sure if it's because the new video card uses the SPDIF out from the mobo or if it's one of the additional packages I installed as recommended from this [link]("http://ubuntuforums.org/showthread.php?t=1130384") or that I'm using the latest NVIDIA drivers.

Oh well.  Hopefully it's helpful to someone.

Justin

---

