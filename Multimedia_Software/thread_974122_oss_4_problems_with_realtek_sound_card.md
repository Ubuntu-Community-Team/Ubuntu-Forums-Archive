---
title: "oss 4 problems with realtek sound card"
date: 2008-11-07
forum: Multimedia Software
---

### Post by Russell Herin on 2008-11-07
Problems with Realtek AC'97  ALC250
I just followed the wiki and installed oss 4 to replace alsa, which made all of my mic input come out as garbled and deep--unusable.

So I followed the directions on the wiki (using Intrepid, xubuntu by the way) and now I still have problems.  The mic can be detected if I put up the volume:  I'll hear myself blowing into the mic and it comes out on the speakers.

HOWEVER I cannot tick the box for spdin on the ossxmixer and recording programs will say "your capture settings needed to be adjusted in system preferences sound.

Well, being on xubuntu, I went into the settings manager and the sound utility won't detect any drivers.  Additionally, the ossinfo report on terminal doesn't seem to detect any input devices.

I'm starting to realize that Ubuntu is pretty crappy for soundcard support (A host of bugs for Realtek is what the search gets me).  Any information I can find even remotely related is in Linux-ese.

uname -a
Linux russel-herin 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 i686 GNU/Linux

ossmix
oaner@russel-herin:~$ uname -a
Linux russel-herin 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 i686 GNU/Linux
oaner@russel-herin:~$ ossmix
Selected mixer 0/AC97 Mixer (ALC250)
Known controls are:


vol [<leftvol>:<rightvol>] (currently 56:56)
vol.rec ON|OFF (currently OFF)

pcm [<leftvol>:<rightvol>] (currently 74:74)

speaker <monovol> (currently 0)

line [<leftvol>:<rightvol>] (currently 0:0)
line.rec ON|OFF (currently OFF)

mic <monovol> (currently 1)
mic.rec ON|OFF (currently ON)

cd [<leftvol>:<rightvol>] (currently 74:74)
cd.rec ON|OFF (currently OFF)

igain [<leftvol>:<rightvol>] (currently 78:78)

aux1 [<leftvol>:<rightvol>] (currently 78:78)
aux1.rec ON|OFF (currently OFF)

phone [<leftvol>:<rightvol>] (currently 78:78)
phone.rec ON|OFF (currently OFF)

mono <monovol> (currently 76)
mono.rec ON|OFF (currently OFF)

video [<leftvol>:<rightvol>] (currently 76:76)
video.rec ON|OFF (currently OFF)


spdout.enable ON|OFF (currently ON)
spdout.adc/dac ON|OFF (currently ON)
spdout.pro <Consumer|Professional> (currently Consumer)
spdout.audio <AUDIO|DATA> (currently AUDIO)
spdout.copy ON|OFF (currently OFF)
spdout.pre-emph ON|OFF (currently OFF)
spdout.rate <48000|44100|32000> (currently 48000)
spdout.vbit ON|OFF (currently OFF)

spdin.enable ON|OFF (currently OFF)
spdin.monitor ON|OFF (currently ON)
spdin.pro <decimal value> (currently 0) (Read-only)
spdin.audio <decimal value> (currently 0) (Read-only)
spdin.copy <decimal value> (currently 0) (Read-only)
spdin.pre-emph <decimal value> (currently 0) (Read-only)
spdin.mode <decimal value> (currently 0) (Read-only)
spdin.category <decimal value> (currently 0) (Read-only)
spdin.genlevel <decimal value> (currently 0) (Read-only)
spdin.source <decimal value> (currently 0) (Read-only)
spdin.channel <decimal value> (currently 0) (Read-only)
spdin.rate <decimal value> (currently 44100) (Read-only)
spdin.clock <decimal value> (currently 0) (Read-only)
spdin.signal <decimal value> (currently 0) (Read-only)
spdin.vbit <decimal value> (currently 0) (Read-only)
vmix0-enable ON|OFF (currently ON)
vmix0-rate <decimal value> (currently 48000) (Read-only)
vmix0-channels <Stereo|Multich> (currently Stereo)
vmix0-src <Fast|Low|Medium|High|High+|Production|OFF> (currently Fast)
vmix0-outvol <monovol> (currently 24.8 dB)

vmix0-invol <monovol> (currently 25.0 dB)
vmix0.pcm1 [<leftvol>:<rightvol>] (currently 25.0:25.0 dB)
vmix0.pcm2 [<leftvol>:<rightvol>] (currently 25.0:25.0 dB)
vmix0.pcm3 [<leftvol>:<rightvol>] (currently 25.0:25.0 dB)
vmix0.pcm4 [<leftvol>:<rightvol>] (currently 25.0:25.0 dB)


ossinfo -v3
Selected mixer 0/AC97 Mixer (ALC250)
Known controls are:


vol [<leftvol>:<rightvol>] (currently 56:56)
vol.rec ON|OFF (currently OFF)

pcm [<leftvol>:<rightvol>] (currently 74:74)

speaker <monovol> (currently 0)

line [<leftvol>:<rightvol>] (currently 0:0)
line.rec ON|OFF (currently OFF)

mic <monovol> (currently 1)
mic.rec ON|OFF (currently ON)

cd [<leftvol>:<rightvol>] (currently 74:74)
cd.rec ON|OFF (currently OFF)

igain [<leftvol>:<rightvol>] (currently 78:78)

aux1 [<leftvol>:<rightvol>] (currently 78:78)
aux1.rec ON|OFF (currently OFF)

