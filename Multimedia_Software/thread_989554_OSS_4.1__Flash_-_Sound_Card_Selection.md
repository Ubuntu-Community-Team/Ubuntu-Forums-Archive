---
title: "OSS 4.1 / Flash - Sound Card Selection"
date: 2008-11-21
forum: Multimedia Software
---

### Post by edwin11 on 2008-11-21
[FONT="Verdana"][SIZE="2"][COLOR="Navy"]Hi all,

Would like to seek your advice on this. i don't think it's a difficult problem, just couldn't figure it out...

i have an onboard soundcard, and a Creative x-Fi.

i just compiled and installed OSS 4.1 by following the instructions from [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound) (including the section on "Flash").

i managed to get Rhythmbox to use the x-Fi soundcard, but Flash uses the onboard one (ossxmix and ossinfo shows this).

Also tried compiling and installing libflashsupport by following [http://www.opensound.com/wiki/index.php/Configuring_Applications_for_OSSv4#compiling_libflashsupport](http://www.opensound.com/wiki/index.php/Configuring_Applications_for_OSSv4#compiling_libflashsupport) but without any difference in results.

Here is the ossinfo -v3. It shows Rhythmbox and Firefox using different soundcards.

```
Version info: OSS 4.1 (b rc2/200811212235) (0x00040090) GPL
Platform: Linux/i686 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 (mydesktop)

Number of audio devices:	8
Number of audio engines:	16
Number of mixer devices:	2


Device objects
 0: osscore0 OSS core services
 1: oss_hdaudio0 ATI HD Audio interrupts=503280 (503280)
    HD Audio controller ATI HD Audio
    Vendor ID    0x10024383
    Subvendor ID 0x10438247
     Codec  0: Unknown (0x10ec0660/0x10438247)
 2: oss_sbxfi0 Sound Blaster X-Fi (SB046x/067x/076x) interrupts=318012 (318012)
    PCI device 1102:0005, subdevice 1102:0021
 3: oss_usb0 USB audio core services


Mixer devices
 0: High Definition Audio 0x10ec066 (Mixer 0 of device object 1)
    Device file /dev/oss/oss_hdaudio0/mix0, Legacy device /dev/mixer0
    Priority: 10
    Caps: 
    Device handle: PCI82471043-0000:00:14.2-mx01
    Device priority: 10

 1: Sound Blaster X-Fi (SB046x/067x (Mixer 0 of device object 2)
    Device file /dev/oss/oss_sbxfi0/mix0, Legacy device /dev/mixer1
    Priority: 1
    Caps: 
    Device handle: PCI00211102-0000:02:01.0-mx01
    Device priority: 1


Audio devices
HD Audio play pcm1                /dev/oss/oss_hdaudio0/pcm0  (device index 0)
    Legacy device /dev/dsp0
    Caps: DUPLEX TRIGGER MMAP 
    Modes: IN/OUT 
      Out engine  1: 0/HD Audio play pcm1
                     Busy (OUT) label 'VMIX' 
      Engine      2: 6/HD Audio play pcm1 (vmix)
                     Busy (OUT) by PID 7420 / firefox label 'firefox' 
      Engine      3: 7/HD Audio play pcm1 (vmix)
                     Available for use 
      Engine      4: 8/HD Audio play pcm1 (vmix)
                     Available for use 
      Engine      5: 9/HD Audio play pcm1 (vmix)
                     Available for use 
    Input formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Output formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Device handle: PCI82471043-0000:00:14.2-au01
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 8
    Native sample rates (min - max): 44100 - 96000 (44100,48000,96000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

HD Audio play pcm2                /dev/oss/oss_hdaudio0/pcm1  (device index 1)
    Legacy device /dev/dsp1
    Caps: TRIGGER MMAP 
    Modes: OUTPUT 
      Out engine  1: 1/HD Audio play pcm2
                     Available for use 
    Input formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Output formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Device handle: PCI82471043-0000:00:14.2-au02
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 44100 - 96000 (44100,48000,96000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

HD Audio play pcm3                /dev/oss/oss_hdaudio0/pcm2  (device index 2)
    Legacy device /dev/dsp2
    Caps: TRIGGER MMAP 
    Modes: OUTPUT 
      Out engine  1: 2/HD Audio play pcm3
                     Available for use 
    Input formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Output formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Device handle: PCI82471043-0000:00:14.2-au03
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 44100 - 96000 (44100,48000,96000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

HD Audio play pcm4                /dev/oss/oss_hdaudio0/pcm3  (device index 3)
    Legacy device /dev/dsp3
    Caps: TRIGGER MMAP 
    Modes: OUTPUT 
      Out engine  1: 3/HD Audio play pcm4
                     Available for use 
    Input formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Output formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Device handle: PCI82471043-0000:00:14.2-au04
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 44100 - 96000 (44100,48000,96000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

HD Audio play spdifout1           /dev/oss/oss_hdaudio0/spdout0  (device index 4)
    Legacy device /dev/dsp4
    Caps: TRIGGER MMAP 
    Modes: OUTPUT 
      Out engine  1: 4/HD Audio play spdifout1
                     Available for use 
    Input formats (0x00001410):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_AC3		- AC3 (Dolby Digital) encoded audio
      AFMT_S32_LE	- 32 bit signed little endian
    Output formats (0x00001410):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_AC3		- AC3 (Dolby Digital) encoded audio
      AFMT_S32_LE	- 32 bit signed little endian
    Device handle: PCI82471043-0000:00:14.2-au05
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 44100 - 96000 (44100,48000,96000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

HD Audio rec mix6                 /dev/oss/oss_hdaudio0/pcmin0  (device index 5)
    Legacy device /dev/dsp5
    Caps: DUPLEX TRIGGER MMAP 
    Modes: IN/OUT 
      In engine   1: 5/HD Audio rec mix6
                     Busy (IN) label 'VMIX_IN' 
      Engine      2: 6/HD Audio play pcm1 (vmix)
                     Busy (OUT) by PID 7420 / firefox label 'firefox' 
      Engine      3: 7/HD Audio play pcm1 (vmix)
                     Available for use 
      Engine      4: 8/HD Audio play pcm1 (vmix)
                     Available for use 
      Engine      5: 9/HD Audio play pcm1 (vmix)
                     Available for use 
    Input formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Output formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Device handle: PCI82471043-0000:00:14.2-au06
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 44100 - 96000 (44100,48000,96000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

Sound Blaster X-Fi (SB046x/067x/076x) output  /dev/oss/oss_sbxfi0/pcm0  (device index 6)
    Legacy device /dev/dsp6
    Caps: DUPLEX TRIGGER MMAP 
    Modes: IN/OUT 
      Out engine  1: 10/Sound Blaster X-Fi (SB046x/067x/076x) output
                     Busy (OUT) label 'VMIX' 
      Engine      2: 12/Sound Blaster X-Fi (SB046x/067x/076x) output (vmix)
                     Busy (OUT) by PID 6646 / rhythmbox label 'rhythmbox' 
      Engine      3: 13/Sound Blaster X-Fi (SB046x/067x/076x) output (vmix)
                     Available for use 
      Engine      4: 14/Sound Blaster X-Fi (SB046x/067x/076x) output (vmix)
                     Available for use 
      Engine      5: 15/Sound Blaster X-Fi (SB046x/067x/076x) output (vmix)
                     Available for use 
    Input formats (0x00000010):
      AFMT_S16_LE	- 16 bit signed little endian
    Output formats (0x00000010):
      AFMT_S16_LE	- 16 bit signed little endian
    Device handle: PCI00211102-0000:02:01.0-au01
    Related mixer dev: 1
    Sample rate source: 10
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 48000 - 92600
    HW Type: Not indicated.
    Minimum latency: Not indicated

Sound Blaster X-Fi (SB046x/067x/076x) input  /dev/oss/oss_sbxfi0/pcmin0  (device index 7)
    Legacy device /dev/dsp7
    Caps: DUPLEX TRIGGER MMAP 
    Modes: IN/OUT 
      In engine   1: 11/Sound Blaster X-Fi (SB046x/067x/076x) input
                     Busy (IN) label 'VMIX_IN' 
      Engine      2: 12/Sound Blaster X-Fi (SB046x/067x/076x) output (vmix)
                     Busy (OUT) by PID 6646 / rhythmbox label 'rhythmbox' 
      Engine      3: 13/Sound Blaster X-Fi (SB046x/067x/076x) output (vmix)
                     Available for use 
      Engine      4: 14/Sound Blaster X-Fi (SB046x/067x/076x) output (vmix)
                     Available for use 
      Engine      5: 15/Sound Blaster X-Fi (SB046x/067x/076x) output (vmix)
                     Available for use 
    Input formats (0x00000010):
      AFMT_S16_LE	- 16 bit signed little endian
    Output formats (0x00000010):
      AFMT_S16_LE	- 16 bit signed little endian
    Device handle: PCI00211102-0000:02:01.0-au02
    Related mixer dev: 1
    Sample rate source: 10
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 48000 - 96000
    HW Type: Not indicated.
    Minimum latency: Not indicated
```

How can i configure Flash to use the x-Fi soundcard?

Thanks in advance!



Thanks,
Edwin[/COLOR][/SIZE][/FONT]

---

### Post by edwin11 on 2008-11-24
[FONT="Verdana"][SIZE="2"][COLOR="Navy"]Followed these instructions:

[http://www.opensound.com/wiki/index.php/Tips_And_Tricks#Changing_the_default_sound_output](http://www.opensound.com/wiki/index.php/Tips_And_Tricks#Changing_the_default_sound_output)



Regards,
Edwin
[/COLOR][/SIZE][/FONT]

---

