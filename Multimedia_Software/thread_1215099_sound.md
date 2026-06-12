---
title: "sound"
date: 2009-07-16
forum: Multimedia Software
---

### Post by papaj on 2009-07-16
can anyone help, ive searched for weeks about sound issues with no luck and feel my meddling may not have helped.  the sound i am getting when playing audio is bitty, almost echo like and of low volume.
no better than no sound at all after the jaunty upgrade

 aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC262 Analog [ALC262 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC262 Digital [ALC262 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


lspci -v
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Device 1a46:1402
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at 99320000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

built in sound card
cannot find an alsa or oss driver for 82801H ICH8 Family 

please

---

### Post by Digitallysick on 2009-07-16
Sigh, you have the dreaded ALC262 that I have. Best to follow this

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

My speakers work, no mic

---

### Post by papaj on 2009-07-17
thanks for the response, i have been working away at this link for several hours now. have tried uninstall alsa reinstall alsa, oss  back to alsa again going to bed soon let u know how its gone later

thanks again

---

### Post by igorzwx on 2009-07-17
Do you mean it does not work with OSS4?

---

### Post by papaj on 2009-07-18
could not find driver for 82801H (ICH8 Family) in oss directory from link on page 152 of link suggested above

i will now look into oss4, not heard of this any tips thanks

i was maybe thinking of getting an extenal usb sound card, usefull for guitar playing and recording, any tips on type would be very helpful, cheers

---

### Post by papaj on 2009-07-18
installed oss4,  ICH8, deb installer, rebooted

mp3 track will only play in rhythmbox (with no output to speaker, not muted)
if sound prefs set to autodetect for music movies playback.

if movies music set to any of the oss4, mp3 will not play at all

either way no music 

help please

aplay -l  now says no soundcards found

perhaps i should try the tar?

thanks

---

### Post by igorzwx on 2009-07-18
read this:
[http://ubuntuforums.org/showthread.php?t=1213896](http://ubuntuforums.org/showthread.php?t=1213896)

---

### Post by markbuntu on 2009-07-18
These are extemely hardware specific problems with very specific solutions


[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

---

### Post by papaj on 2009-07-19
thanks 

tried this [http://shibuvarkala.blogspot.com/2009/04/howto-make-ubuntu-904-jaunty-jackalope.html](http://shibuvarkala.blogspot.com/2009/04/howto-make-ubuntu-904-jaunty-jackalope.html)

then followed the oss commands

papaj@papaj-desktop:~$ ossmix

Selected mixer 0/High Definition Audio ALC262

Known controls are:

codec1.jack.int-purple.mode1 <mix|mix|input> (currently mix)

codec1.jack.int-purple1 [<leftvol>:<rightvol>] (currently 29.9:29.9 dB)

codec1.jack.int-purple.mute1 ON|OFF (currently OFF)

codec1.jack.green.mode <mix|mix|input> (currently mix)

codec1.jack.green [<leftvol>:<rightvol>] (currently 29.9:29.9 dB)

codec1.jack.green.mute ON|OFF (currently OFF)

codec1.jack.int-purple.mute2 ON|OFF (currently OFF)

codec1.jack.int-purple.speaker- ON|OFF (currently OFF)

codec1.jack.int-purple.mix-mute ON|OFF (currently OFF)

codec1.jack.int-purple.mix <monovol> (currently 38.9 dB)

codec1.jack.pink.mode <mix|mix|input> (currently mix)

codec1.jack.pink [<leftvol>:<rightvol>] (currently 29.9:29.9 dB)

codec1.jack.pink.mute ON|OFF (currently OFF)

codec1.jack.int-purple.mode2 <mix|mix|input> (currently mix)

codec1.jack.int-purple2 [<leftvol>:<rightvol>] (currently 29.9:29.9 dB)

codec1.jack.int-purple.mute3 ON|OFF (currently OFF)

codec1.record.mix.mute.mic1 ON|OFF (currently OFF)

codec1.record.mix.mute.int-mic1 ON|OFF (currently OFF)

codec1.record.mix.mute.line-ou1 ON|OFF (currently OFF)

codec1.record.mix.mute.headpho1 ON|OFF (currently OFF)

codec1.record.mix.mute.mix1 ON|OFF (currently OFF)

codec1.record.mix1 [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)

codec1.record.mix.mute.mic2 ON|OFF (currently OFF)

codec1.record.mix.mute.int-mic2 ON|OFF (currently OFF)

codec1.record.mix.mute.line-ou2 ON|OFF (currently OFF)

codec1.record.mix.mute.headpho2 ON|OFF (currently OFF)

codec1.record.mix.mute.mix2 ON|OFF (currently OFF)

codec1.record.mix2 [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)

codec1.record.select.select <mic|int-mic|mix|dmic> (currently mic)

codec1.record.select [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)

codec1.misc.mic [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)

codec1.misc.int-mic [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)

codec1.misc.line-out [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)

codec1.misc.headphone [<leftvol>:<rightvol>] (currently 29.9:29.9 dB)

codec1.misc.mix1 <mic|int-mic> (currently mic)

codec1.misc.speaker-mute ON|OFF (currently OFF)

codec1.misc.mix-mute1 ON|OFF (currently OFF)

codec1.misc.mix2 [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)

codec1.misc.mix3 <speaker|mix> (currently speaker)

codec1.misc.headphone-mute ON|OFF (currently OFF)

codec1.misc.mix-mute2 ON|OFF (currently OFF)

codec1.misc.mix4 [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)

codec1.misc.mix5 <headphone|mix> (currently headphone)

vmix0-enable ON|OFF (currently ON)

vmix0-rate <decimal value> (currently 48000) (Read-only)

vmix0-channels <Stereo|Multich> (currently Stereo)

vmix0-src <Fast|Low|Medium|High|High+|Production|OFF> (currently Fast)

vmix0-outvol <monovol> (currently 25.0 dB)

vmix0-invol <monovol> (currently 25.0 dB)

vmix0.pcm6 [<leftvol>:<rightvol>] (currently 25.0:25.0 dB)

vmix0.pcm7 [<leftvol>:<rightvol>] (currently 25.0:25.0 dB)

vmix0.pcm8 [<leftvol>:<rightvol>] (currently 25.0:25.0 dB)

vmix0.pcm9 [<leftvol>:<rightvol>] (currently 25.0:25.0 dB)



papaj@papaj-desktop:~$ ossinfo -v3

Version info: OSS 4.1 (b 1052/200903240610) (0x00040100) 

Platform: Linux/i686 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009 (papaj-desktop)



Number of audio devices:	6

Number of audio engines:	10

Number of mixer devices:	1





Device objects

 0: osscore0 OSS core services

 1: oss_hdaudio0 Intel HD Audio interrupts=144 (1493)

    HD Audio controller Intel HD Audio

    Vendor ID    0x8086284b

    Subvendor ID 0x1a461402

     Codec  0: ALC262 (0x10ec0262/0x1a461402)

     Codec  1: Unknown (0x10573055)

 2: oss_usb0 USB audio core services





Mixer devices

 0: High Definition Audio ALC262 (Mixer 0 of device object 1)

    Device file /dev/oss/oss_hdaudio0/mix0, Legacy device /dev/mixer0

    Priority: 10

    Caps: 

    Device handle: PCI14021a46-0000:00:1b.0-mx01

    Device priority: 10





Audio devices

HD Audio play speaker             /dev/oss/oss_hdaudio0/pcm0  (device index 0)

    Legacy device /dev/dsp0

    Caps: DUPLEX TRIGGER MMAP 

    Modes: IN/OUT 

      Out engine  1: 0/HD Audio play speaker

                     Available for use 

      Engine      2: 6/HD Audio play speaker (vmix)

                     Available for use 

      Engine      3: 7/HD Audio play speaker (vmix)

                     Available for use 

      Engine      4: 8/HD Audio play speaker (vmix)

                     Available for use 

      Engine      5: 9/HD Audio play speaker (vmix)

                     Available for use 

    Input formats (0x00001010):

      AFMT_S16_LE	- 16 bit signed little endian

      AFMT_S32_LE	- 32 bit signed little endian

    Output formats (0x00001010):

      AFMT_S16_LE	- 16 bit signed little endian

      AFMT_S32_LE	- 32 bit signed little endian

    Device handle: PCI14021a46-0000:00:1b.0-au01

    Related mixer dev: 0

    Sample rate source: 0

    Preferred channel configuration: Not indicated

    Supported number of channels (min - max): 2 - 8

    Native sample rates (min - max): 44100 - 192000 (44100,48000,96000,192000)

    HW Type: Not indicated.

    Minimum latency: Not indicated



HD Audio play headphone           /dev/oss/oss_hdaudio0/pcm1  (device index 1)

    Legacy device /dev/dsp1

    Caps: TRIGGER MMAP 

    Modes: OUTPUT 

      Out engine  1: 1/HD Audio play headphone

                     Available for use 

    Input formats (0x00001010):

      AFMT_S16_LE	- 16 bit signed little endian

      AFMT_S32_LE	- 32 bit signed little endian

    Output formats (0x00001010):

      AFMT_S16_LE	- 16 bit signed little endian

      AFMT_S32_LE	- 32 bit signed little endian

    Device handle: PCI14021a46-0000:00:1b.0-au02

    Related mixer dev: 0

    Sample rate source: 0

    Preferred channel configuration: Not indicated

    Supported number of channels (min - max): 2 - 2

    Native sample rates (min - max): 44100 - 192000 (44100,48000,96000,192000)

    HW Type: Not indicated.

    Minimum latency: Not indicated



HD Audio play spdif-out           /dev/oss/oss_hdaudio0/spdout0  (device index 2)

    Legacy device /dev/dsp2

    Caps: TRIGGER MMAP 

    Modes: OUTPUT 

      Out engine  1: 2/HD Audio play spdif-out

                     Available for use 

    Input formats (0x00001410):

      AFMT_S16_LE	- 16 bit signed little endian

      AFMT_AC3		- AC3 (Dolby Digital) encoded audio

      AFMT_S32_LE	- 32 bit signed little endian

    Output formats (0x00001410):

      AFMT_S16_LE	- 16 bit signed little endian

      AFMT_AC3		- AC3 (Dolby Digital) encoded audio

      AFMT_S32_LE	- 32 bit signed little endian

    Device handle: PCI14021a46-0000:00:1b.0-au03

    Related mixer dev: 0

    Sample rate source: 0

    Preferred channel configuration: Not indicated

    Supported number of channels (min - max): 2 - 2

    Native sample rates (min - max): 44100 - 192000 (44100,48000,96000,192000)

    HW Type: Not indicated.

    Minimum latency: Not indicated



HD Audio rec mix                  /dev/oss/oss_hdaudio0/pcmin0  (device index 3)

    Legacy device /dev/dsp3

    Caps: DUPLEX TRIGGER MMAP 

    Modes: IN/OUT 

      In engine   1: 3/HD Audio rec mix

                     Available for use 

      Engine      2: 6/HD Audio play speaker (vmix)

                     Available for use 

      Engine      3: 7/HD Audio play speaker (vmix)

                     Available for use 

      Engine      4: 8/HD Audio play speaker (vmix)

                     Available for use 

      Engine      5: 9/HD Audio play speaker (vmix)

                     Available for use 

    Input formats (0x00001010):

      AFMT_S16_LE	- 16 bit signed little endian

      AFMT_S32_LE	- 32 bit signed little endian

    Output formats (0x00001010):

      AFMT_S16_LE	- 16 bit signed little endian

      AFMT_S32_LE	- 32 bit signed little endian

    Device handle: PCI14021a46-0000:00:1b.0-au04

    Related mixer dev: 0

    Sample rate source: 0

    Preferred channel configuration: Not indicated

    Supported number of channels (min - max): 2 - 2

    Native sample rates (min - max): 44100 - 96000 (44100,48000,96000)

    HW Type: Not indicated.

    Minimum latency: Not indicated



HD Audio rec mix                  /dev/oss/oss_hdaudio0/pcmin1  (device index 4)

    Legacy device /dev/dsp4

    Caps: TRIGGER MMAP 

    Modes: INPUT  

      In engine   1: 4/HD Audio rec mix

                     Available for use 

    Input formats (0x00001010):

      AFMT_S16_LE	- 16 bit signed little endian

      AFMT_S32_LE	- 32 bit signed little endian

    Output formats (0x00001010):

      AFMT_S16_LE	- 16 bit signed little endian

      AFMT_S32_LE	- 32 bit signed little endian

    Device handle: PCI14021a46-0000:00:1b.0-au05

    Related mixer dev: 0

    Sample rate source: 0

    Preferred channel configuration: Not indicated

    Supported number of channels (min - max): 2 - 2

    Native sample rates (min - max): 44100 - 96000 (44100,48000,96000)

    HW Type: Not indicated.

    Minimum latency: Not indicated



HD Audio rec select               /dev/oss/oss_hdaudio0/pcmin2  (device index 5)

    Legacy device /dev/dsp5

    Caps: TRIGGER MMAP 

    Modes: INPUT  

      In engine   1: 5/HD Audio rec select

                     Available for use 

    Input formats (0x00001010):

      AFMT_S16_LE	- 16 bit signed little endian

      AFMT_S32_LE	- 32 bit signed little endian

    Output formats (0x00001010):

      AFMT_S16_LE	- 16 bit signed little endian

      AFMT_S32_LE	- 32 bit signed little endian

    Device handle: PCI14021a46-0000:00:1b.0-au06

    Related mixer dev: 0

    Sample rate source: 0

    Preferred channel configuration: Not indicated

    Supported number of channels (min - max): 2 - 2

    Native sample rates (min - max): 44100 - 96000 (44100,48000,96000)

    HW Type: Not indicated.

    Minimum latency: Not indicated




and finally

papaj@papaj-desktop:~$ osstest
Sound subsystem and version: OSS 4.1 (b 1052/200903240610) (0x00040100)
Platform: Linux/i686 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009

*** Scanning sound adapter #-1 ***
/dev/oss/oss_hdaudio0/pcm0 (audio engine 0): HD Audio play speaker
- Performing audio playback test... 
  <left> Device returned error: Input/output error
/dev/oss/oss_hdaudio0/pcm1 (audio engine 1): HD Audio play headphone
- Performing audio playback test... 
  <left> OK <right> OK <stereo> OK <measured srate 15259.00 Hz (-68.21%)> 
/dev/oss/oss_hdaudio0/spdout0 (audio engine 2): HD Audio play spdif-out
- Performing audio playback test... 
  <left> OK <right> OK <stereo> OK <measured srate 15171.00 Hz (-68.39%)> 
/dev/oss/oss_hdaudio0/pcmin0 (audio engine 3): HD Audio rec mix
- Skipping input only device
/dev/oss/oss_hdaudio0/pcmin1 (audio engine 4): HD Audio rec mix
- Skipping input only device
/dev/oss/oss_hdaudio0/pcmin2 (audio engine 5): HD Audio rec select
- Skipping input only device

*** Some errors were detected during the tests ***


error found in audio play speaker? in oss test

also in oss mix - codec1.jack.int-purple.speaker- ON|OFF (currently OFF)

should this be on?

using oss play then oss test result is

papaj@papaj-desktop:~$ osstest
Sound subsystem and version: OSS 4.1 (b 1052/200903240610) (0x00040100)
Platform: Linux/i686 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009

*** Scanning sound adapter #-1 ***
/dev/oss/oss_hdaudio0/pcm0 (audio engine 0): HD Audio play speaker
- Performing audio playback test... 
  <left> OK <right> OK <stereo> OK <measured srate 15351.00 Hz (-68.02%)> 
/dev/oss/oss_hdaudio0/pcm1 (audio engine 1): HD Audio play headphone
- Performing audio playback test... 
  <left> OK <right> OK <stereo> OK <measured srate 15172.00 Hz (-68.39%)> 
/dev/oss/oss_hdaudio0/spdout0 (audio engine 2): HD Audio play spdif-out
- Performing audio playback test... 
  <left> OK <right> OK <stereo> OK <measured srate 15172.00 Hz (-68.39%)> 
/dev/oss/oss_hdaudio0/pcmin0 (audio engine 3): HD Audio rec mix
- Skipping input only device
/dev/oss/oss_hdaudio0/pcmin1 (audio engine 4): HD Audio rec mix
- Skipping input only device
/dev/oss/oss_hdaudio0/pcmin2 (audio engine 5): HD Audio rec select
- Skipping input only device

*** All tests completed OK ***

seems ok but audacious has no sound when playing mp3 file?

sorry if i seem slow and long winded, its an extra big learning curve im on.
 thanks all again

---

### Post by papaj on 2009-07-19
just a thought alsa and pulseaudio are still listed as options in sound pref
although not selected.  selections for playback are all set to oss4 hd audio play speaker
 
i thought i had removed alsa?

should i do any thing with pulse? sure i removed it before installing oss

thanks again

---

### Post by igorzwx on 2009-07-19
[http://wiki.archlinux.org/index.php/...DAudio_devices]("http://wiki.archlinux.org/index.php/OSS#Troubleshooting_HDAudio_devices")
**  Troubleshooting HDAudio devices **

 **  Understanding why problems arise **

 If you have a HDAudio sound device, it's very likely that you will have to adjust some mixer settings before your sound works. 
HDAudio devices are very powerful in the sense that they can contain a lot of small circuits (called *widgets*) that can be adjusted by software at any time. These controls are exposed to the mixer, and they can be used, for example, to turn the earphone jack into a sound input jack instead of a sound output jack. 
However, there is a side effect, mainly because the HDAudio standard is more flexible than it perhaps should be, and because the vendors often only care to get their *official drivers* working. 
Then, when using HDAudio devices, you often find disorganized mixer controls, that doesn't work at all by default, and you are forced to try every mixer control combination, until it works. 
 **  How to solve **

 Open ossxmix and try to change every mixer control in the *middle area*, that contains the sound card specific controls, as explained in the previous "[The mixer]("http://wiki.archlinux.org/index.php/OSS#The_mixer")" section. 
You'll probably want to setup a program to record/play continously in the background (e.g. [COLOR=#000055][FONT=monospace]ossrecord - [/FONT][/COLOR]  for recording or [COLOR=#000055][FONT=monospace]osstest -lV[/FONT][/COLOR] for playing), while changing mixer settings in ossxmix in the foreground. 
 
[LIST]
[*] Raise every volume control slider.
[*] In each option box, try to change the selected option, trying all the possible combinations.
[*] If you get noise, try to lower and/or mute some volume controls, until you find the source of the noise.
[/LIST]
 Please note again that you do **not** need to change any controls in the *top area* nor in the *bottom area*, as they are virtual vmix-related mixer controls. 
 **  Troubleshooting other issues **

 
[LIST]
[*] If you get distorted sound, try lowering some volume control sliders.
[/LIST]
 
[LIST]
[*] If you need to change the default sound card, look at [here]("http://www.opensound.com/wiki/index.php/Tips_And_Tricks#Changing_the_default_sound_output").
[/LIST]
 
[LIST]
[*] If you have another issues, try searching or asking for help at the [4front forums]("http://www.4front-tech.com/forum").
[/LIST]
 **  No audio in Banshee or Other Gstreamer Programs **

 Ensure that you have not inadvertantly installed pulseaudio or gstreamer0.10-pulse. This is easy mistake to make when installing all the gstreamer codecs.

---

### Post by igorzwx on 2009-07-19
you do not need to remove ALSA (it can be utilized with OSS4)

You have alredy blacklisted ALSA modules (it is enough)

read that wiki about HDA troubleshooting

---

### Post by igorzwx on 2009-07-19
run

osstest

before and after experiments

---

### Post by papaj on 2009-07-19
yet another thought, oh no i hear u sigh.

in volume control  playback only shows codec1 misc headphones.

should any of the others in 'vol control prefs' be checked? if so which ones i cant find any guides on this

cheers

sorry didnt relize that you'd replied so soon. will check out your post's above 

thanks

---

### Post by igorzwx on 2009-07-19
1. type on terminal

osstest

2. type on terminal

ossxmix

---

### Post by papaj on 2009-07-19
getting no directory on both commands now?

test was working earlier

---

### Post by papaj on 2009-07-19
i re did instructions on [https://help.ubuntu.com/community/OpenSound#Installing%20Prerequisite%20Packages](https://help.ubuntu.com/community/OpenSound#Installing%20Prerequisite%20Packages)

re-installed deb package

and now have No volume control GStreamer plugins and/or devices found

---

### Post by igorzwx on 2009-07-19
it seems that you are doing this too fast

read this:
[https://help.ubuntu.com/community/OpenSound#Recovering%20From%20a%20Failed%20.deb%20Install](https://help.ubuntu.com/community/OpenSound#Recovering%20From%20a%20Failed%20.deb%20Install)
**Troubleshooting**

 If you run into problems, follow these steps first: 
 
**Recovering From a Failed .deb Install**

 If you use the .deb package and it fails to install completely, [use this procedure]("http://ubuntuforums.org/showpost.php?p=5055305&postcount=105") to remove it. 



then read manual once more.
And make new installation.
Try to make it carefully


Good luck!

 
[B]
[/B]

---

### Post by papaj on 2009-07-19
thanks for all help im going back to begining and hope to see where i went wrong if i retrace my steps

 'im going outside i might be some time'

---

### Post by igorzwx on 2009-07-19
very good idea!

it is not really a difficult task

I have an old box for experiments.
You learn the art very fast

---

### Post by igorzwx on 2009-07-19
The most important thing is intallation of OSS4

install OSS4

osstest

and so on.

then try

ossplay

man ossplay

When ossplay is working, you can fix all your players one after another.

---

### Post by igorzwx on 2009-07-19
[http://shibuvarkala.blogspot.com/2009/04/howto-make-ubuntu-904-jaunty-jackalope.html](http://shibuvarkala.blogspot.com/2009/04/howto-make-ubuntu-904-jaunty-jackalope.html)

---

### Post by igorzwx on 2009-07-19
when medibuntu is enabled
you can install skype-static-oss

---

### Post by papaj on 2009-07-20
hello again if your still with me thanks for your patience

good news and bad

ossxmix ,brings up desk ok

osstest ,works, all outputs getting ok ,though sound is a bit choppy and left speaker sounds a bit central plus nothing is actually heard in headphones.
skips input only device

ossplay ,brings up list of options (i take it this is good)

ossplay<filename>, brings (filename)mp3: Unrecognized audio file type.

man ossplay , brings oss user command list

so mp3 not recognised ( i have installed media codecs?)

and im not sure if im a bit dumb on this one but , how do these commands work , tried typing -o? ,bash command not found?

i think i will go out again , pea picking was very therapeutic last time

thanks for any input

---

### Post by igorzwx on 2009-07-20
QUOTE:

ossplay<filename>, brings (filename)mp3: Unrecognized audio file type.

End of QUOTE

ossplay should not play mp3, by definition.

As I understood, you have already codecs from Medibuntu
installed.
Mp3 files can be played with VLC,
but you shoud configure VLC to use OSS4 devices
VLC -> Tools -> Preferences -> Audio -> output -> Unix OSS
see the screenshot

---

### Post by igorzwx on 2009-07-20
Sound might be strange if you use USB audio devices.
The reason is simple.
USB audio devices are not supported by OSS4

---

### Post by papaj on 2009-07-20
thanks for reply

vlc is already set to oss as you recommend

no usb device used for music just file transfer from the could do without msoft, music from music folder.

vlc will play the track but no sound,

osstest still ok before and after trying vlc.

i did read somewhere (iforget  where now) to soundoff then soundon 

papaj@papaj-desktop:~$ sudo soundoff
[sudo] password for papaj: 

Some applications are still using OSS - cannot unload

3198 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFIID:GNOME_MixerApplet_Factory --oaf-ior-fd=19
3198 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFIID:GNOME_MixerApplet_Factory --oaf-ior-fd=19

Please stop these applications and run soundoff again

could this be a problem?

do you know what could be running vlc is not on and no other media program

---

### Post by igorzwx on 2009-07-20
open synaptic and deinstall
pulse plug for vlc

perhaps, deinstall other pulse things too

check with task manager which processes are running

reboot and make osstest first

---

### Post by igorzwx on 2009-07-20
deinstall gnome-alsa-mixer (and similar things),
or disable it (remove from panel)
You do not need them now.

You have ossxmix, it is enough

---

### Post by igorzwx on 2009-07-20
Does your Skype work now?

---

### Post by papaj on 2009-07-20
sorry bear with me just de-installed pulse & rebooted osstest still ok 

will take a while to follow other directions 

glad of your guidance

---

### Post by igorzwx on 2009-07-20
install Skype and we can test it.

skype-static-oss

---

### Post by papaj on 2009-07-20
skype failed to install via Gdebi installer

no gnome alsa mixer installed

in task manager mixer applet2 currently sleeping

think this is what was refered to when soundoff failed

mixer applet2 in synaptic lists

library for GNOME Panel applets

ALSA utilities

GNOME media utilities

Various applets for GNOME 2 panel - binary files

this last one i'll uninstall looks like the one, can always re-install if wrong

will have to remove skype and re-instal with terminal

---

### Post by igorzwx on 2009-07-20
you should simply deinstall skype without special ceremonies.
then you should open Synaptic and install
skype-static-oss

it should be there (in Synaptic), if Medibuntu repositories are enabled
read this too:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by igorzwx on 2009-07-20
it might be difficult to deinstall skype, if it is running.
kill it and deinstall

---

### Post by papaj on 2009-07-20
rebooted 
osstest still works , soundoff/on works,  soundon message

papaj@papaj-desktop:~$ sudo soundon
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ipwraw, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ipwraw, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ipwraw, it will be ignored in a future release.

osstest still completed ok

vlc still plays mp3 with no sound

skype installed ok it auto uninstalled skype leaving skype common in

no sound on test sound skype test call went ok but no sound

---

### Post by papaj on 2009-07-20
skype stevepapaj

---

### Post by igorzwx on 2009-07-20
system -> preferences -> sound
change everything to OSS4

---

### Post by papaj on 2009-07-20
low sound now coming when playing mp3/vlc
using ossxmix going to play some more tommorrow 
thanks again for your input

---

### Post by igorzwx on 2009-07-20
read this too:
[http://www.opensound.com/wiki/index.php/Configuring_Applications_for_OSSv4](http://www.opensound.com/wiki/index.php/Configuring_Applications_for_OSSv4)

tried to call you.
We can continue tomorrow.
Most important, OSS4 is now working.
aps can be fixed one after one

---

### Post by papaj on 2009-07-20
louder and louder feels good
so pleased
thanks 

today vlc tomorrow skype

should get some sleep now ive found my way out of the 'wild wild wood'

sorry mp3 was weller

sorry not noticed a caller
thanks agian

---

### Post by papaj on 2009-07-21
frustrating couple of hours

boot

open terminal

ossplay - ok

osstest - ok

ossxmix - ok

open vlc play file various humming type noises, adjusting ossxmix no results

reboot several times, same result, finally 

vlc - ok (trying this in terminal now)

select to open file (mp3)

terminal (vlc) 

[00000471] oss audio output error: write failed (Input/output error)
[00000471] oss audio output error: write failed (Input/output error)

killed vlc 

retest osstest - ok

checked vlc audio output still unix oss

going to try uninstall/reinstall vlc 

ps tried skype again test call works without sound and test sound not working will look into this later

would not be suprised if you gave up, im at the point of starting to manically laugh aaaaaaaaaaaaaarrggggggghhhhhhhh

cheers

---

### Post by igorzwx on 2009-07-21
Try this:
[http://wiki.archlinux.org/index.php/OSS#Troubleshooting](http://wiki.archlinux.org/index.php/OSS#Troubleshooting)
**  Troubleshooting HDAudio devices **

 **  Understanding why problems arise **

 If you have a HDAudio sound device, it's very likely that you will have to adjust some mixer settings before your sound works. 
HDAudio devices are very powerful in the sense that they can contain a lot of small circuits (called *widgets*) that can be adjusted by software at any time. These controls are exposed to the mixer, and they can be used, for example, to turn the earphone jack into a sound input jack instead of a sound output jack. 
However, there is a side effect, mainly because the HDAudio standard is more flexible than it perhaps should be, and because the vendors often only care to get their *official drivers* working. 
Then, when using HDAudio devices, you often find disorganized mixer controls, that doesn't work at all by default, and you are forced to try every mixer control combination, until it works. 
 **  How to solve **

 Open ossxmix and try to change every mixer control in the *middle area*, that contains the sound card specific controls, as explained in the previous "[The mixer]("http://wiki.archlinux.org/index.php/OSS#The_mixer")" section. 
You'll probably want to setup a program to record/play continously in the background (e.g. [COLOR=#000055][FONT=monospace]ossrecord - [/FONT][/COLOR]  for recording or [COLOR=#000055][FONT=monospace]osstest -lV[/FONT][/COLOR] for playing), while changing mixer settings in ossxmix in the foreground. 
 
[LIST]
[*] Raise every volume control slider.
[*] In each option box, try to change the selected option, trying all the possible combinations.
[*] If you get noise, try to lower and/or mute some volume controls, until you find the source of the noise.
[/LIST]
 Please note again that you do **not** need to change any controls in the *top area* nor in the *bottom area*, as they are virtual vmix-related mixer controls. 
 **  Troubleshooting other issues **

 
[LIST]
[*] If you get distorted sound, try lowering some volume control sliders.
[/LIST]
 
[LIST]
[*] If you need to change the default sound card, look at [here]("http://www.opensound.com/wiki/index.php/Tips_And_Tricks#Changing_the_default_sound_output").
[/LIST]
 
[LIST]
[*] If you have another issues, try searching or asking for help at the [4front forums]("http://www.4front-tech.com/forum").
[/LIST]
 **  No audio in Banshee or Other Gstreamer Programs **

 Ensure that you have not inadvertantly installed pulseaudio or gstreamer0.10-pulse. This is easy mistake to make when installing all the gstreamer codecs. 
 **  Tips and Tricks **

 **  Using multimedia keys with OSS **

 An easy way to mute/unmute and increase/decrease the volume is to use the [[COLOR=#000055][FONT=monospace]ossvol[/FONT][/COLOR] script]("http://www.opensound.com/wiki/index.php/Tips_And_Tricks#ossvol"). It is available in [AUR]("http://wiki.archlinux.org/index.php/AUR") but **the package is out of date as of 20 June 2009**. 
Once you installed it try to toggle the sound: 
 $ ossvol -t
Type [COLOR=#000055][FONT=monospace]ossvol -h[/FONT][/COLOR] for the other commands. 
If you don't know how to assign commands to your multimedia keys, see [Extra Keyboard Keys]("http://wiki.archlinux.org/index.php/Extra_Keyboard_Keys"). 
 ** [COLOR=#000055][FONT=monospace]ossvol[/FONT][/COLOR] troubleshooting**

 If you get an error like: 
 Bad mixer control name(987) 'vol'
you need to edit the script ([COLOR=#005500][FONT=monospace]/usr/bin/ossvol[/FONT][/COLOR]) and change the value of the [COLOR=#000055][FONT=monospace]CHANNEL[/FONT][/COLOR] variable which is at the beginning of the script. For example mine is [COLOR=#000055][FONT=monospace]CHANNEL="vmix0-outvol"[/FONT][/COLOR].

---

### Post by papaj on 2009-07-21
have been trying  alot of tweaks in ossxmix as suggested no results

have been reading the above
under changing default sound output

Q? skype pref audio - sound in -out and ringing /dev/dsp

vlc pref audio type = unix oss,  device = /dev/dsp

should this be oss in both cases?

 ossinfo -a
Audio devices
HD Audio play speaker             /dev/oss/oss_hdaudio0/pcm0  (device index 0)
HD Audio play headphone           /dev/oss/oss_hdaudio0/pcm1  (device index 1)
HD Audio play spdif-out           /dev/oss/oss_hdaudio0/spdout0  (device index 2)
HD Audio rec mix                  /dev/oss/oss_hdaudio0/pcmin0  (device index 3)
HD Audio rec mix                  /dev/oss/oss_hdaudio0/pcmin1  (device index 4)
HD Audio rec select               /dev/oss/oss_hdaudio0/pcmin2  (device index 5)


not to sure of this procedure

---

### Post by igorzwx on 2009-07-21
dsp is OSS device everything is OK.

try system -> preferences -> sound

see my settings in the screenshots

---

### Post by igorzwx on 2009-07-21
do you have skype-static-oss from Medibuntu, or something else?

---

### Post by papaj on 2009-07-21
yes all the same in skype

in sound slight diference but all set to oss4 hd audio play speaker

default mixer is hi def audio alc262(ossv4 audio mixer)

ps recieved your call no sound though

---

### Post by igorzwx on 2009-07-21
install Audacity, it shoud work out of the box.
install Epiphany Web Browser and try to play something in youtube

but  system -> preferences -> sound
change everything to OSS4

---

### Post by igorzwx on 2009-07-21
QUOTE:
ossplay - ok

osstest - ok

Does it mean that ossplay plays on one device,
and Skype to another?

man ossplay

---

### Post by igorzwx on 2009-07-21
man osstest

 It is possible to test just one of the available  audio  devices  by
          giving  its  number on command line (for example osstest 1). Use the
          device index numbers reported by "ossinfo -a".

       ·  Use the -l command line option to loop the test infinitely.

       ·  Virtual mixer devices will not be tested. Use the  -V  command  line
          option to force test of virtual devices.

---

### Post by papaj on 2009-07-21
papaj@papaj-desktop:~$ ossplay
Usage: ossplay [options] filename(s)
  Options:  -v             Verbose output.
            -q             No informative printouts.
            -d<devname>    Change output device.
            -g<gain>       Change gain.
            -s<rate>       Change playback rate.
            -f<fmt>|?      Change/Query input format.
            -c<channels>   Change number of channels.
            -o<playtgt>|?  Select/Query output target.
            -l             Loop playback indefinitely.
            -F             Treat all input as raw PCM.
            -S<secs>       Start playing from offset.
            -R             Open sound device in raw mode.


audacity hums pretty much the same as vlc 

thinking if no luck will try reinstall oss4 tomorrow

---

### Post by papaj on 2009-07-21
osstest doesnt work when vlc audacity or skype are open

*** Scanning sound adapter #-1 ***
/dev/oss/oss_hdaudio0/pcm0 (audio engine 0): HD Audio play speaker
Note! Device is in use (by PID 0/VMIX) but will try anyway
- Performing audio playback test... 
  <left> Device returned error: Input/output error
/dev/oss/oss_hdaudio0/pcm1 (audio engine 1): HD Audio play headphone
- Performing audio playback test... 
  <left> OK <right> OK <stereo> 

at least the audio playback test reports device in use

---

### Post by igorzwx on 2009-07-21
QUOTE:
osstest doesnt work when vlc audacity or skype are open

*** Scanning sound adapter #-1 ***
/dev/oss/oss_hdaudio0/pcm0 (audio engine 0): HD Audio play speaker
Note! Device is in use (by PID 0/VMIX) but will try anyway

It is a configuration error!
No reason for new installation.
You should ask on OSS4 forum.
I have not HDA, I cannot help much.
But is should be something very simple.

In short, ask on OSS4 forum,
and I will try ask some friends too.

---

### Post by papaj on 2009-07-21
thanks igor 

running out of time for me today will have a look into this tomorrow

cheers

---

### Post by igorzwx on 2009-07-21
Perhaps, this may help.
On the screenshot (OSS Mixer), you may see that I play
music in 3 Players simultaneously (VLC, Audacious, and Totem)
and mix the sound in "vmix0"

But this is a very old box with a simple sound card.
And a lot of things to adjust.
You may have much more such things in your HDA,
and more work to set it right.

---

### Post by igorzwx on 2009-07-22
Hi Steve!

 Could you please post a screenshot of your mixer window?

Open your OSS Mixer GUI (ossxmix)

Click on the Mixer window (to select this window),
then Alt+Print and save screenshot.

Then upload it here.

see below "Manage Attachments" (click on it)
then select the screenshot
then click on "Upload"
it will be attached to your post.

Best,
Igor

---

### Post by papaj on 2009-07-22
just booted up 

terminal commands
ossplay

osstest

test played ok with this screenshot 
not had a chance to look into your suggestions from yesterday

---

### Post by papaj on 2009-07-22
sorry just checked that here's second half

---

