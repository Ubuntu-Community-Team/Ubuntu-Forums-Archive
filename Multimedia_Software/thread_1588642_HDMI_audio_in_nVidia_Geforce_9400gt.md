---
title: "HDMI audio in nVidia Geforce 9400gt"
date: 2010-10-05
forum: Multimedia Software
---

### Post by dvinothkumar on 2010-10-05
I just installed Ubuntu 10.04. I couldn't get the audio working over HDMI through my nVidia MSI GeForce 9400gt video card. I tried the following:

- Updated to the latest nVidia driver version(256.53) for 64-bit Linux
- Updated the ALSA driver to  1.0.23 by following the instructions at [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)
- Tried the fix at [http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240](http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240) . that how-to is not actually prescribed for 9400GT. But I tried it anyways, and it did not work. 

I used to have a window7 in this computer and the HDMI worked just fine. So, it is not something to do with hardware. Even with Ubuntu 10.04, the headphone jack works. The problem is only with the HDMI port in the nVidia 9400gt graphics adapter. Any help to resolve this is much appreciated.


Here is the output of "aplay -l"

vinoth@htpc:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 1: SB [HDA ATI SB], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
vinoth@htpc:~$ 


Am I supposed to see an item for nVidia in this "aplay -l" output?

---

### Post by xavhornet on 2010-12-18
Hello,

I have exactly the same problem. I have the last Alsa driver and the last from Nvidia on a 10.04 LTS.
When i use aplay -l i have the same answer and i don't see any HDMI Nvidia output... i am a beat confuse because it write on my box's 9400GT that it can do pass trough audio to HDMI.
I will try an install of a 10.10 to see what append.

---

### Post by lmce on 2012-04-17
This is now two years later and still having the same issue as the above two.  Is this fixed in future ubuntu versions?

---

### Post by BicyclerBoy on 2012-04-17
The 9400GT does not have HDMI HDA codecs..

All pre GT210 nVidia video cards only have S/PDIF pass-thru' audio (pre-Azalia) **if** they have any audio at all.
The exceptions are the nVidia mobo chipset GPUs with HDMI output..

So if you have a pre-Azalia video card **& it has** **the S/PDIF header fitted**...you can link the mobo S/PDIF header to the video card header..

Note:
I don't think all 9400GT have the S/PDIF header..
The audio output device will not be listed as HDMI, just digital S/PDIF.
No presence detect, no ELD.
HDMI audio is possible over DVI-D
Don't follow probemask advice from XBMC.

---

### Post by mikaelcrocker on 2012-04-17
Have you tried opening alsamixer?  Going in there you may be able to turn off/on what you need, and indicate the output device and so on.

Or simple just making sure nvidia drivers are installed, and going to the admin panel and looking at the sound options, and do some clicking around in there, but I'm going to assume you've done that already

running alsamixer i as simple as going to console and `alsamixer`

---

### Post by mikaelcrocker on 2012-04-17
> **mikaelcrocker said:**
> Have you tried opening alsamixer?  Going in there you may be able to turn off/on what you need, and indicate the output device and so on.

Or simple just making sure nvidia drivers are installed, and going to the admin panel and looking at the sound options, and do some clicking around in there, but I'm going to assume you've done that already

running alsamixer i as simple as going to console and `alsamixer`
Oh! and one last thing, `lspci` gives a list of well pci devices.. and from there my machine will have Audio device: nVidia Corporation.. bla bla (blas are figurative ;) )

---

### Post by lmce on 2012-04-24
> **BicyclerBoy said:**
> The 9400GT does not have HDMI HDA codecs..

All pre GT210 nVidia video cards only have S/PDIF pass-thru' audio (pre-Azalia) **if** they have any audio at all.
The exceptions are the nVidia mobo chipset GPUs with HDMI output..

So if you have a pre-Azalia video card **& it has** **the S/PDIF header fitted**...you can link the mobo S/PDIF header to the video card header..

Note:
I don't think all 9400GT have the S/PDIF header..
The audio output device will not be listed as HDMI, just digital S/PDIF.
No presence detect, no ELD.
HDMI audio is possible over DVI-D
Don't follow probemask advice from XBMC.

 The 9400 is installed on an ASUS M3A87-EM mainboard with a S/PDIF out connected to the S/PDIF input on the 9400.  I can get S/PDIF on the front panel output without difficulty, but can't seem to get the signal through the card to my HDMI device.

---

### Post by lmce on 2012-04-24
> **mikaelcrocker said:**
> Have you tried opening alsamixer?  Going in there you may be able to turn off/on what you need, and indicate the output device and so on.

Or simple just making sure nvidia drivers are installed, and going to the admin panel and looking at the sound options, and do some clicking around in there, but I'm going to assume you've done that already

running alsamixer i as simple as going to console and `alsamixer`

  alsamixer shows the mainboard onboard devices and they play fine, but it won't pass-through the vid card.  No vidcard sound alsadevice is found.

