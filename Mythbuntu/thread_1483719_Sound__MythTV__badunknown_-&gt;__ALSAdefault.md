---
title: "Sound:  MythTV  bad/unknown -&gt;  ALSA:default"
date: 2010-05-14
forum: Mythbuntu
---

### Post by winewood on 2010-05-14
Greetings!
 
I cannot get MythTV to play any sound. I have working sound in VLC media player to all 5 channels via my SPDIF that comes from my mobo hardwired. PLEASE someone help me. I can currently use MYTH to record off air TV, with 5.1 sound IN the files. Playback of video is perfect. 
I have used the frontend to assign audio to ALSA:default , ALSA:surround51 and ALSA:iec958
 
I get no apparent errors in the mythfrontend.log pertaining to audio.
 
 
***********************************************
 
Software:
Mythbuntu 10.4 64 bit.
Hardware:
BiostarT6100 : Sound AC97 using a harwired SPIDF to mobo
AMD 4200
2GB mem
NVidia 7800GT
Hauppauge 2250 - with MCE remote
 
I downloaded the newest ALSA player, drivers etc using: 
[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)
I am assuming my drivers are good, as I can play 5.1 sound in OTHER applications.
 
WHAT WORKS from my SPDIF:
---------------------------------
1. ' aplay test.ac3 '
2. ' mplayer -ao alsa:device=default -ac hwac3 test.ac3 ' all Channels..
3. VLC Media Player : 5.1 encoded hidef video : all channels
 
WHAT DOESNT:
---------------------------------
1. ' aplay -D ALSA:iec958 test.ac3 '
error: "ALSA lib pcm.c:2211:(snd_pcm_open_noupdate) **Unknown PCM ALSA:iec958**"
2. ' aplay -D ALSA:default test.ac3 '
ALSA lib pcm.c:2211:(snd_pcm_open_noupdate) **Unknown PCM ALSA:default**
3. MYTHTV sound of any kind...
 
MISSING:
---------------------------------
After reading the forums, my configurations are **MISSING** the following files:
 
"/etc/asound.conf"
"~/.asoundrc"
 
I self created a "~/.asoundrc" using:
[http://ubuntuforums.org/showthread.php?t=899139](http://ubuntuforums.org/showthread.php?t=899139)
 
Do I even need them??
 
 
```
winewood@mythtv:/opt/package/nforce$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH [Intel ICH], device 0: Intel ICH [Intel ICH]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH [Intel ICH], device 2: Intel ICH - IEC958 [Intel ICH - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
 

```
 
```
winewood@mythtv:/opt/package/nforce$ aplay -L
surround51:CARD=ICH,DEV=0
    Intel ICH, Intel ICH
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=ICH,DEV=0
    Intel ICH, Intel ICH
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=ICH,DEV=0
    Intel ICH, Intel ICH - IEC958
    IEC958 (S/PDIF) Digital Audio Output

```
 
from mythfrontend.log showing errors to surround 5.1 .. the same errors were identical to the ones when I used ALSA:Default. Replace surround51 with default to imagine what those looked like.
```
 
 
2010-05-14 20:05:23.041 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/recordings-ui.xml
2010-05-14 20:05:24.046 TV: Attempting to change from None to WatchingPreRecorded
2010-05-14 20:05:24.234 AFD: Opened codec 0x7f94356729a0, id(MPEG2VIDEO) type(Video)
2010-05-14 20:05:24.234 AFD: codec AC3 has 6 channels
2010-05-14 20:05:24.235 AFD: Opened codec 0x7f94357405b0, id(AC3) type(Audio)
2010-05-14 20:05:24.236 AFD: codec AC3 has 1 channels
2010-05-14 20:05:24.236 AFD: Opened codec 0x7f9435745260, id(AC3) type(Audio)
2010-05-14 20:05:24.328 Opening audio device 'surround51'. ch 2(6) sr 48000 (reenc 0)
2010-05-14 20:05:24.329 Opening ALSA audio device 'surround51'.
2010-05-14 20:05:24.448 Opening audio device 'surround51'. ch 2(6) sr 48000 (reenc 0)
2010-05-14 20:05:24.448 Opening ALSA audio device 'surround51'.
2010-05-14 20:05:24.582 Opening audio device 'surround51'. ch 2(2) sr 48000 (reenc 0)
2010-05-14 20:05:24.583 Opening ALSA audio device 'surround51
2010-05-14 20:05:24.735 VDPAU Error: Error at mythrender_vdpau.cpp:1448 (#1, Unknown)
2010-05-14 20:05:24.735 VDPAU Error: Failed to create VDPAU device.
2010-05-14 20:05:24.735 VDPAU Error: No VDPAU device
2010-05-14 20:05:24.735 Failed to create VDPAU render device.
2010-05-14 20:05:24.735 VidOutVDPAU Error: Failed to initialise VDPAU
2010-05-14 20:05:24.743 VideoOutputXv: Desired video renderer 'xvmc-blit' not available.
                        codec 'MPEG2' makes 'xv-blit,xshm,xlib,' available, using 'xv-blit' instead.

```

---

### Post by winewood on 2010-05-14
I have been working on this for weeks.  I just got it WORKING...
 
after I looked at what I had typed I happened up on this page...
 
[http://alsa.opensrc.org/index.php/DigitalOut#Find_your_device](http://alsa.opensrc.org/index.php/DigitalOut#Find_your_device)
 
and saw this...
 
If you want your digital output to be the default you might need to add this
 
>  
 
pcm.!default {
        type hw
        card <the card number you worked out above>
        device <the device number you worked out above>
}


---

