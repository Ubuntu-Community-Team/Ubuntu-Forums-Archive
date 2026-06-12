---
title: "big mistake - gstreamer, alsa, plz help!!!!!"
date: 2009-07-18
forum: Multimedia Software
---

### Post by eldersoares on 2009-07-18
jaunty acer aspire 5100 soud card ati sb, i guess

long story:

1) microphones (integrated and not-integ) never worked. so i installed alsa-driver from source. it worked ONCE, and then, don't know if i changed something in alsamixer (such a mess all these configs!)... never worked anymore.

2) i tried to solve the good-old bug in rhythmbox that keeps trying to download codecs in my 20,000 music collection, repeatdly. so i reinstalled it from source. it asked me for a LOT LOT of packages.

3) so i had to install gstreamer and gst-plugins from source. and well.... rhythm, totem and amarok stopped playing any sound

4) sooo i uninstalled gstreamer, gst-plugins from the source folder, and then rhythm, totem and bla bla bla blaa anything i found similar to gst in synaptics. installed everything again from the packages, rebooted and yet no sound.

5) my volume control appears always muted and when i double click, error message! in system-preferences-sound, no device appears to choose in the combo-boxes. however login sound and sounds through flash player (in firefox, in you tube, f.ex.) work perfectly.

6) i can't live without music! i tried to uninstall the main gstreamer package (iguess) but it would also unisntall ubuntu-desktop, and i think that's not a good idea!

does anybody??????
thanks a lot

---

### Post by igorzwx on 2009-07-18
If you cannot live without music,
you may better use OSS4, not ALSA.

---

### Post by eldersoares on 2009-07-18
does skype work with oss4?

---

### Post by igorzwx on 2009-07-18
I works perfectly on my old boxes.
No delay, no latency, no noise.
Fantastic quality.
Ukraine, Australia, Chile, everywhere.

for OSS4 -> skype-static-oss
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)
[http://wiki.archlinux.org/index.php/OSS](http://wiki.archlinux.org/index.php/OSS)

---

### Post by igorzwx on 2009-07-18
Ekiga works well with OSS4 too
But few people use it.

---

### Post by eldersoares on 2009-07-18
yeah, actually i'd love to use ekiga, but none of my contacts use it, neither they have linux... :(

but, attention! as i thought (and according to the error messages) the problem is mainly with gstreamer. because in kde and with xine, i can hear perfectly... i guess if i change alsa to oss, the problem will persist. but i'll try.

i'd also like to know if i can put back my old gstreamer packages (i've already uninstalled the compiled ones and reinstalled the packages thru synaptic) to make it work as before. OR find a way to change this "music engine" in gnome for xine, rather than gstreamer.

;)

---

### Post by igorzwx on 2009-07-18
Try to make it carefully.
read howto
read pdf doc for OSS4

usefull commands:

osstext

ossplay

ossrecord

ossmix

ossxmix   [GUI mixer for OSS4]

QUOTE:
If you have OSS installed properly, but still have issues, the OpenSound project has free user support forums and an IRC channel. Be sure to include the output from these commands so the experts don't have to prompt you for them 



ossmix

ossinfo -v3

Also, you'll want to note if the osstest command works and plays sound.

---

### Post by eldersoares on 2009-07-18
the same... nothing plays and in system-preferences-sound there are still no devices. actually, after this, neither in kde it works anymore. it shows an error message saying that the sound devices were removed. however, if i try osstest in terminal, i can hear a sound. :/

---

### Post by igorzwx on 2009-07-18
if you hear sound with osstest,
everything is perfectly O.K.

---

### Post by igorzwx on 2009-07-18
I want to see the output of these commands:

ossmix

ossinfo -v3

---

### Post by igorzwx on 2009-07-18
"in system-preferences-sound there are still no devices."

make reboot, and configure your apps to use OSS4

---