---

### Post by BicyclerBoy on 2012-04-24
It will never show as HDMI audio device because it is not a video card codec.
This HDMI audio can only support stereo PCM & matrix AC3/DTS as digital pass thru' (48Khz).
No SAD/ELD
No hot plug events.

It is very easy to incorrectly wire up the link cable..some headers are 2, 3 or 4 pin (boxless & unpolarised)

Try
speaker-test -c 2 -r 48000 -l 1 -D hw:0,1
can not test AC3 with speaker-test..need to use VLC or mplayer..

---

### Post by lmce on 2012-04-26
> **BicyclerBoy said:**
> It will never show as HDMI audio device because it is not a video card codec.
This HDMI audio can only support stereo PCM & matrix AC3/DTS as digital pass thru' (48Khz).
No SAD/ELD
No hot plug events.

It is very easy to incorrectly wire up the link cable..some headers are 2, 3 or 4 pin (boxless & unpolarised)

Try
speaker-test -c 2 -r 48000 -l 1 -D hw:0,1
can not test AC3 with speaker-test..need to use VLC or mplayer..

  Confirmed that the s/pdif jumper and pins are linked properly on both mainboard and on the EN9400GT.  Gnd->Gnd, signal->signal.  No luck with the speaker-test.  Any other suggestions or diagnostics to check?

---

### Post by BicyclerBoy on 2012-04-27
aplay -l
aplay -L

The OP (if they care) needs to remove the snd-hda-intel option probemask..

---

### Post by lmce on 2012-04-28
> **BicyclerBoy said:**
> aplay -l
aplay -L

The OP (if they care) needs to remove the snd-hda-intel option probemask..

```
aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

aplay -L

null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=SB
    HDA ATI SB, ALC1200 Analog
    Default Audio Device
front:CARD=SB,DEV=0
    HDA ATI SB, ALC1200 Analog
    Front speakers
surround40:CARD=SB,DEV=0
    HDA ATI SB, ALC1200 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=SB,DEV=0
    HDA ATI SB, ALC1200 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=SB,DEV=0
    HDA ATI SB, ALC1200 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=SB,DEV=0
    HDA ATI SB, ALC1200 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=SB,DEV=0
    HDA ATI SB, ALC1200 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=SB,DEV=0
    HDA ATI SB, ALC1200 Digital
    IEC958 (S/PDIF) Digital Audio Output

```

---

### Post by BicyclerBoy on 2012-04-28
That previous speaker-test should have worked..
Try
speaker-test -c 2 -r 48000 -D iec958
speaker-test -c 2 -r 44100 -D iec958
speaker-test -c 2 -r 22050 -D iec958
speaker-test -c 2 -r 44100 -D hw:0,1
(close re-open terminal <ctrl>+<alt>+<t> between each)


Is the HDMI [S/PDIF] connected device a HT amp (AVR) of just a TV?

---

### Post by lmce on 2012-04-28
> **BicyclerBoy said:**
> That previous speaker-test should have worked..
Try
speaker-test -c 2 -r 48000 -D iec958
speaker-test -c 2 -r 44100 -D iec958
speaker-test -c 2 -r 22050 -D iec958
speaker-test -c 2 -r 44100 -D hw:0,1
(close re-open terminal <ctrl>+<alt>+<t> between each)


Is the S/PDIF connected device a HT amp (AVR) of just a TV?

The S/PDIF is being passed through the 9400GT to the HDMI and then to the LCD TV.  No AV receiver interposed.

Speaker-tests pending.

```

speaker-test -c 2 -r 48000 -D iec958

speaker-test 1.0.22

Playback device is iec958
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 16384
Period size range from 32 to 8192
Using max buffer size 16384
Periods = 4
was set period_size = 4096
was set buffer_size = 16384
 0 - Front Left
Write error: -32,Broken pipe
 1 - Front Right
Time per period = 5.339986
 0 - Front Left
 1 - Front Right
Time per period = 5.959350
 0 - Front Left
 1 - Front Right
Time per period = 5.959352
 0 - Front Left
 1 - Front Right
Time per period = 5.959347
 0 - Front Left
 1 - Front Right
Write error: -32,Broken pipe
Time per period = 5.642499
 0 - Front Left
 1 - Front Right
Time per period = 5.790792
 0 - Front Left
 1 - Front Right

```

---

### Post by lmce on 2012-04-28
```

speaker-test -c 2 -r 44100 -D iec958

speaker-test 1.0.22

Playback device is iec958
Stream parameters are 44100Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Rate set to 44100Hz (requested 44100Hz)
Buffer size range from 64 to 16384
Period size range from 32 to 8192
Using max buffer size 16384
Periods = 4
was set period_size = 4096
was set buffer_size = 16384
 0 - Front Left
 1 - Front Right
Time per period = 5.562170
 0 - Front Left
 1 - Front Right

```

No sound on any tests so far via HDMI.

---