phone [<leftvol>:<rightvol>] (currently 78:78)
phone.rec ON|OFF (currently OFF)

mono <monovol> (currently 76)
mono.rec ON|OFF (currently OFF)

video [<leftvol>:<rightvol>] (currently 76:76)
video.rec ON|OFF (currently OFF)


spdout.enable ON|OFF (currently ON)
spdout.adc/dac ON|OFF (currently ON)
spdout.pro <Consumer|Professional> (currently Consumer)
spdout.audio <AUDIO|DATA> (currently AUDIO)
spdout.copy ON|OFF (currently OFF)
spdout.pre-emph ON|OFF (currently OFF)
spdout.rate <48000|44100|32000> (currently 48000)
spdout.vbit ON|OFF (currently OFF)

spdin.enable ON|OFF (currently OFF)
spdin.monitor ON|OFF (currently ON)
spdin.pro <decimal value> (currently 0) (Read-only)
spdin.audio <decimal value> (currently 0) (Read-only)
spdin.copy <decimal value> (currently 0) (Read-only)
spdin.pre-emph <decimal value> (currently 0) (Read-only)
spdin.mode <decimal value> (currently 0) (Read-only)
spdin.category <decimal value> (currently 0) (Read-only)
spdin.genlevel <decimal value> (currently 0) (Read-only)
spdin.source <decimal value> (currently 0) (Read-only)
spdin.channel <decimal value> (currently 0) (Read-only)
spdin.rate <decimal value> (currently 44100) (Read-only)
spdin.clock <decimal value> (currently 0) (Read-only)
spdin.signal <decimal value> (currently 0) (Read-only)
spdin.vbit <decimal value> (currently 0) (Read-only)
vmix0-enable ON|OFF (currently ON)
vmix0-rate <decimal value> (currently 48000) (Read-only)
vmix0-channels <Stereo|Multich> (currently Stereo)
vmix0-src <Fast|Low|Medium|High|High+|Production|OFF> (currently Fast)
vmix0-outvol <monovol> (currently 24.8 dB)

vmix0-invol <monovol> (currently 25.0 dB)
vmix0.pcm1 [<leftvol>:<rightvol>] (currently 25.0:25.0 dB)
vmix0.pcm2 [<leftvol>:<rightvol>] (currently 25.0:25.0 dB)
vmix0.pcm3 [<leftvol>:<rightvol>] (currently 25.0:25.0 dB)
vmix0.pcm4 [<leftvol>:<rightvol>] (currently 25.0:25.0 dB)
oaner@russel-herin:~$ 
oaner@russel-herin:~$ ossinfo -v3
Version info: OSS 4.1 (b rc2/200811071353) (0x00040090) GPL
Platform: Linux/i686 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 (russel-herin)

Number of audio devices:	2
Number of audio engines:	7
Number of mixer devices:	1


Device objects
 0: osscore0 OSS core services
 1: oss_atiaudio0 ATI IXP200 interrupts=527234 (527234)
 2: oss_usb0 USB audio core services


Mixer devices
 0: AC97 Mixer (ALC250) (Mixer 0 of device object 1)
    Device file /dev/oss/oss_atiaudio0/mix0, Legacy device /dev/mixer0
    Priority: 2
    Caps: 
    Device handle: PCIff101179-0000:00:14.5-mx01
    Device priority: 2


Audio devices
ATI IXP200                        /dev/oss/oss_atiaudio0/pcm0  (device index 0)
    Legacy device /dev/dsp0
    Caps: DUPLEX TRIGGER MMAP 
    Modes: IN/OUT 
      Engine      1: 0/ATI IXP200
                     Busy (IN/OUT) label 'VMIX' 
      Engine      2: 1/ATI IXP200 (vmix)
                     Busy (OUT) by PID 5845 / rhythmbox label 'rhythmbox' 
      Engine      3: 2/ATI IXP200 (vmix)
                     Available for use 
      Engine      4: 3/ATI IXP200 (vmix)
                     Available for use 
      Engine      5: 4/ATI IXP200 (vmix)
                     Available for use 
      Engine      6: 5/ATI IXP200
                     Available for use 
    Input formats (0x00000410):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_AC3		- AC3 (Dolby Digital) encoded audio
    Output formats (0x00000410):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_AC3		- AC3 (Dolby Digital) encoded audio
    Device handle: PCIff101179-0000:00:14.5-au01
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 6
    Native sample rates (min - max): 48000 - 48000
    HW Type: Not indicated.
    Minimum latency: Not indicated

ATI IXP200 (SPDIF out)            /dev/oss/oss_atiaudio0/spdout  (device index 1)
    Legacy device /dev/dsp1
    Caps: TRIGGER MMAP 
    Modes: OUTPUT 
      Out engine  1: 6/ATI IXP200 (SPDIF out)
                     Available for use 
    Input formats (0x00000410):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_AC3		- AC3 (Dolby Digital) encoded audio
    Output formats (0x00000410):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_AC3		- AC3 (Dolby Digital) encoded audio
    Device handle: PCIff101179-0000:00:14.5-au02
    Related mixer dev: 0
    Sample rate source: 6
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 6
    Native sample rates (min - max): 48000 - 48000
    HW Type: Not indicated.
    Minimum latency: Not indicated



Worst case, can anyone just tell me how to get alsa back in.  The guide that the oss wiki links to is too hard to understand.  I seriously have reread it a dozen times and I have no idea what I supposed to do.

---

