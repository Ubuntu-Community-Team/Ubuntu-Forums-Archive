---
title: "Command line recording of a stereo input"
date: 2013-05-03
forum: Multimedia Software
---

### Post by MakOwner on 2013-05-03
I'm not sure if this should go here or in the Sudio forum, so If I have this in the wrong place, can some one please slap me on the wrist and move it?


I know very little about sound recording and the general theroy behind Analog to Digital sound conversion and all that good stuff.  Most of it is way over my head - I get losat just reading the man page for arecord and lame.
But -- I am recording a local over-the-air FM signal that is broadcast in stereo.  
I am doing this on relatively old hardware so I run from a minimal install and only install the stuff I really need to make the thing work -- including no graphical interface at all, as the system is headless and has less video memory than I care to admit.

I am using an ASUS sound card that shows up as this in lspci
```

02:04.0 Multimedia audio controller: C-Media Electronics Inc CMI8788 [Oxygen HD Audio]
	Subsystem: ASUSTeK Computer Inc. Virtuoso 100 (Xonar DX)
	Flags: bus master, medium devsel, latency 32, IRQ 16
	I/O ports at ec00 [size=256]
	Capabilities: [c0] Power Management version 2
	Kernel driver in use: snd_virtuoso
	Kernel modules: snd-virtuoso

```

I am using alsamixer to adjust the input device to either mic jack or the line-in device (which are both the same jack/interface on the card).
I have a [Rolls HR78]("http://www.rolls.com/product.php?pid=hr78") AM/FM digital tuner using the Red/White RCA jack outputs to a 3.55 stereo plug converter connected to the line in/mic jack on the sound card.
I have the option to connect directly to a "headphone out" 3.5 mm jack on the back of the unit too.
I use arecord to record in cd format to a wav file:
arecord -f cd -t wav -d $SECONDS $NAME.wav
arecord has the annoying habit of splitting to a second file when you get cloase to 2GB, so if more than one file is produced, I concatenate them using sox.
I then use lame to conver to an mp3 file to reduce size and listen to them on a phone.

I'm having issues somewhere in all of this with getting the audio levels correct and ensuring that I am capturing the stereo separation in the broadcast.

Would recroding from the PCM device rather than the the line in or mic jack give cleaner source sound, given this hardware?
How would one set the PCM device as the inpout device on this hardware?
Is there a (layman's terms) guide somewhere to help me determine the apprpriate levels to use to aquire the optimal sound and stereo recording without either requiring a PhD in math or 6 months of trial and error?
I have been doing a fair amount of that already.

My previous generation of hardware was an even older bit of server hardware with an Ensoniq 32 bit PCI sound card.  I recorded from a table top radio there -- and had recurring issues with signal drift from the FM station - thus the Rolls HR78.

I find a fair amount of information about this on the web, however almost _everything_ assumes you are doing things in a GUI interface.  Not at all possible for me.

---

### Post by ibjsb4 on 2013-05-03
Just want something quick and dirty :)

One moment please, can't get it to post

#!/bin/bash
# Copyright 2008-2009, Kees Cook <kees@outflux.net>
#
# Records the PulseAudio monitor channel.
# [http://www.outflux.net/blog/archives/2009/04/19/recording-from-pulseaudio/](http://www.outflux.net/blog/archives/2009/04/19/recording-from-pulseaudio/)
#
#This script require sox
#sudo apt-get install sox

if [ -n "$1" ]; then
    OUTFILE="$1"
else
    TIME=$(date +%d-%b-%y_%H%M-%Z)
    OUTFILE="recording_$TIME.wav"
fi

# Get sink monitor:
MONITOR=$(pactl list | grep -A2 '^Source #' | grep 'Name: .*\.monitor$' | awk '{print $NF}' | tail -n1)

# Record it raw, and convert to a wav
echo "Recording. Ctrl-C or close window to stop"
parec -d "$MONITOR" | sox -t raw -r 44100 -sLb 16 -c 2 - "$OUTFILE"

# End of sound_cap.sh

---

### Post by tgalati4 on 2013-05-03
The 2GB limit is probably related to running 32-bit version of linux, which I assume since you are running old hardware.  PCM might get you cleaner signal, but you still need a graphical level indicator to see your gain levels so you can adjust them right before recording.  Otherwise, you would need to use compression (which sox can do) to control the wild level swings.

Searching the repos:

tgalati4@Mint14-Extensa ~ $ apt-cache search alsa meter
ams - Realtime modular synthesizer for ALSA
librtaudio4 - C++ library for realtime audio input/ouput
mudita24 - ALSA GUI control tool for Envy24 (ice1712) soundcards
qarecord - audio recording tool

Not much to work with.  I don't know if there is a simple mixer/meter for the terminal.  Sox may have a display with a switch.  You can also use some leveling:

       --norm[=dB-level]
              Automatically invoke the gain effect to guard against clipping and to normalise the audio. E.g.
                 sox --norm infile -b 16 outfile rate 44100 dither -s

You will have to do extensive testing since you have unique hardware.  I presume that the radio station doesn't have a website stream?  That would be easier to record.

---

### Post by MakOwner on 2013-05-03
> **ibjsb4 said:**
> Just want something quick and dirty :)

One moment please, can't get it to post