### Post by lmce on 2012-04-28
Also just tried to install the backported alsa upgrades... still no luck.

---

### Post by BicyclerBoy on 2012-04-29
You have the S/PDIF header working from another jack so I doubt the alsa packages are to blame.

But why are they so old?
10.04.3 is alsa 1.0.23 kernel modules.

This should not affect you but with real HDMI audio, alsa 1.0.24 libs & utils are recommended..
alsa 1.0.25 from git is recommended to fix ELD/SAD problems.
 
I notice you are using AMD mobo chipset just like the OP?

Just to be sure you are using:
- the nVidia proprietary driver?
- an active X server screen on the HDMI connection?

Can you verify the TV HDMI audio with another device? 
Can you find another HDMI device to attach to PC like AVR etc?

---

### Post by lmce on 2012-04-29
> **BicyclerBoy said:**
> You have the S/PDIF header working from another jack so I doubt the alsa packages are to blame.

But why are they so old?

Dunno.... running 10.04, so that may have something to do with it?

> 10.04.3 is alsa 1.0.23 kernel modules.

This should not affect you but with real HDMI audio, alsa 1.0.24 libs & utils are recommended..
alsa 1.0.25 from git is recommended to fix ELD/SAD problems.
 

I'm probably not up for recompiling alsa at this point.  I'll probably just try 12.04.

> I notice you are using AMD mobo chipset just like the OP?

Just to be sure you are using:
- the nVidia proprietary driver?

Yep.

> - an active X server screen on the HDMI connection?

Yep, it's my monitor, but just can't get sound.

> Can you verify the TV HDMI audio with another device? 

It works with the cable box HDMI.

> Can you find another HDMI device to attach to PC like AVR etc?

I'm getting one soonish and will test the HDMI output on it when it arrives.

---

### Post by BicyclerBoy on 2012-04-29
Think I'm using proposed packages settings in synaptic..
The current lucid kernel gets you alsa 1.0.23.

You can avoid the need to compile the kernel or compile any alsa components.

Useful audio ppa:
- dkms-hda-intel ppa 1.0.25 (kernel dkms loaded) but not for lucid ?
- iQuik audio ppa (alsa 1.0.24 user-space) for lucid.
- ubuntu audio-dev, not very useful for lucid..

You could run the alsa-info script (from alsa project website) & post the link here..
Might help..

Apparently the ALC1200 codec custom device & is/was closed sourced (2009)..

---

### Post by lmce on 2012-05-01
Installed 12.04 last night.  I do have sound in 12.04, but it's tremendously distorted and clearly something isn't set up correctly.  It's going out via HDMI through my AV receiver (Marantz SR6006) and back to the display.  No problems with the display, but the sound is distored (filtered somehow?) and the vid/sound appears to desynchronize intermittently during playback (VLC).  This occurs even with analog output from the PC to a set of stereo speakers, so it's not the AV receiver as far as I can tell.  I'll post some diagnostic results when I get home.

aplay -l
```

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```aplay -L
```

default
    Playback/recording through the PulseAudio sound server
sysdefault:CARD=SB
    HDA ATI SB, ALC1200 Analog
    Default Audio Device
front:CARD=SB,DEV=0
    HDA ATI SB, ALC1200 Analog
    Front speakers
surround40:CARD=SB,DEV=0
    HDA ATI SB, ALC1200 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=SB,DEV=0
    HDA ATI SB, ALC1200 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=SB,DEV=0
    HDA ATI SB, ALC1200 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=SB,DEV=0
    HDA ATI SB, ALC1200 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=SB,DEV=0
    HDA ATI SB, ALC1200 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=SB,DEV=0
    HDA ATI SB, ALC1200 Digital
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=SB,DEV=0
    HDA ATI SB, ALC1200 Analog
    Direct sample mixing device
dmix:CARD=SB,DEV=1
    HDA ATI SB, ALC1200 Digital
    Direct sample mixing device
dsnoop:CARD=SB,DEV=0
    HDA ATI SB, ALC1200 Analog
    Direct sample snooping device
dsnoop:CARD=SB,DEV=1
    HDA ATI SB, ALC1200 Digital
    Direct sample snooping device
hw:CARD=SB,DEV=0
    HDA ATI SB, ALC1200 Analog
    Direct hardware device without any conversions
hw:CARD=SB,DEV=1
    HDA ATI SB, ALC1200 Digital
    Direct hardware device without any conversions
plughw:CARD=SB,DEV=0
    HDA ATI SB, ALC1200 Analog
    Hardware device with all software conversions
plughw:CARD=SB,DEV=1
    HDA ATI SB, ALC1200 Digital
    Hardware device with all software conversions

```Something is definitely different here... 

Help?

PS:  Alsa-dump for those who know enough to read it...

alsa-info.sh