### Post by eldersoares on 2009-07-18
$ ossmix
Selected mixer 0/High Definition Audio ALC883
Known controls are:
jack.fp-black.mode <front|rear|center/LFE|side|pcm4|input> (currently front)
jack.fp-black [<leftvol>:<rightvol>] (currently 29.9:29.9 dB)
jack.fp-black.mute ON|OFF (currently OFF)
jack.fp-pink.mode <front|rear|center/LFE|side|pcm4|input> (currently front)
jack.fp-pink [<leftvol>:<rightvol>] (currently 29.9:29.9 dB)
jack.fp-pink.mute ON|OFF (currently OFF)
jack.fp-blue.mode <front|rear|center/LFE|side|pcm4|input> (currently input)
jack.fp-blue [<leftvol>:<rightvol>] (currently 29.9:29.9 dB)
jack.fp-blue.mute ON|OFF (currently OFF)
record.mix.mute.fp-mic1 ON|OFF (currently OFF)
record.mix.mute.fp-linein1 ON|OFF (currently OFF)
record.mix.mute.fp-headphone1 ON|OFF (currently OFF)
record.mix.mute.input-mix1 ON|OFF (currently OFF)
record.mix1 [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
record.mix.mute.fp-mic2 ON|OFF (currently OFF)
record.mix.mute.fp-linein2 ON|OFF (currently OFF)
record.mix.mute.fp-headphone2 ON|OFF (currently OFF)
record.mix.mute.input-mix2 ON|OFF (currently OFF)
record.mix2 [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
misc.fp-mic [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
misc.fp-linein [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
misc.fp-headphone [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
misc.input-mix <fp-mic|fp-linein> (currently fp-mic)
misc.front-mute ON|OFF (currently OFF)
misc.input-mix-mute1 ON|OFF (currently OFF)
misc.front1 [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
misc.front2 <front|input-mix> (currently front)
misc.rear-mute ON|OFF (currently OFF)
misc.input-mix-mute2 ON|OFF (currently OFF)
misc.rear1 [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
misc.rear2 <rear|input-mix> (currently rear)
misc.center/lfe-mute ON|OFF (currently OFF)
misc.input-mix-mute3 ON|OFF (currently OFF)
misc.center/lfe1 [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
misc.center/lfe2 <center/LFE|input-mix> (currently center/LFE)
misc.side-mute ON|OFF (currently OFF)
misc.input-mix-mute4 ON|OFF (currently OFF)
misc.side1 [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
misc.side2 <side|input-mix> (currently side)
misc.pcm4-mute ON|OFF (currently OFF)
misc.input-mix-mute5 ON|OFF (currently OFF)
misc.pcm41 [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
misc.pcm42 <pcm4|input-mix> (currently pcm4)
vmix0-enable ON|OFF (currently ON)
vmix0-rate <decimal value> (currently 48000) (Read-only)
vmix0-channels <Stereo|Multich> (currently Stereo)
vmix0-src <Fast|Low|Medium|High|High+|Production|OFF> (currently Fast)
vmix0-outvol <monovol> (currently 25.0 dB)
vmix0-invol <monovol> (currently 25.0 dB)
vmix0.pcm10 [<leftvol>:<rightvol>] (currently 25.0:25.0 dB)
vmix0.pcm11 [<leftvol>:<rightvol>] (currently 25.0:25.0 dB)
vmix0.pcm12 [<leftvol>:<rightvol>] (currently 25.0:25.0 dB)
vmix0.pcm13 [<leftvol>:<rightvol>] (currently 25.0:25.0 dB)





$ ossinfo -v3
Version info: OSS 4.1 (b 1052/200903240621) (0x00040100) 
Platform: Linux/x86_64 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 22:12:12 UTC 2009 (atan-laptop)

Number of audio devices:	10
Number of audio engines:	14
Number of mixer devices:	1


Device objects
 0: osscore0 OSS core services
 1: oss_hdaudio0 ATI HD Audio interrupts=906 (906)
    HD Audio controller ATI HD Audio
    Vendor ID    0x1002437b
    Subvendor ID 0x1025009f
     Codec  0: ALC883 (0x10ec0883/0x1025009f)
     Codec  1: Conexant2bfa (0x14f12bfa)
 2: oss_usb0 USB audio core services


Mixer devices
 0: High Definition Audio ALC883 (Mixer 0 of device object 1)
    Device file /dev/oss/oss_hdaudio0/mix0, Legacy device /dev/mixer0
    Priority: 10
    Caps: 
    Device handle: PCI009f1025-0000:00:14.2-mx01
    Device priority: 10


Audio devices
HD Audio play front               /dev/oss/oss_hdaudio0/pcm0  (device index 0)
    Legacy device /dev/dsp0
    Caps: DUPLEX TRIGGER MMAP 
    Modes: IN/OUT 
      Out engine  1: 0/HD Audio play front
                     Available for use 
      Engine      2: 10/HD Audio play front (vmix)
                     Available for use 
      Engine      3: 11/HD Audio play front (vmix)
                     Available for use 
      Engine      4: 12/HD Audio play front (vmix)
                     Available for use 
      Engine      5: 13/HD Audio play front (vmix)
                     Available for use 
    Input formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Output formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Device handle: PCI009f1025-0000:00:14.2-au01
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 8
    Native sample rates (min - max): 44100 - 192000 (44100,48000,96000,192000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

HD Audio play rear                /dev/oss/oss_hdaudio0/pcm1  (device index 1)
    Legacy device /dev/dsp1
    Caps: TRIGGER MMAP 
    Modes: OUTPUT 
      Out engine  1: 1/HD Audio play rear
                     Available for use 
    Input formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Output formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Device handle: PCI009f1025-0000:00:14.2-au02
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 44100 - 192000 (44100,48000,96000,192000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

HD Audio play center/LFE          /dev/oss/oss_hdaudio0/pcm2  (device index 2)
    Legacy device /dev/dsp2
    Caps: TRIGGER MMAP 
    Modes: OUTPUT 
      Out engine  1: 2/HD Audio play center/LFE
                     Available for use 
    Input formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Output formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Device handle: PCI009f1025-0000:00:14.2-au03
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 44100 - 192000 (44100,48000,96000,192000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

HD Audio play side                /dev/oss/oss_hdaudio0/pcm3  (device index 3)
    Legacy device /dev/dsp3
    Caps: TRIGGER MMAP 
    Modes: OUTPUT 
      Out engine  1: 3/HD Audio play side
                     Available for use 
    Input formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Output formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Device handle: PCI009f1025-0000:00:14.2-au04
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 44100 - 192000 (44100,48000,96000,192000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

HD Audio play pcm4                /dev/oss/oss_hdaudio0/pcm4  (device index 4)
    Legacy device /dev/dsp4
    Caps: TRIGGER MMAP 
    Modes: OUTPUT 
      Out engine  1: 4/HD Audio play pcm4
                     Available for use 
    Input formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Output formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Device handle: PCI009f1025-0000:00:14.2-au05
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 44100 - 192000 (44100,48000,96000,192000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

HD Audio play modem-out           /dev/oss/oss_hdaudio0/pcm5  (device index 5)
    Legacy device /dev/dsp5
    Caps: TRIGGER MMAP 
    Modes: OUTPUT 
      Out engine  1: 5/HD Audio play modem-out
                     Available for use 
    Input formats (0x00000010):
      AFMT_S16_LE	- 16 bit signed little endian
    Output formats (0x00000010):
      AFMT_S16_LE	- 16 bit signed little endian
    Device handle: PCI009f1025-0000:00:14.2-au06
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 16000 - 48000 (16000,48000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

HD Audio play spdif-out           /dev/oss/oss_hdaudio0/spdout0  (device index 6)
    Legacy device /dev/dsp6
    Caps: TRIGGER MMAP 
    Modes: OUTPUT 
      Out engine  1: 6/HD Audio play spdif-out
                     Available for use 
    Input formats (0x00001410):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_AC3		- AC3 (Dolby Digital) encoded audio
      AFMT_S32_LE	- 32 bit signed little endian
    Output formats (0x00001410):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_AC3		- AC3 (Dolby Digital) encoded audio
      AFMT_S32_LE	- 32 bit signed little endian
    Device handle: PCI009f1025-0000:00:14.2-au07
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 44100 - 192000 (44100,48000,96000,192000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

HD Audio rec mix                  /dev/oss/oss_hdaudio0/pcmin0  (device index 7)
    Legacy device /dev/dsp7
    Caps: DUPLEX TRIGGER MMAP 
    Modes: IN/OUT 
      In engine   1: 7/HD Audio rec mix
                     Available for use 
      Engine      2: 10/HD Audio play front (vmix)
                     Available for use 
      Engine      3: 11/HD Audio play front (vmix)
                     Available for use 
      Engine      4: 12/HD Audio play front (vmix)
                     Available for use 
      Engine      5: 13/HD Audio play front (vmix)
                     Available for use 
    Input formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Output formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Device handle: PCI009f1025-0000:00:14.2-au08
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 44100 - 96000 (44100,48000,96000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

HD Audio rec mix                  /dev/oss/oss_hdaudio0/pcmin1  (device index 8)
    Legacy device /dev/dsp8
    Caps: TRIGGER MMAP 
    Modes: INPUT  
      In engine   1: 8/HD Audio rec mix
                     Available for use 
    Input formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Output formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Device handle: PCI009f1025-0000:00:14.2-au09
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 44100 - 96000 (44100,48000,96000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

HD Audio rec modem-out            /dev/oss/oss_hdaudio0/pcmin2  (device index 9)
    Legacy device /dev/dsp9
    Caps: TRIGGER MMAP 
    Modes: INPUT  
      In engine   1: 9/HD Audio rec modem-out
                     Available for use 
    Input formats (0x00000010):
      AFMT_S16_LE	- 16 bit signed little endian
    Output formats (0x00000010):
      AFMT_S16_LE	- 16 bit signed little endian
    Device handle: PCI009f1025-0000:00:14.2-au10
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 16000 - 48000 (16000,48000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

---

### Post by igorzwx on 2009-07-18
[http://wiki.archlinux.org/index.php/OSS#Troubleshooting_HDAudio_devices](http://wiki.archlinux.org/index.php/OSS#Troubleshooting_HDAudio_devices)
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
 [B] 
[/B]

---

### Post by eldersoares on 2009-07-19
thanks A LOT igorzwx, your help is being really useful, although i couldn't make it work yet.

what seems to happen is that oss works well in the tests but gnome and gnome applications don't recognize it, as if they were still configured to use alsa. when i open totem, i receive a message saying that gstreamer couldn't be initialized. in preferences-sound, still no option to choose, everything is blank! and it was something i did wrong when installing and uninstalling gst and rhythm from source, because before, i had many options in preferences-sound, including oss.

i'll keep trying, reading wikis and how-tos. if you have an idea, plz tell me. and thank you again!!!

---

### Post by igorzwx on 2009-07-19
I think the easiest way is to install the second Ubuntu 9.04 on the same box
and make everything clean.
The OSS4 howto on Ubuntu Documentation is designed for the standard
installation of Ubuntu 9.04.
On Ubuntu 8.04, for example, you have to compile OSS4 and blacklist
something manually.

The OSS4 problems might be better discuss on OSS4 forum as it was advised by
Ubuntu Documentation.

Best,
Igor

---

