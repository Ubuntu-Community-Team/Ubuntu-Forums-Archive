---
title: "USB soundcard no sound from Alsa (hw)"
date: 2015-06-04
forum: Multimedia Software
---

### Post by klasw on 2015-06-04
Hello!

I bought a new USB external sound card; Taga Harmony [COLOR=#333745][FONT=Helvetica]DA-300.

SPDIF IN (coaxial and optical):
[FONT=inherit]24bit 192kHz (Coaxial, Optical)[/FONT]
[FONT=inherit]TI Burr-Brown Audio PCM2704 chip[/FONT]
[FONT=inherit] 
USB IN:[/FONT]
[FONT=inherit]16bit 48kHz (USB) [FONT=inherit]CirrusLogic CS8416 chip[/FONT][/FONT]

----------
Its function, I tested it on a  Macbook air (excuse me if I swear).

I am only using ALSA,  (for Kodi configuration)!
-----------

I can not get the usb interface to function directly. A bit novice on this.

I got it though  to play sound by  this command:

aplay -D plughw:2,1 /usr/share/sounds/alsa/Noise.wav

and this:

aplay -D plughw:2,2 /usr/share/sounds/alsa/Noise.wav

but this will not function:

aplay -D hw:2,1 /usr/share/sounds/alsa/Noise.wav

aplay -D hw:2,2 /usr/share/sounds/alsa/Noise.wav


(
and not this either:

aplay -D hw:2,0 /usr/share/sounds/alsa/Noise.wav
)

Conclusion,  looks like it havet two  PCM, and a SPDIF also. Not shure if SPDIF is only in, for recording.

How can I get this card t function? Can I add plughw some were?

OUTPUTS:
-------------

(kort = card)

(enhet = device)
-----------


cat /proc/asound/cards  

.
.

 2 [Audio]: USB-Audio - USB2.0 High-Speed True HD Audio

    CMEDIA USB2.0 High-Speed True HD Audio at usb-0000:00:1d.7-4, high speed
..


arecord -l | grep USB

.
.


kort 2: Audio [**USB**2.0 High-Speed True HD Audio], enhet 0: **USB** Audio [**USB** Audio]
kort 2: Audio [**USB**2.0 High-Speed True HD Audio], enhet 1: **USB** Audio [**USB** Audio #1]
kort 2: Audio [**USB**2.0 High-Speed True HD Audio], enhet 3: **USB** Audio [**USB** Audio #3]
...


aplay -l


.
.
kort 2: Audio [USB2.0 High-Speed True HD Audio], enhet 0: USB Audio [USB Audio]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: subdevice #0
kort 2: Audio [USB2.0 High-Speed True HD Audio], enhet 1: USB Audio [USB Audio #1]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: subdevice #0
kort 2: Audio [USB2.0 High-Speed True HD Audio], enhet 2: USB Audio [USB Audio #2]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: subdevice #0
kort 2: Audio [USB2.0 High-Speed True HD Audio], enhet 3: USB Audio [USB Audio #3]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: subdevice #0
..


find /lib/modules/`uname -r` | grep snd
.
.
/lib/modules/3.13.0-53-generic/kernel/sound/usb/**snd**-usb-audio.ko
..
(module is there)


alsamixer -c 2

[ATTACH=CONFIG]262431[/ATTACH]

EDIT

Output from [/FONT][/COLOR]dmesg:[COLOR=#333745][FONT=Helvetica]


[/FONT][/COLOR]ALSA/HDA dmesg                                                           
**&#9474;** !!--------------                                                           
**&#9474;**                                                                            
**&#9474;** [    1.921270] [drm] Connector 1:                                          
**&#9474;** [    1.921272] [drm]   HDMI-A-1                                           
**&#9474;** [    1.921274] [drm]   HPD1                                               
**&#9474;** --                                                                        
**&#9474;** [    8.492456] REISERFS (device sdh1): Using r5 hash to sort names         
**&#9474;** [    8.670426] snd_hda_core: module verification failed: signature and/or  
**&#9474;** [    8.681434] usb-audio:4: clock source 23 is not valid, cannot use       
**&#9474;** [    8.685430] usb-audio:4: clock source 23 is not valid, cannot use  
[COLOR=#333745][FONT=Helvetica]

?

Grateful for any help!

Klas


[/FONT][/COLOR]

---

### Post by klasw on 2015-06-05
Got som progress on this, got sound out from hw by adding this in my .asoundrc:

cm.!default {
        type plug
        slave {
         pcm "hw:0,1"
        }
}


ctl.!default {
        type hw
        card 0
}

and changing in:  /etc/modprobe.d/alsa-base.conf

options snd-usb-audio index=-2

..to:

options snd-usb-audio index=0

So know I can get sound out by:


aplay  /usr/share/sounds/alsa/Noise.wav

and the device comes up in Kodi as default, but still no sound out from Kodi, but I can play sound by mplayer (mplayer /usr/share/sounds/alsa/Noise.wav ).

---

### Post by klasw on 2015-06-06
Got it to function now, in Kodi also, with some simple basic settings in .asoundrc. Only this:

defaults.pcm.!card Audio
defaults.pcm.!device 1

( default:CARD=Audio from aplay -L)

I also installed phonon-backend-vlc, and move up default in multimedia gui in KDE. Do not know if that made any difference.

The funny thing is that when a had above configuration (in my second replay here) , I got better output from, mplayer:

mplayer /media/multimedia/music/Pink\ Floyd\ -\ The\ Dark\ Side\ Of\ The\ Moon\ \(2011\)\ \{FLAC\}\ \[Blu-Ray\ 24-96\ Stereo\]\04.Time.flac


AUDIO: 96000 Hz, 2 ch, s32le, 2834.0 kbit/46.13% (ratio: 354244->768000)
Selected audio codec: [ffflac] afm: ffmpeg (FFmpeg FLAC audio) 


AO: [alsa] 96000Hz 2ch s32le (4 bytes per sample)

Now I only got this:


AO: [alsa] 48000Hz 2ch s32le (4 bytes per sample)


I doubt I can hear any difference, but its funny the usb take the higher sampling rate.  If I try to put it out by raw format (aplay) it did ot function, only got noise.


From cat /proc/asound/card0/stream1


Playback:
  Status: Stop
  Interface 2
    Altset 1
    Format: S16_LE
    Channels: 2
    Endpoint: 6 OUT (ASYNC)
    Rates: 44100, 48000, 88200, 96000, 176400, 192000
    Data packet interval: 125 us
  Interface 2
    Altset 2
    Format: S24_3LE
    Channels: 2
    Endpoint: 6 OUT (ASYNC)
    Rates: 44100, 48000, 88200, 96000, 176400, 192000
    Data packet interval: 125 us


Capture:
  Status: Stop
  Interface 5
    Altset 1
    Format: S16_LE
    Channels: 2
    Endpoint: 8 IN (ASYNC)
    Rates: 44100, 48000, 88200, 96000, 176400, 192000
    Data packet interval: 125 us
  Interface 5
    Altset 2
    Format: S24_3LE
    Channels: 2
    Endpoint: 8 IN (ASYNC)
    Rates: 44100, 48000, 88200, 96000, 176400, 192000
    Data packet interval: 125 us

From cat /proc/asound/card0/stream2


Playback:
  Status: Running
    Interface = 2
    Altset = 3
    Packet Size = 33
    Momentary freq = 48000 Hz (0x6.0000)
    Feedback Format = 16.16
  Interface 2
    Altset 3
    Format: S16_LE
    Channels: 2
    Endpoint: 6 OUT (ASYNC)
    Rates: 44100, 48000, 88200, 96000, 176400, 192000
    Data packet interval: 125 us

---
The case is closed, as I got a my solution, but any comment is interesting on this, I think.

---