```

upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Tue May  1 18:42:54 UTC 2012


!!Linux Distribution
!!------------------

Ubuntu 12.04 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"


!!DMI Information
!!---------------

Manufacturer:      System manufacturer
Product Name:      System Product Name
Product Version:   System Version


!!Kernel Information
!!------------------

Kernel release:    3.2.0-23-generic-pae
Operating System:  GNU/Linux
Architecture:      i686
Processor:         athlon
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.24
Library version:    1.0.25
Utilities version:  1.0.25


!!Loaded ALSA modules
!!-------------------

snd_hda_intel


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xf7ff4000 irq 16


!!PCI Soundcards installed in the system
!!--------------------------------------

00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:14.2 0403: 1002:4383
    Subsystem: 1043:82fe


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-caiaq: index=-2
snd-usb-ua101: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-usb-audio: index=-2
snd-hda-intel: model=intel probe_mask=1


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
    align_buffer_size : Y
    bdl_pos_adj : 32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-
1,-1,-1,-1,-1,-1
    beep_mode : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
    enable_msi : -1
    id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(nul
l),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),
(null),(null),(null),(null),(null)
    index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-
1,-1,-1,-1
    model : intel,(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(n
ull),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null
),(null),(null),(null),(null),(null)
    patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(
null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(nul
l),(null),(null),(null),(null),(null)
    position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    power_save : 0
    power_save_controller : Y
    probe_mask : 1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,
-1,-1,-1,-1,-1
    probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    single_cmd : N
    snoop : Y


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Realtek ALC1200
Address: 0
AFG Function Id: 0x1 (unsol 1)
Vendor Id: 0x10ec0888
Subsystem Id: 0x104382fe
Revision Id: 0x100101
No Modem Function Group found
Default PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=2, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x02 [Audio Output] wcaps 0x11: Stereo
  Device: name="ALC1200 Analog", type="Audio", device=0
  Converter: stream=8, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x03 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=8, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x04 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=8, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x05 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=8, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x06 [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=8, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM
Node 0x07 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x08 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Control: name="Capture Switch", index=0, device=0
  Control: name="Capture Volume", index=0, device=0
  Device: name="ALC1200 Analog", type="Audio", device=0
  Amp-In caps: ofs=0x0b, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x0b 0x0b]
  Converter: stream=4, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0x6]: 16 20
    formats [0x1]: PCM
  Connection: 1
     0x23
Node 0x09 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Control: name="Capture Switch", index=1, device=0
  Control: name="Capture Volume", index=1, device=0
  Device: name="ALC1200 Analog", type="Audio", device=2
  Amp-In caps: ofs=0x0b, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x80 0x80]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0x6]: 16 20
    formats [0x1]: PCM
  Connection: 1
     0x22
Node 0x0a [Audio Input] wcaps 0x100391: Stereo Digital
  Control: name="IEC958 Capture Switch", index=0, device=0
  Control: name="IEC958 Capture Default", index=0, device=0
  Device: name="ALC1200 Digital", type="SPDIF", device=1
  Converter: stream=0, channel=0
  SDI-Select: 0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x1f
Node 0x0b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="CD Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=4, ofs=0
  Control: name="CD Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=4, ofs=0
  Control: name="Line Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Control: name="Line Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Control: name="Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Front Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Control: name="Front Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Control: name="Beep Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=5, ofs=0
  Control: name="Beep Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=5, ofs=0
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [
0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 10
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17
Node 0x0c [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Control: name="Front Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x0f 0x0f]
  Connection: 2
     0x02 0x0b
Node 0x0d [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Control: name="Surround Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x0e 0x0e]
  Connection: 2
     0x03 0x0b
Node 0x0e [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Control: name="Center Playback Volume", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Control: name="LFE Playback Volume", index=0, device=0
    ControlAmp: chs=2, dir=Out, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x0f 0x0f]
  Connection: 2
     0x04 0x0b
Node 0x0f [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Control: name="Side Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x0f 0x0f]
  Connection: 2
     0x05 0x0b
Node 0x10 [Audio Output] wcaps 0x211: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="IEC958 Default PCM Playback Switch", index=0, device=0
  Device: name="ALC1200 Digital", type="SPDIF", device=1
  Converter: stream=8, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM
Node 0x11 [Pin Complex] wcaps 0x400300: Mono Digital
  Pincap 0x00000010: OUT
  Pin Default 0x99430140: [Fixed] SPDIF Out at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0x4, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x10
Node 0x12 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x13 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x14 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000003e: IN OUT HP Detect Trigger
  Pin Default 0x01014010: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x15 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000003e: IN OUT HP Detect Trigger
  Pin Default 0x01011012: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0x1, Sequence = 0x2
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c 0x0d* 0x0e 0x0f 0x26
Node 0x16 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00000036: IN OUT Detect Trigger
  Pin Default 0x01016011: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Orange
    DefAssociation = 0x1, Sequence = 0x1
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c 0x0d 0x0e* 0x0f 0x26
Node 0x17 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00000036: IN OUT Detect Trigger
  Pin Default 0x01012014: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Grey
    DefAssociation = 0x1, Sequence = 0x4
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c 0x0d 0x0e 0x0f* 0x26
Node 0x18 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Control: name="Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x01 0x01]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x01a19850: [Jack] Mic at Ext Rear
    Conn = 1/8, Color = Pink
    DefAssociation = 0x5, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x19 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Control: name="Front Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x02a19c60: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Pink
    DefAssociation = 0x6, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1a [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x0181305f: [Jack] Line In at Ext Rear
    Conn = 1/8, Color = Blue
    DefAssociation = 0x5, Sequence = 0xf
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1b [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Control: name="Headphone Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000373e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x02214c20: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Green
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0xc0: OUT HP VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1c [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x593301f0: [N/A] CD at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x1d [Pin Complex] wcaps 0x400000: Mono
  Pincap 0x00000020: IN
  Pin Default 0x4015e601: [N/A] Speaker at Ext N/A
    Conn = Optical, Color = White
    DefAssociation = 0x0, Sequence = 0x1
  Pin-ctls: 0x20: IN
Node 0x1e [Pin Complex] wcaps 0x400300: Mono Digital
  Pincap 0x00000010: OUT
  Pin Default 0x01456130: [Jack] SPDIF Out at Ext Rear
    Conn = Optical, Color = Orange
    DefAssociation = 0x3, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x06
Node 0x1f [Pin Complex] wcaps 0x400200: Mono Digital
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
  Processing caps: benign=0, ncoeff=17
Node 0x21 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x22 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Input Source", index=1, device=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [
0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 11
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b
Node 0x23 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Input Source", index=0, device=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [
0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 11
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b
Node 0x24 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x25 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x26 [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x25 0x0b
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw---T+ 1 root audio 116,  8 May  1 14:04 /dev/snd/controlC0
crw-rw---T+ 1 root audio 116,  7 May  1 14:04 /dev/snd/hwC0D0
crw-rw---T+ 1 root audio 116,  6 May  1 14:39 /dev/snd/pcmC0D0c
crw-rw---T+ 1 root audio 116,  5 May  1 14:39 /dev/snd/pcmC0D0p
crw-rw---T+ 1 root audio 116,  4 May  1 14:39 /dev/snd/pcmC0D1c
crw-rw---T+ 1 root audio 116,  3 May  1 14:39 /dev/snd/pcmC0D1p
crw-rw---T+ 1 root audio 116,  2 May  1 14:04 /dev/snd/pcmC0D2c
crw-rw---T+ 1 root audio 116,  1 May  1 14:04 /dev/snd/seq
crw-rw---T+ 1 root audio 116, 33 May  1 14:04 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 May  1 14:04 .
drwxr-xr-x 3 root root 240 May  1 14:04 ..
lrwxrwxrwx 1 root root  12 May  1 14:04 pci-0000:00:14.2 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 2: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [SB]

Card hw:0 'SB'/'HDA ATI SB at 0xf7ff4000 irq 16'
  Mixer name    : 'Realtek ALC1200'
  Components    : 'HDA:10ec0888,104382fe,00100101'
  Controls      : 40
  Simple ctrls  : 22
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 15 [48%] [-24.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pswitch penum
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Front Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Front Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 30 [97%] [-1.50dB] [on]
  Front Right: Playback 30 [97%] [-1.50dB] [on]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Side',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [on]
  Front Right: Playback 0 [0%] [-34.50dB] [on]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 1 [33%] [10.00dB]
  Front Right: 1 [33%] [10.00dB]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined cswitch cswitch-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Mono: Playback [on] Capture [off]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Beep',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 11 [35%] [0.00dB] [on]
  Front Right: Capture 11 [35%] [0.00dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 0 [0%] [-16.50dB] [off]
  Front Right: Capture 0 [0%] [-16.50dB] [off]
Simple mixer control 'Channel Mode',0
  Capabilities: enum
  Items: '6ch' '8ch'
  Item0: '8ch'
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line' 'CD'
  Item0: 'Mic'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line' 'CD'
  Item0: 'Mic'


!!Alsactl output
!!-------------

--startcollapse--
state.SB {
    control.1 {
        iface MIXER
        name 'Front Playback Volume'
        value.0 31
        value.1 31
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 31'
            dbmin -4650
            dbmax 0
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.2 {
        iface MIXER
        name 'Front Playback Switch'
        value.0 true
        value.1 true
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.3 {
        iface MIXER
        name 'Surround Playback Volume'
        value.0 30
        value.1 30
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 31'
            dbmin -4650
            dbmax 0
            dbvalue.0 -150
            dbvalue.1 -150
        }
    }
    control.4 {
        iface MIXER
        name 'Surround Playback Switch'
        value.0 true
        value.1 true
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.5 {
        iface MIXER
        name 'Center Playback Volume'
        value 31
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 31'
            dbmin -4650
            dbmax 0
            dbvalue.0 0
        }
    }
    control.6 {
        iface MIXER
        name 'LFE Playback Volume'
        value 31
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 31'
            dbmin -4650
            dbmax 0
            dbvalue.0 0
        }
    }
    control.7 {
        iface MIXER
        name 'Center Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.8 {
        iface MIXER
        name 'LFE Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.9 {
        iface MIXER
        name 'Side Playback Volume'
        value.0 31
        value.1 31
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 31'
            dbmin -4650
            dbmax 0
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.10 {
        iface MIXER
        name 'Side Playback Switch'
        value.0 true
        value.1 true
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.11 {
        iface MIXER
        name 'Headphone Playback Switch'
        value.0 true
        value.1 true
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.12 {
        iface MIXER
        name 'CD Playback Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 31'
            dbmin -3450
            dbmax 1200
            dbvalue.0 -3450
            dbvalue.1 -3450
        }
    }
    control.13 {
        iface MIXER
        name 'CD Playback Switch'
        value.0 false
        value.1 false
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.14 {
        iface MIXER
        name 'Line Playback Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 31'
            dbmin -3450
            dbmax 1200
            dbvalue.0 -3450
            dbvalue.1 -3450
        }
    }
    control.15 {
        iface MIXER
        name 'Line Playback Switch'
        value.0 true
        value.1 true
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.16 {
        iface MIXER
        name 'Mic Playback Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 31'
            dbmin -3450
            dbmax 1200
            dbvalue.0 -3450
            dbvalue.1 -3450
        }
    }
    control.17 {
        iface MIXER
        name 'Mic Boost Volume'
        value.0 1
        value.1 1
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 3'
            dbmin 0
            dbmax 3000
            dbvalue.0 1000
            dbvalue.1 1000
        }
    }
    control.18 {
        iface MIXER
        name 'Mic Playback Switch'
        value.0 false
        value.1 false
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.19 {
        iface MIXER
        name 'Front Mic Playback Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 31'
            dbmin -3450
            dbmax 1200
            dbvalue.0 -3450
            dbvalue.1 -3450
        }
    }
    control.20 {
        iface MIXER
        name 'Front Mic Boost Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 3'
            dbmin 0
            dbmax 3000
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.21 {
        iface MIXER
        name 'Front Mic Playback Switch'
        value.0 false
        value.1 false
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.22 {
        iface MIXER
        name 'Channel Mode'
        value '8ch'
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 '6ch'
            item.1 '8ch'
        }
    }
    control.23 {
        iface MIXER
        name 'Capture Switch'
        value.0 true
        value.1 true
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.24 {
        iface MIXER
        name 'Capture Switch'
        index 1
        value.0 false
        value.1 false
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.25 {
        iface MIXER
        name 'Capture Volume'
        value.0 11
        value.1 11
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 31'
            dbmin -1650
            dbmax 3000
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.26 {
        iface MIXER
        name 'Capture Volume'
        index 1
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 31'
            dbmin -1650
            dbmax 3000
            dbvalue.0 -1650
            dbvalue.1 -1650
        }
    }
    control.27 {
        iface MIXER
        name 'Input Source'
        value Mic
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Mic
            item.1 'Front Mic'
            item.2 Line
            item.3 CD
        }
    }
    control.28 {
        iface MIXER
        name 'Input Source'
        index 1
        value Mic
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Mic
            item.1 'Front Mic'
            item.2 Line
            item.3 CD
        }
    }
    control.29 {
        iface MIXER
        name 'IEC958 Playback Con Mask'
        value '0fff00000000000000000000000000000000000000000000000000000000000000000000000000
00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.30 {
        iface MIXER
        name 'IEC958 Playback Pro Mask'
        value '0f0000000000000000000000000000000000000000000000000000000000000000000000000000
00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.31 {
        iface MIXER
        name 'IEC958 Playback Default'
        value '040000000000000000000000000000000000000000000000000000000000000000000000000000
00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access 'read write'
            type IEC958
            count 1
        }
    }
    control.32 {
        iface MIXER
        name 'IEC958 Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.33 {
        iface MIXER
        name 'IEC958 Default PCM Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.34 {
        iface MIXER
        name 'IEC958 Capture Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.35 {
        iface MIXER
        name 'IEC958 Capture Default'
        value '040000000000000000000000000000000000000000000000000000000000000000000000000000
00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.36 {
        iface MIXER
        name 'Beep Playback Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 31'
            dbmin -3450
            dbmax 1200
            dbvalue.0 -3450
            dbvalue.1 -3450
        }
    }
    control.37 {
        iface MIXER
        name 'Beep Playback Switch'
        value.0 false
        value.1 false
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.38 {
        iface MIXER
        name 'Master Playback Volume'
        value 15
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 31'
            dbmin -4650
            dbmax 0
            dbvalue.0 -2400
        }
    }
    control.39 {
        iface MIXER
        name 'Master Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.40 {
        iface MIXER
        name 'PCM Playback Volume'
        value.0 255
        value.1 255
        comment {
            access 'read write user'
            type INTEGER
            count 2
            range '0 - 255'
            tlv '0000000100000008ffffec1400000014'
            dbmin -5100
            dbmax 0
            dbvalue.0 0
            dbvalue.1 0
        }
    }
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
rfcomm
vesafb
bnep
bluetooth
snd_hda_codec_realtek
nfsd
nfs
lockd
fscache
auth_rpcgss
nfs_acl
sunrpc
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_pcm
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
ppdev
snd_seq
snd_timer
snd_seq_device
snd
nvidia
soundcore
joydev
k10temp
snd_page_alloc
asus_atk0110
parport_pc
sp5100_tco
i2c_piix4
mac_hid
wmi
lp
parport
usbhid
hid
skge
floppy
pata_atiixp
firewire_ohci
firewire_core
crc_itu_t
r8169


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x11 0x99430140
0x14 0x01014010
0x15 0x01011012
0x16 0x01016011
0x17 0x01012014
0x18 0x01a19850
0x19 0x02a19c60
0x1a 0x0181305f
0x1b 0x02214c20
0x1c 0x593301f0
0x1d 0x4015e601
0x1e 0x01456130
0x1f 0x411111f0

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[    9.236054] FS-Cache: Netfs 'nfs' registered for caching
[    9.240223] snd_hda_intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.240907] init: failsafe main process (734) killed by TERM signal
--
[  600.000314] NETDEV WATCHDOG: eth1 (r8169): transmit queue 0 timed out
[  600.000319] Modules linked in: rfcomm vesafb bnep bluetooth snd_hda_codec_realtek nfsd nfs lockd f
scache auth_rpcgss nfs_acl sunrpc snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawm
idi snd_seq_midi_event ppdev snd_seq snd_timer snd_seq_device snd nvidia(P) soundcore joydev k10temp 
snd_page_alloc asus_atk0110 parport_pc sp5100_tco i2c_piix4 mac_hid wmi lp parport usbhid hid skge fl
oppy pata_atiixp firewire_ohci firewire_core crc_itu_t r8169
[  600.000407] Pid: 0, comm: swapper/1 Tainted: P           O 3.2.0-23-generic-pae #36-Ubuntu


```

