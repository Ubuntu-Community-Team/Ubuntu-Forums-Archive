---
title: "USB Sound Card Issue"
date: 2009-01-21
forum: Multimedia Software
---

### Post by dysonsphere23 on 2009-01-21
Hello,

I have a Dell laptop with a broken audio out port, so can't get sound through speakers or headphones.  As a work-around I purchased a USB audio adapter.

It works, but only on one channel, the left.  Both stereo channels go through the left so there is no loss of sound.

I have set the usb card to be the default in pulseaudio and can see the sound in both channels in the volume meter.  When I start pulseaudio in the terminal it gives the following messages:

W: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:1
W: alsa-util.c: Cannot find fallback mixer control "PCM".
W: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.

Funny thing is that it worked randomly one day while I was playing Spore in WINE,  and once while playing a dvd in vlc.  But I haven't been able to reproduce that.

The USB card is a virtual 7.1. with the following specs:

The USB Vitrual 7.1CH Sound Card is highly flexible audio interface which can be used either with Desktop or Notebook systems. Bundled with Xear 3D Sound simulation software, it turns your stereo speaker or earphones into 7.1 channel environment. No drivers required, just plug and play or instant audio playback, also compatible with all major operation systems.

1. USB 2.0 Full-Speed (12Mbps), USB audio device compliant
2. USB Bus powered, no external power needed
3. Connectors: USB Type-A, Stereo output jack,Microphone-input jack
4. Functional keys: Microphone-Mute Status, Volume up/Volume down control
5. Red & green status indicator lights
6. Mute control
7. Include Xear 3D, the virtual 7.1 channel sound simulation software for Windows XP/Vista
8. Driver not required for Windows 98SE/ME/2000/XP/Vista, Linux, Mas OS
9. Excellent Chipset: CM119 of C-Media
10. Light weight: 15g
11. Slim size: 58x25x13mm


sudo asoundconf list gives:

Names of available sound cards:
ICH6
default

aplay -L gives:

front:CARD=ICH6,DEV=0
    Intel ICH6, Intel ICH6
    Front speakers
surround40:CARD=ICH6,DEV=0
    Intel ICH6, Intel ICH6
    4.0 Surround output to Front and Rear speakers
surround41:CARD=ICH6,DEV=0
    Intel ICH6, Intel ICH6
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=ICH6,DEV=0
    Intel ICH6, Intel ICH6
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=ICH6,DEV=0
    Intel ICH6, Intel ICH6
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
null
    Discard all samples (playback) or generate zero samples (capture)
front:CARD=default,DEV=0
    C-Media USB Audio Device   , USB Audio
    Front speakers
surround40:CARD=default,DEV=0
    C-Media USB Audio Device   , USB Audio
    4.0 Surround output to Front and Rear speakers
surround41:CARD=default,DEV=0
    C-Media USB Audio Device   , USB Audio
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=default,DEV=0
    C-Media USB Audio Device   , USB Audio
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=default,DEV=0
    C-Media USB Audio Device   , USB Audio
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=default,DEV=0
    C-Media USB Audio Device   , USB Audio
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=default,DEV=0
    C-Media USB Audio Device   , USB Audio
    IEC958 (S/PDIF) Digital Audio Output


I am running Ubuntu 8.04.

Thanks

---