#!/bin/bash
# Copyright 2008-2009, Kees Cook <kees@outflux.net>
#
# Records the PulseAudio monitor channel.
# [http://www.outflux.net/blog/archives/2009/04/19/recording-from-pulseaudio/](http://www.outflux.net/blog/archives/2009/04/19/recording-from-pulseaudio/)
#
#This script require sox
#sudo apt-get install sox

if [ -n "$1" ]; then
    OUTFILE="$1"
else
    TIME=$(date +%d-%b-%y_%H%M-%Z)
    OUTFILE="recording_$TIME.wav"
fi

# Get sink monitor:
MONITOR=$(pactl list | grep -A2 '^Source #' | grep 'Name: .*\.monitor$' | awk '{print $NF}' | tail -n1)

# Record it raw, and convert to a wav
echo "Recording. Ctrl-C or close window to stop"
parec -d "$MONITOR" | sox -t raw -r 44100 -sLb 16 -c 2 - "$OUTFILE"

# End of sound_cap.sh

Looks like 'pactl' is a pulseaudio utility -- pactl isn't installed.  I'm using alsa because it has  been the easiest to get functioning.  
Getting the sound card to function these days without a GUI has been another fun exercise in itself...

---

### Post by MakOwner on 2013-05-03
> **tgalati4 said:**
> The 2GB limit is probably related to running 32-bit version of linux, which I assume since you are running old hardware.  PCM might get you cleaner signal, but you still need a graphical level indicator to see your gain levels so you can adjust them right before recording.  Otherwise, you would need to use compression (which sox can do) to control the wild level swings.

Searching the repos:

tgalati4@Mint14-Extensa ~ $ apt-cache search alsa meter
ams - Realtime modular synthesizer for ALSA
librtaudio4 - C++ library for realtime audio input/ouput
mudita24 - ALSA GUI control tool for Envy24 (ice1712) soundcards
qarecord - audio recording tool

Not much to work with.  I don't know if there is a simple mixer/meter for the terminal.  Sox may have a display with a switch.  You can also use some leveling:

       --norm[=dB-level]
              Automatically invoke the gain effect to guard against clipping and to normalise the audio. E.g.
                 sox --norm infile -b 16 outfile rate 44100 dither -s

You will have to do extensive testing since you have unique hardware.  I presume that the radio station doesn't have a website stream?  That would be easier to record.

I'm on 64 bit 12.04 LTS and arecord still spins off a new file at 2GB.  I had toyed with just recording in raw format and use cat to append the additional files ot the first, but sox seems to be just as fast and with wav files the header contaiins all the critical information abotu the recording variables to be used by lame.  That's the least of my worries at this point.

I tried the website stream and it drops way to frequently and aborts the recording; and what they push online is thier 'second channel' apparently as it doesn't always have the same content as the over the air broadcast.


So, anyway -- Would I gain anything by tryng to record from the PCM device?  

This is the content of /dev/snd - I'm not even sure what arecord is recording from, I know that using the ncurses version alsamixer I set the input to 'line in' and I get audio that's pretty low volume, and if I putz with increasing the volume too much I wind up with a lot of .. static-like fuzz and noise in the quiet areas.  These are most noticeable when playing on headphones.  

When I use the mic jack for recording, the output volume on the Rolls and the recording gain have to be just right or you can't hear anything, or you get blasted by sounds like loudspeakers overdriven to the point they will melt.

When I use lame to convert the wav to mp3 interactively, it has a rudimentary display that looks sort of like a level indicator -- but I have yet tor un across a reasonable explantion of this to help figure out what I'm really looking at.


```

# ls -al /dev/snd/
total 0
drwxr-xr-x  3 root root      180 May  2 11:39 .
drwxr-xr-x 14 root root     4140 May  3 09:31 ..
drwxr-xr-x  2 root root       60 May  2 11:39 by-path
crw-rw---T  1 root audio 116,  5 May  2 11:39 controlC0
crw-rw---T  1 root audio 116,  4 May  3 10:13 pcmC0D0c
crw-rw---T  1 root audio 116,  3 May  2 11:39 pcmC0D0p
crw-rw---T  1 root audio 116,  2 May  2 11:39 pcmC0D1p
crw-rw---T  1 root audio 116,  1 May  2 11:39 seq
crw-rw---T  1 root audio 116, 33 May  2 11:39 timer

**** List of CAPTURE Hardware Devices ****
card 0: DX [Xonar DX], device 0: Multichannel [Multichannel]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

dmix:CARD=DX,DEV=0
    Xonar DX, Multichannel
    Direct sample mixing device
dsnoop:CARD=DX,DEV=0
    Xonar DX, Multichannel
    Direct sample snooping device
hw:CARD=DX,DEV=0
    Xonar DX, Multichannel
    Direct hardware device without any conversions
plughw:CARD=DX,DEV=0
    Xonar DX, Multichannel
    Hardware device with all software conversions




```


Added the PCM device lists

---

### Post by tgalati4 on 2013-05-04
You can record off of any channel that is exposed to the operating system.  Snoop is the feedback channel, and it looks like you have pre and post digital channels as well.  Only experimentation will tell what works for you.  I agree, I have never figured out what LAME was displaying, other than "it seems to be doing something."  And I couldn't find anything in the documentation either.  Is each hash mark 3dB?  Who knows?

I would send an email to the radio station and tell them of your troubles.  It is true that many stations broadcast a different stream than over-the-air.  Not sure why, but it may have to do with advertising contracts or tailoring their airplay to a commuter market versus an at-home market.

---