---

### Post by lmce on 2012-05-01
Attempting to follow [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

Step 1:

Completed.

Sound functions.  Getting Dolby Digital out of my AV receiver!

However, there is distortion on the sound which remains most noted on main channel.  Also incredibly slow video for 1080p and choppy video on occasion.

---

### Post by BicyclerBoy on 2012-05-01
Not likely to make any diff but..
I suggest you comment out/delete the **probe_mask option** in /etc/modprobe.d/asound.conf that is generating this:
snd-hda-intel: model=intel **probe_mask=1**

That probe mask forces only the 1st HDA codec (on card0 here) to be exposed/enumerated by alsa.
Probe masks are not needed with later alsa. They never were actually required but were used to try to simplify the pulse audio configuration.

Can you not use the 64 bit kernel ?
vlc does not use VDPAU (your card is feature set B) but can use va-api.

---

### Post by lmce on 2012-05-01
> **BicyclerBoy said:**
> Not likely to make any diff but..
I suggest you comment out/delete the **probe_mask option** in /etc/modprobe.d/asound.conf that is generating this:
snd-hda-intel: model=intel **probe_mask=1**

That probe mask forces only the 1st HDA codec (on card0 here) to be exposed/enumerated by alsa.
Probe masks are not needed with later alsa. They never were actually required but were used to try to simplify the pulse audio configuration.

Can you not use the 64 bit kernel ?
vlc does not use VDPAU (your card is feature set B) but can use va-api.

Removed the probe_mask=1.  No change.

I haven't tried a 64bit kernel... but I'd like to get the sound working before I try it.

I have no idea what your comment about VDPAU or va-api refers to?

---

### Post by BicyclerBoy on 2012-05-01
The nVidia HDMI audio doc & others..suggests that changes to files in /etc/modprobe.d/ folders require:
sudo update-initramfs -u

The requirement of this depends on the exact linux distro.
This command is triggered by kernel updates etc.
The author of the nVidia HDMI audio would be one of the more knowledgeable on the subject..

You mentioned incredibly slow video...so ..

A random check-list of ideas:
Your CPU is == core2duo ?
9400GT card is okay using VDPAU & but not for advanced VDPAU features.

core2duo can decode 10Mbps HD H264 at about 50% CPU (vlc).
Not usable when attempting to use the yadifx2 interlacing filter (vlc). 

The possible playback problems with vlc (not exhaustive)..
- frequency scaling CPU clock
[http://www.mythtv.org/wiki/VDPAU#CPU_Frequency_Scaling](http://www.mythtv.org/wiki/VDPAU#CPU_Frequency_Scaling)
- CPU decode for HD (not using va-api)
- pulse audio: time vs interrupt scheduling bug with older vlc (using pulse server)


How confident are you that option model=intel is correct/required?

---

### Post by lmce on 2012-05-01
> **BicyclerBoy said:**
> The nVidia HDMI audio doc & others..suggests that changes to files in /etc/modprobe.d/ folders require:
sudo update-initramfs -u

The requirement of this depends on the exact linux distro.
This command is triggered by kernel updates etc.
The author of the nVidia HDMI audio would be one of the more knowledgeable on the subject..

You mentioned incredibly slow video...so ..

Not incredibly slow, just choppy.

> 
A random check-list of ideas:
Your CPU is == core2duo ?
9400GT card is okay using VDPAU & but not for advanced VDPAU features.

core2duo can decode 10Mbps HD H264 at about 50% CPU (vlc), not if using yadifx2 interlacing filter. 

The possible playback problems with vlc (not exhaustive)..
- frequency scaling CPU clock
[http://www.mythtv.org/wiki/VDPAU#CPU_Frequency_Scaling](http://www.mythtv.org/wiki/VDPAU#CPU_Frequency_Scaling)
- CPU decode for HD (not using va-api)
- pulse audio: time vs interrupt scheduling bug with older vlc (using pulse server)


How confident are you that option model=intel is correct/required?

Not confident at all.  I removed it from the file.

None of this was an issue in 10.04 or in 8.10.  The same system played 1080p video with flawless sound without problems.

---

### Post by BicyclerBoy on 2012-05-01
Unity/compiz/composite effects are forced on 12.04.

nVidia has always had a difficult relationship with composite effects.
There are some 'ccsm' settings that can help with tearing/vsync but not slow choppy video ..
The 9400GT is not a fast (openGL) card..I still have one in non-HTPC box running 12.04..
Unity3d & VDPAU video flash etc is okay..

Another long shot:
Could try the gnone-session-fallback desktop env. (just a simple package install).
gnome-session-fallback does not need to use compiz.

---

### Post by lmce on 2012-05-01
> **BicyclerBoy said:**
> Unity/compiz/composite effects are forced on 12.04.

nVidia has always had a difficult relationship with composite effects.
There are some 'ccsm' settings that can help with tearing/vsync but not slow choppy video ..
The 9400GT is not a fast (openGL) card..I still have one in non-HTPC box running 12.04..
Unity3d & VDPAU video flash etc is okay..

Another long shot:
Could try the gnone-session-fallback desktop env. (just a simple package install).
gnome-session-fallback does not need to use compiz.

Well that sucks.

If I pull the 9400, I could try out the onboard video in the M3A87-EM... 

It sounds like I should just downgrade to 10.04 and leave it there until ubuntu gets this stuff figured out.

---

### Post by BicyclerBoy on 2012-05-01
I'm not saying that unity is the problem..just could be an additional problem..
I have a unity3d 12.04 box with 9400GT & it works okay (i3 CPU).
This box was problematic to get good full screen video playback in 11.04 (no composite redirection).
But this box was upgraded thru' each release & now 12.04 seems fine.
So it can work okay..

To clarify
I don't know if compiz can be blamed for slow choppy video.
I don't know any compiz/ccsm settings that cause slow choppy video.
There are settings that cause/stop vsync/tearing.

Gnome-session-fallback is similar to 10.04 gnome but not as complete.

---

### Post by lmce on 2012-05-01
> **BicyclerBoy said:**
> I'm not saying that unity is the problem..just could be an additional problem..
I have a unity3d 12.04 box with 9400GT & it works okay (i3 CPU).
This box was problematic to get good full screen video playback in 11.04 (no composite redirection).
But this box was upgraded thru' each release & now 12.04 seems fine.
So it can work okay..

To clarify
I don't know if compiz can be blamed for slow choppy video.
I don't know any compiz/ccsm settings that cause slow choppy video.
There are settings that cause/stop vsync/tearing.

Gnome-session-fallback is similar to 10.04 gnome but not as complete.

Managed to fix most of the problems by going back to pure ALSA output.

Still getting intermittent cut-outs, but I think it's a Pulseaudio problem.

---

### Post by lmce on 2012-05-03
Anyone else have suggestions?  Or know anyone on the pulseaudio team that actually wants to make their project compatible with a TON of existing hardware?

---

### Post by BicyclerBoy on 2012-05-04
The same codec ALC1200 in my intel H67? chipset mobo has worked without problem with alsa/pulse in all the ubuntu releases..
Granted that is only a test of stereo analogue output.

So maybe it has something to do with AMD chipset & less to do with audio codec.

---

### Post by lmce on 2012-05-04
> **BicyclerBoy said:**
> The same codec ALC1200 in my intel H67? chipset mobo has worked without problem with alsa/pulse in all the ubuntu releases..
Granted that is only a test of stereo analogue output.

So maybe it has something to do with AMD chipset & less to do with audio codec.

 It's a digital problem.

---

### Post by lmce on 2012-05-14
No one else has any ideas?

---

