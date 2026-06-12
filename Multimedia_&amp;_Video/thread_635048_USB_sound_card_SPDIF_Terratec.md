---
title: "USB sound card SPDIF Terratec"
date: 2007-12-08
forum: Multimedia &amp; Video
---

### Post by gombihu on 2007-12-08
Hello,

I'm using Ubuntu for 3 months on a notebook and I get bored with the integrated sound card, so I bought a Terratec 5.1 USB MKII in order to get digital S-PDIF output and watch the movies in Dolby sound. 
I have already spent 2 days](*,) with google finding a solution but no use :( The amplifier never changed its state from Stereo to Dolby. I also have a desktop PC with Nvidia3 chipset and its S-PDIF (optical) output works fine. 

I was not able to pass AC3 trough SPDIF with mplayer:
$ mplayer -vo gl2 dolbyrain.vob -ao alsa:device=hw=1 -ac hwac3
..
[AO_ALSA] alsa-lib: pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM hw:1,AES0=6
..

I would really appreciate some help!:confused:
gombihu

Here are some logs: 

[FONT="System"]

[B]$ cat /proc/asound/cards
[/B]
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfe020000 irq 21
 1 [Audio          ]: USB-Audio - USB Audio
                      USB Audio at usb-0000:00:1d.0-1, full speed


**$cat /proc/asound/card1/pcm0p/info **

card: 1
device: 0
subdevice: 0
stream: PLAYBACK
id: USB Audio
name: USB Audio
subname: subdevice #0
class: 0
subclass: 0
subdevices_count: 1
subdevices_avail: 1

**$aplay -L**

front:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
front:CARD=Audio,DEV=0
    USB Audio, USB Audio
    Front speakers
surround40:CARD=Audio,DEV=0
    USB Audio, USB Audio
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Audio,DEV=0
    USB Audio, USB Audio
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Audio,DEV=0
    USB Audio, USB Audio
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Audio,DEV=0
    USB Audio, USB Audio
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Audio,DEV=0
    USB Audio, USB Audio
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Audio,DEV=0
    USB Audio, USB Audio
    IEC958 (S/PDIF) Digital Audio Output


**$ mplayer -vo gl2 dolbyrain.vob -ao alsa:device=hw=1 -ac hwac3**

Forced audio codec: hwac3
Opening audio decoder: [hwac3] AC3/DTS pass-through S/PDIF
No accelerated IMDCT transform found
hwac3: switched to AC3, 448000 bps, 48000 Hz
AUDIO: 48000 Hz, 2 ch, ac3, 448.0 kbit/29.17% (ratio: 56000->192000)
Selected audio codec: [hwac3] afm: hwac3 (AC3 through S/PDIF)
==========================================================================
[AO_ALSA] alsa-lib: conf.c:3840:(parse_args) Unknown parameter AES0
[AO_ALSA] alsa-lib: conf.c:3966:(snd_config_expand) Parse arguments error: No such file or directory
[AO_ALSA] alsa-lib: pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM hw:1,AES0=6
AO: [alsa] 48000Hz 2ch ac3 (1 bytes per sample)
Starting playback...

[/FONT]

---

### Post by gombihu on 2007-12-20
Nobody has any clue? :(

---

