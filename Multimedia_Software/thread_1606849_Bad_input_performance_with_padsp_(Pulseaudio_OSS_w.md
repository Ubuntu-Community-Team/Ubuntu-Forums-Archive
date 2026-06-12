---
title: "Bad input performance with padsp (Pulseaudio OSS wrapper)"
date: 2010-10-27
forum: Multimedia Software
---

### Post by ThatBum on 2010-10-27
Hello world. I stumbled across [Qtel]("http://sourceforge.net/apps/trac/svxlink/") recently, which is a Qt-based straightforward, no-frills EchoLink client (for ham radio, Internet linked repeaters and such) that uses OSS for input/output for transmitting/receiving. It's a part of SvxLink, the server side, and shares some libraries and stuff. The program itself works perfect, but the sound input does not.

See, the machine has Maverick on it, which does not have OSS (or low-level OSS, at least, it doesn't have /dev/dsp, /dev/mixer, etc). I found I could use padsp to fix this. padsp is some sort of OSS emulator, and it just forwards the OSS output to Pulseaudio, so legacy OSS apps can still work. When I am receiving, it works very well; it's free of distortion and can the volume can be adjusted by the indicator applet volume thing. When I transmit, however, it's barely functional. It seems to let out a 1/4 second burst of loud, distorted sound every 2 seconds or so.

I know it's using the mic as input, because If I tap it, it does increase in volume. I don't think it has to do with Qtel particularly, because padsp does this to something as basic as running a script with 'cat /dev/dsp | aplay' in it.

This is the debug output while transmitting to a test server.

```
justyn@NetbookOfAwesomeness:~$ padsp -d qtel 
utils/padsp.c: dsp_open()
utils/padsp.c: fd_info_new()
utils/padsp.c: dsp_open() succeeded, fd=9
utils/padsp.c: SNDCTL_DSP_SETDUPLEX
utils/padsp.c: SNDCTL_DSP_CAPS
utils/padsp.c: SNDCTL_DSP_SETFRAGMENT: 0x0002000a
utils/padsp.c: SNDCTL_DSP_SETFMT: 16
utils/padsp.c: SNDCTL_DSP_CHANNELS: 1
utils/padsp.c: SNDCTL_DSP_SPEED: 8000
utils/padsp.c: ss: s16le 1ch 8000Hz
utils/padsp.c: SNDCTL_DSP_GETBLKSIZE
utils/padsp.c: freeing fd info (fd=9)
utils/padsp.c: Draining.
utils/padsp.c: dsp_open()
utils/padsp.c: fd_info_new()
utils/padsp.c: dsp_open() succeeded, fd=11
utils/padsp.c: SNDCTL_DSP_SETDUPLEX
utils/padsp.c: SNDCTL_DSP_CAPS
utils/padsp.c: SNDCTL_DSP_SETFRAGMENT: 0x0002000a
utils/padsp.c: SNDCTL_DSP_SETFMT: 16
utils/padsp.c: SNDCTL_DSP_CHANNELS: 1
utils/padsp.c: SNDCTL_DSP_SPEED: 8000
utils/padsp.c: ss: s16le 1ch 8000Hz
utils/padsp.c: SNDCTL_DSP_GETBLKSIZE
utils/padsp.c: stream established.
utils/padsp.c: SNDCTL_DSP_GETOSPACE
<This is the server's audio greeting.>
utils/padsp.c: fragsize=1024, fragstotal=2, bytes=2048, fragments=2
utils/padsp.c: SNDCTL_DSP_GETISPACE
utils/padsp.c: fragsize=1024, fragstotal=2, bytes=1024, fragments=1
utils/padsp.c: SNDCTL_DSP_GETISPACE
utils/padsp.c: fragsize=1024, fragstotal=2, bytes=1024, fragments=1
utils/padsp.c: SNDCTL_DSP_GETISPACE
utils/padsp.c: fragsize=1024, fragstotal=2, bytes=1062, fragments=1
utils/padsp.c: SNDCTL_DSP_GETISPACE
utils/padsp.c: fragsize=1024, fragstotal=2, bytes=4256, fragments=4
utils/padsp.c: SNDCTL_DSP_GETISPACE
utils/padsp.c: fragsize=1024, fragstotal=2, bytes=2056, fragments=2
utils/padsp.c: SNDCTL_DSP_GETOSPACE
utils/padsp.c: fragsize=1024, fragstotal=2, bytes=2048, fragments=2
utils/padsp.c: SNDCTL_DSP_GETOSPACE
utils/padsp.c: pa_stream_writable_size(): Bad state
utils/padsp.c: fragsize=1024, fragstotal=2, bytes=-2049, fragments=-2
utils/padsp.c: stream established.
utils/padsp.c: SNDCTL_DSP_GETOSPACE
utils/padsp.c: fragsize=1024, fragstotal=2, bytes=1024, fragments=1
utils/padsp.c: SNDCTL_DSP_GETOSPACE
utils/padsp.c: fragsize=1024, fragstotal=2, bytes=0, fragments=0
utils/padsp.c: SNDCTL_DSP_GETOSPACE
utils/padsp.c: fragsize=1024, fragstotal=2, bytes=0, fragments=0
utils/padsp.c: SNDCTL_DSP_GETOSPACE
utils/padsp.c: fragsize=1024, fragstotal=2, bytes=0, fragments=0
utils/padsp.c: SNDCTL_DSP_GETOSPACE
utils/padsp.c: fragsize=1024, fragstotal=2, bytes=0, fragments=0
utils/padsp.c: SNDCTL_DSP_GETOSPACE
utils/padsp.c: fragsize=1024, fragstotal=2, bytes=0, fragments=0
utils/padsp.c: SNDCTL_DSP_GETOSPACE
utils/padsp.c: fragsize=1024, fragstotal=2, bytes=0, fragments=0
utils/padsp.c: SNDCTL_DSP_GETOSPACE
utils/padsp.c: fragsize=1024, fragstotal=2, bytes=0, fragments=0
utils/padsp.c: SNDCTL_DSP_GETOSPACE
utils/padsp.c: fragsize=1024, fragstotal=2, bytes=0, fragments=0
utils/padsp.c: SNDCTL_DSP_GETOSPACE
<SNIP>
utils/padsp.c: SNDCTL_DSP_GETOSPACE
utils/padsp.c: fragsize=1024, fragstotal=2, bytes=888, fragments=0
utils/padsp.c: SNDCTL_DSP_GETOSPACE
utils/padsp.c: fragsize=1024, fragstotal=2, bytes=888, fragments=0
utils/padsp.c: SNDCTL_DSP_GETOSPACE
utils/padsp.c: fragsize=1024, fragstotal=2, bytes=888, fragments=0
utils/padsp.c: SNDCTL_DSP_GETOSPACE
utils/padsp.c: fragsize=1024, fragstotal=2, bytes=888, fragments=0
utils/padsp.c: SNDCTL_DSP_GETOSPACE
utils/padsp.c: fragsize=1024, fragstotal=2, bytes=888, fragments=0
utils/padsp.c: SNDCTL_DSP_GETOSPACE
utils/padsp.c: fragsize=1024, fragstotal=2, bytes=888, fragments=0
utils/padsp.c: SNDCTL_DSP_GETOSPACE
utils/padsp.c: fragsize=1024, fragstotal=2, bytes=888, fragments=0
utils/padsp.c: SNDCTL_DSP_GETOSPACE
utils/padsp.c: fragsize=1024, fragstotal=2, bytes=888, fragments=0
utils/padsp.c: SNDCTL_DSP_GETOSPACE
<I Start transmitting here, and say "KI6USU test test." It should be much longer,
the fragments might have to do with it.>
utils/padsp.c: fragsize=1024, fragstotal=2, bytes=2182, fragments=2
utils/padsp.c: SNDCTL_DSP_GETOSPACE
utils/padsp.c: fragsize=1024, fragstotal=2, bytes=3072, fragments=3
utils/padsp.c: SNDCTL_DSP_GETOSPACE
utils/padsp.c: fragsize=1024, fragstotal=2, bytes=3072, fragments=3
utils/padsp.c: SNDCTL_DSP_GETOSPACE
utils/padsp.c: fragsize=1024, fragstotal=2, bytes=2048, fragments=2
utils/padsp.c: SNDCTL_DSP_GETISPACE
utils/padsp.c: fragsize=1024, fragstotal=2, bytes=4602, fragments=4
utils/padsp.c: SNDCTL_DSP_GETISPACE
utils/padsp.c: fragsize=1024, fragstotal=2, bytes=2148, fragments=2
utils/padsp.c: SNDCTL_DSP_GETISPACE
utils/padsp.c: fragsize=1024, fragstotal=2, bytes=3200, fragments=3
utils/padsp.c: SNDCTL_DSP_GETISPACE
utils/padsp.c: fragsize=1024, fragstotal=2, bytes=2084, fragments=2
utils/padsp.c: SNDCTL_DSP_GETISPACE
utils/padsp.c: fragsize=1024, fragstotal=2, bytes=1154, fragments=1
utils/padsp.c: SNDCTL_DSP_GETISPACE
utils/padsp.c: fragsize=1024, fragstotal=2, bytes=4602, fragments=4
utils/padsp.c: SNDCTL_DSP_GETISPACE
utils/padsp.c: fragsize=1024, fragstotal=2, bytes=2056, fragments=2
utils/padsp.c: SNDCTL_DSP_GETISPACE
utils/padsp.c: fragsize=1024, fragstotal=2, bytes=3108, fragments=3
utils/padsp.c: SNDCTL_DSP_GETISPACE
utils/padsp.c: fragsize=1024, fragstotal=2, bytes=2530, fragments=2
utils/padsp.c: SNDCTL_DSP_GETOSPACE
utils/padsp.c: fragsize=1024, fragstotal=2, bytes=3072, fragments=3
utils/padsp.c: SNDCTL_DSP_GETOSPACE
utils/padsp.c: fragsize=1024, fragstotal=2, bytes=1024, fragments=1
utils/padsp.c: SNDCTL_DSP_GETOSPACE
utils/padsp.c: fragsize=1024, fragstotal=2, bytes=3072, fragments=3
utils/padsp.c: SNDCTL_DSP_GETOSPACE
utils/padsp.c: fragsize=1024, fragstotal=2, bytes=3072, fragments=3
utils/padsp.c: SNDCTL_DSP_GETOSPACE
utils/padsp.c: fragsize=1024, fragstotal=2, bytes=2048, fragments=2
utils/padsp.c: SNDCTL_DSP_GETISPACE
utils/padsp.c: fragsize=1024, fragstotal=2, bytes=4606, fragments=4
utils/padsp.c: SNDCTL_DSP_GETISPACE
utils/padsp.c: fragsize=1024, fragstotal=2, bytes=2056, fragments=2
utils/padsp.c: freeing fd info (fd=11)
utils/padsp.c: Draining.
utils/padsp.c: Really draining.
```I would really like this client to work, because it looks really promising...I tried alsa-oss, but using aoss had no audio at all, in or out. I tried installing actual OSS, but that borked my audio and I had to reinstall. Some help please?

Not sure if this is the right place to put it, but it's audio/Pulse related, so...

EDIT: I tried osspd, that didn't work. it made a /dev/dsp, but I get 'open failed: Permission denied' as normal user and 'open failed: Input/output error' as root when trying an OSS program.

---

### Post by ThatBum on 2010-10-29
Bump.

Any hams out there know of a more recent EchoLink client that uses Pulseaudio/ALSA? And don't say EchoLinux, that's even more confusing than Qtel.

EDIT: I tried Qtel/osspd on my Lucid box, and it worked. So it's either something with Maverick, or something with my netbook's hardware. Meh.

[COLOR=Red]E2: I think I figured it out...osspd still isn't working, but I got padsp going. It was conflicting with psyke83's Pulseaudio Equalizer thingie. pdasp doesn't like LADSPA, apparently. I have to disable it before I use padsp. But it works! I'm talking on VAN-IRLP now.[/COLOR]

(I found out this isn't true)

I just realized, I have a habit of answering my own posts...I have to stop. Maybe this information will be useful.

---

### Post by ThatBum on 2010-10-29
Nope, it still doesn't quite work...it only works when I have some kind of peak monitoring program open, of all things. A peak monitoring program being System-Preferences-Sound (gnome-volume-control) or Applications-Sound and Video-PulseAudio Volume Control (pavucontrol). As soon as I close it, it goes back to the same old behavior of barely updating at all.

I attached a screenshot of Qtel and gnome-volume-control running together. I would make another edit, but I couldn't attach something in an edit.

E: I figured out it can be any program that accesses the microphone that sets it working. It works with Sound Recorder, and even arecord.

E2: I compiled the trunk source of Qtel. This uses ALSA instead of OSS, so this problem is effectively solved now. I figured out a workaround kludge thing when I had the SourceForge OSS-using version. I renamed the qtel binary qtel-bin, made a script named qtel, and put in /usr/bin with the executable bit turned on:

```
#!/bin/bash
# Kinda-sorta PulseAudio compatibility
arecord -r 96000 -D pulse -c 1 > /dev/null 2>&1 &
padsp qtel-bin
killall arecord
```

Now I have an unrelated problem with my microphone that I need another thread for.

---

