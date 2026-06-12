---
title: "No Valid ELD - AMD Radeon 6xxx, dual monitor. Yamaha RX-v773 HDMI"
date: 2014-02-05
forum: Multimedia Software
---

### Post by cschroter on 2014-02-05
Noob to Linux, Have worked with IBM Unix years ago. Experienced with Windows and OSx.

Ubuntu 12.04 LTS, Desktop CD installed, Usually using Gnome desktop.

Dell Inspiron 580 (Intel® Core&#8482; i3 CPU 550 @ 3.20GHz × 4) Triple Boot - W7, Kubuntu (Latest Release), Ubuntu 12.04 LTS

AMD Radeon HD6850 PCI graphics card
Dual monitors, extended desktop configuration.
Main display BenQ GW2750 DVI
Extended Desktop HDMI to Yamaha RX-v773 AVR
AVR HDMI OUT1 to Sharp LC301 through an EDID emulator since the TV reports an invalid EDID (Stored in BIOS if we need it). 
Use 1280x720 resolution.

AMD fglrx driver and fglrx-amdcccle installed and functioning properly.

_**Problem:**_ No valid ELD being reported and/or read, so only PCM 2-channel stereo and AC3 output to AVR over HDMI with 'Generic' settings. 

Onboard graphics HDMI/VGA not used, but onboard analog 5.1 audio is in use and working.

AVR is connected to the to the extended display ouput via HDMI. Main display speakerless (DVI).

DVI Display#1, HDMI Display#2 (AVR). Both connected to AMD Radeon HD6850, Display Port unused.

Card 1, Dev 3 is the HDMI port connected to the AVR (I think...)

Hardware functions in W7 for all audio formats.

Using VLC 2.0.8 or XBMC 12.2 to play files.

My ALSA information is located at [http://www.alsa-project.org/db/?f=7e1d5f8c0f518dd4150906e085a0b663d94724d6](http://www.alsa-project.org/db/?f=7e1d5f8c0f518dd4150906e085a0b663d94724d6)



/proc/asound/card0:
total 0
dr-xr-xr-x 6 root root 0 Feb  5 20:48 .
dr-xr-xr-x 5 root root 0 Feb  5 20:48 ..
-r--r--r-- 1 root root 0 Feb  5 20:48 codec#0
-r--r--r-- 1 root root 0 Feb  5 20:48 codec#3
-rw-r--r-- 1 root root 0 Feb  5 20:48 eld#3.0
-r--r--r-- 1 root root 0 Feb  5 20:48 id
dr-xr-xr-x 3 root root 0 Feb  5 20:48 pcm0c
dr-xr-xr-x 3 root root 0 Feb  5 20:48 pcm0p
dr-xr-xr-x 3 root root 0 Feb  5 20:48 pcm2c
dr-xr-xr-x 3 root root 0 Feb  5 20:48 pcm3p

/proc/asound/card0/eld#0.0:

monitor_present 0                               ******correct, no monitor connected to onboard graphics
eld_valid        0                                          ******correct value, no monitor & therefore no sound




/proc/asound/card1:
total 0
dr-xr-xr-x 3 root root 0 Feb  5 20:48 .
dr-xr-xr-x 5 root root 0 Feb  5 20:48 ..
-r--r--r-- 1 root root 0 Feb  5 20:48 codec#0
-rw-r--r-- 1 root root 0 Feb  5 20:48 eld#0.0
-r--r--r-- 1 root root 0 Feb  5 20:48 id
dr-xr-xr-x 3 root root 0 Feb  5 20:48 pcm3p

/proc/asound/card1/eld#0.0:

monitor_present        1                                ******This value changes with the on/off or passthrough state of the AVR as expected
**eld_valid        0**                                         ******Problem - not reading or accepting info from AVR

/proc/asound/Generic/codec#0

Codec: ATI R6xx HDMI
Address: 0
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x1002aa01
Subsystem Id: 0x00aa0100
Revision Id: 0x100200
No Modem Function Group found
[B]Default PCM:
    rates [0x70]: 32000 44100 48000
    bits [0x2]: 16
    formats [0x5]: PCM AC3[/B]
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x02 [Audio Output] wcaps 0x201: Stereo Digital
  Converter: stream=1, channel=0
  Digital: Enabled
  Digital category: 0x0
  IEC Coding Type: 0x0
Node 0x03 [Pin Complex] wcaps 0x400381: Stereo Digital
  Control: name="HDMI/DP,pcm=3 Jack", index=0, device=0
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="ELD", index=0, device=3
  Pincap 0x00000094: OUT Detect HDMI
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=01, enabled=1
  Connection: 1
     0x02

/proc/asound/cards

 0 [MID            ]: HDA-Intel - HDA Intel MID
                      HDA Intel MID at 0xfbcf8000 irq 48
 1 [Generic        ]: HDA-Intel - HD-Audio Generic                *******HDA-Intel ? Should this be AMD/ATI something?
                      HD-Audio Generic at 0xfbdbc000 irq 49

---

### Post by jskiles1 on 2014-02-09
I'm in a similar boat as you.

OS: Debian Wheezy (3.12 kernel backport)
CPU: AMD A10-5800K (Radeon 7660D)

HDMI from PC to Sony HTSS360.
HDMI from Sony HTSS360 to HDTV.

Installed AMD Propritary Driver and CCC (3D acceleration and else functions as expected).

Card is detected properly and labeled as HDMI ATI when using "aplay", as seen below.

> card 0: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

> hdmi:CARD=HDMI,DEV=0
    HDA ATI HDMI, HDMI 0
    HDMI Audio Output

PulseAudio and ALSA only report 2 channel stereo (presumably due to improper ELD data being  read from receiver). 

All ELD files indicate the same as yours,  "monitor_present" and "eld_valid" are the only entries to the files.

I can only assume that because the ELD data is not being read from my receiver properly, the correctly supported audio formats are not capable of being utilized by PulseAudio and ALSA.

Of interest: [http://phoronix.com/forums/showthread.php?87172-Intel-AMD-HDMI-Audio-Improvements-In-Linux-3-13&p=370310#post370310](http://phoronix.com/forums/showthread.php?87172-Intel-AMD-HDMI-Audio-Improvements-In-Linux-3-13&p=370310#post370310)

---

### Post by jskiles1 on 2014-02-09
Update with some partial success:

As chronicled here: [http://forums.debian.net/viewtopic.php?f=7&t=111519&p=529586#p529586](http://forums.debian.net/viewtopic.php?f=7&t=111519&p=529586#p529586)

I was ultimately able to get a hacky solution to playing multi-channel audio with XBMC by forcing XBMC to use my audio device with HDMI and 5.1 channels. In XBMC's audio settings, I did:

> plughw:0,3

For both audio and passthrough settings. That device number will be different depending on the output of `aplay` audio device listings.

Unfortunately, this solution required killing PulseAudio and preventing it from auto starting prior to launching XBMC, which has a nasty side effect of no menu/desktop audio while XBMC is running.

---

### Post by cschroter on 2014-02-09
I do get 5.1 (AC3) with standard settings in XBMC and vlc. Have a newer version of XBMC loaded than is available from the standard sources. The AUDIO settings are a bit simpler with no change in functionality.

aplay -l
card 0: MID [HDA Intel MID], device 0: ALC887 Analog [ALC887 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: MID [HDA Intel MID], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Card 0 is onboard graphics/audio and card 1 is the PCI installed MSI AMD Radeon HD6850.

Some very good info here: [http://http.download.nvidia.com/XFree86/gpu-hdmi-audio-document/gpu-hdmi-audio.html](http://http.download.nvidia.com/XFree86/gpu-hdmi-audio-document/gpu-hdmi-audio.html) . For NVIDIA but all the concepts apply.

Found these messages in Xorg log:

[    3.618965] ACPI Warning: 0x0000000000000828-0x000000000000082f SystemIO conflicts with Region \PMRG 1 (20121018/utaddress-251)
[    3.618971] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    3.619020] lpc_ich: Resource conflict(s) found affecting gpio_ich
[    3.619221] hda-intel 0000:01:00.1: Handle VGA-switcheroo audio client
[    3.619288] snd_hda_intel 0000:01:00.1: irq 49 for MSI/MSI-X
[    3.625340] input: HD-Audio Generic HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input14
[    3.702464] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)

Maybe the video card being an MSI is a problem. Neglected to include the MSI branding of the video card in my original post.

Learning a lot trying to get this working.... 

Going to boot into kubuntu and see if there is any difference.

Most related threads are years old and tend to reference removing pulseaudio.  As indicated, removing PA or disabling does not go well in the latest releases.

Not much online about ELD data.

Thanks for posting a reply.


If there is a guru perusing this thread any help would be greatly appreciated. :confused:

---

### Post by cschroter on 2014-02-10
Real-Time EDID display from W7 using EnTech Monitor Asset Manager 2.70.0.989:


CE audio data (formats supported)
  LPCM    2-channel, 16/20/24 bit depths at 32/44/48/88/96/176/192 kHz
  LPCM    8-channel, 16/20/24 bit depths at 32/44/48/88/96/176/192 kHz
  AC-3    6-channel,  640k max. bit rate at 32/44/48 kHz
  DTS     7-channel, 1536k max. bit rate at 32/44/48/88/96 kHz
  SACD    6-channel                      at 44 kHz
  DD+     8-channel                      at 44/48 kHz
  DVD-A   8-channel                      at 48/96/192 kHz
  DTS-HD  8-channel, 16-bit              at 48/96/192 kHz

CE speaker allocation data
  Channel configuration.... 7.1
  Front left/right......... Yes
  Front LFE................ Yes
  Front center............. Yes
  Rear left/right.......... Yes
  Rear center.............. Yes
  Front left/right center.. No
  Rear left/right center... Yes
  Rear LFE................. No

Registry entry has no audio information

---

