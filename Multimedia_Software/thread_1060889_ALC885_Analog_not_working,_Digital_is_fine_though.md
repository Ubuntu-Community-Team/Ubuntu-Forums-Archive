---
title: "ALC885 Analog not working, Digital is fine though"
date: 2009-02-05
forum: Multimedia Software
---

### Post by perelin on 2009-02-05
Hi everybody,
it seems I have a bit of an ALSA Problem:

I use PulseAudio and pavucontrol to direct my audio streams between headphone (ALSA PCM on front:0,1 (ALC885 Analog) via DMA) and Stereo (SPDIF/ ALSA PCM on front:0,1 (ALC885 Digital) via DMA) output. Everything in my System->Preferences->Sound->Devices tab ist set to "PulseAudio Sound Server". 

A few days ago the VLC (VideoLanClient Video Player) audio stream was not shown anymore in the pavucontrol->Playback tab and I couldn't switch the stream to my stereo (digital out) like I usually do. I thought maybe a hick up, restart will fix it and used Totem for a while. When I saw the same thing is going on with browser audio (ie Flash streams) I got curious. I noticed that not even the headphones (analog out) receive any signal. It seems most applications can only use the digital out. The rest don't use any output channel at all. Analog channels are filled with a very loud (I can even hear it at zero volume) and very high screechy noise. The noise starts at bootup with the ALSA drivers and ends at shutdown with the ALSA drivers. Must be ALSA related... ;-) **Hardware failure is not an option since I tested the analog channels on a dual booted vista installation.**

I tried some stuff like purging and reinstalling the ALSA drivers and changing sound sources in System->Preferences->Sound->Devices. Reinstalling ALSA wasn't any good. Changing audio sources at least yielded an error message: when I set any source to "HDA Intel ALC885 Analog (ALSA)" i get:

```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.
```

"HDA Intel ALC885 Digital (ALSA)" works fine in all cases.

aplay -l yields:

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC885 Analog [ALC885 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC885 Digital [ALC885 Digital]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```

I have no idea what to do/try next. Any suggestions would be appreciated!

---

### Post by markbuntu on 2009-02-05
In a terminal close all your sound using applications and stop pulseaudio

killall pulseaudio

Then start it again with

pulseaudio -vvv

and start up some applications and see what messages you get. the -vvv option will give verbose output of all the pulseaudio messages. This will help you to find out what is going on.

---

### Post by perelin on 2009-02-07
thx for the reply markbuntu!

Btw: I eliminated the high pitched noise by muting my mic channels in volume control (HDA Intel (Alsa mixer)).

The main problem still stands: neither VLC nor Firefox audio streams are recognized by Pulseaudio.

Like you suggested I killed pulseaudio deamon and restarted it with the debuger option. The startup output is in the pulseaudio_vvv_output_20090207_1241.txt attachment.
When I open a application recognized by PA output looks like this:
```
I: client.c: Created 1 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: protocol-native.c: Enabled SHM for new connection
I: client.c: Client 1 changed name from "Native client (UNIX socket client)" to "amarokapp"
```
Hence everything is fine, audio stream is recognized by PA and shown in pavucontrol "Playback" tab so I can switch between analog and digitla output channel.
When I try to open flash audio (in Firefox) or VLC and start playback output looks like this:
```
I: client.c: Created 2 "Native client (UNIX socket client)"
I: client.c: Freed 2 "Native client (UNIX socket client)"
I: protocol-native.c: connection died.
```
Still stuck.

---

### Post by perelin on 2009-02-08
So I finally fixed my issues. Here is a quick explanation.

VLC:
VLC was not shown in pavucontrol because vlc-plugin-pulse was not installed. Installing the package and switching audio output to pulseaudio in vlc preferences resolved this.

Flash:
Since I use flash player 10 which has native support for pulseaudio I had to uninstall libflashsupport and flashplugin-nonfree-extrasound. That done everything worked smoothly

This thread is helpful with pulseaudio issues: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

cu!

---

