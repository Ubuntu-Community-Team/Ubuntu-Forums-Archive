---
title: "NI Traktor Scratch USB - .asoundrc, PA, jack, how!?"
date: 2017-05-07
forum: Multimedia Software
---

### Post by Andreas_Hesse on 2017-05-07
I have this Native Instruments Traktor Audio 4 usb that's hooked      up to a ok beefy desktop running kubuntu 16.04.

    I figure this might have asked before but I thought i'd give it a try anyway as I'm so totally      stuck setting it up and maybe someone has the simple trick. I thought I was pretty confident in a linux      terminal but all that sound stuff is confusing to me. Alsa, jack,      jackqtl, OSD, pulseaudio the list goes on.. i'm lost on what to      have and not have and i feel i've been through so many google      links, .asoundrc options and jackd flags. I don't get whats doing      what and what's needed to get the last bits working.
    I'm trying to avoid having to launch a full desktop vm!!

    Below's my .asoundrc and running jackd first is now saying the card    exists when starting traktor (2.6.2 is the only one so far i've been    able to launch well in playonlinux) 
[B]
Everything seems to work fine except still no input from the vinyls! Help![/B]
    
    the output of 
    ```
jackd -d alsa -d plughw:Audio4DJ > jackdoutput1.txt 2>&1
```

#run playonlinux
# run traktor...
#take screnshot
# quit all

```
&#9492;[~]> awk '!a[$0]++' jackdoutput1.txt 
no message buffer overruns
jackdmp 1.9.11
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2014 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in realtime mode with priority 10
self-connect-mode is "Don't restrict self connect requests"
audio_reservation_init
Acquire audio card Audio2
creating alsa driver ... plughw:Audio4DJ|plughw:Audio4DJ|1024|2|48000|0|0|nomon|swmeter|-|32bit
configuring for 48000Hz, period = 1024 frames (21.3 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit float little-endian
You appear to be using the ALSA software "plug" layer, probably
a result of using the "default" ALSA device. This is less
efficient than it could be. Consider using a hardware device
instead rather than using the plug layer. Usually the name of the
hardwa
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit float little-endian
ALSA: use 2 periods for playback
JackEngine::XRun: client = Traktor was not finished, state = Triggered
JackAudioDriver::ProcessGraphAsyncMaster: Process error
Jack main caught signal 2
Released audio card Audio2
audio_reservation_finish
WARNING: 8 message buffer overruns!

```
hope to hear your tips if you have a moment.. so many hours of beats lay ahead if i get this up and running (again)!

Andreas
```
[SIZE=-1]&#9492;[~]> cat .asoundrc
#-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-
# Native Instruments :: Audio2DJ ALSA Configuration
# - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
#
# device        channels ports
# -------- --- ---------
# djA 2 12xx
# djB 2 xx34
#
# djAB 4 1234

#-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-
# dj(a-d) :: Raw 1x1 Stereo Devices
# - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
pcm.djA { type plug; slave.pcm "hw:Audio4DJ,0,0"; }
pcm.djB { type plug; slave.pcm "hw:Audio4DJ,0,1"; }


# - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
# djAB :: Multi 2x2 Stereo Device (Ports 1-4, Channels A+B)
# - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
pcm.djAB {
type multi

# bind hardware devices
slaves.a.pcm djA
slaves.a.channels 2
slaves.b.pcm djB
slaves.b.channels 2

# bind channels to virtual device
bindings.0.slave a
bindings.0.channel 0
bindings.1.slave a
bindings.1.channel 1
bindings.2.slave b
bindings.2.channel 0
bindings.3.slave b
bindings.3.channel 1
}

# ------------------------------------------------------
# Custom asoundrc file for use with snd-aloop and JACK
#
# use it like this:
# env JACK_SAMPLE_RATE=44100 JACK_PERIOD_SIZE=1024 alsa_in (...)
#

# ------------------------------------------------------
# playback device
pcm.aloopPlayback {
type dmix
ipc_key 1
ipc_key_add_uid true
slave {
pcm "hw:Loopback,0,0"
format S32_LE
rate {
@func igetenv
vars [ JACK_SAMPLE_RATE ]
default 44100
}
period_size {
@func igetenv
vars [ JACK_PERIOD_SIZE ]
default 1024
}
buffer_size 4096
}
}

# capture device
pcm.aloopCapture {
type dsnoop
ipc_key 2
ipc_key_add_uid true
slave {
pcm "hw:Loopback,0,1"
format S32_LE
rate {
@func igetenv
vars [ JACK_SAMPLE_RATE ]
default 44100
}
period_size {
@func igetenv
vars [ JACK_PERIOD_SIZE ]
default 1024
}
buffer_size 4096
}
}

# duplex device
pcm.aloopDuplex {
type asym
playback.pcm "aloopPlayback"
capture.pcm "aloopCapture"
}

# ------------------------------------------------------
# default device
pcm.!default {
type plug
slave.pcm "aloopDuplex"
}

# ------------------------------------------------------
# alsa_in -j alsa_in -dcloop -q 1
pcm.cloop {
type dsnoop
ipc_key 3
ipc_key_add_uid true
slave {
pcm "hw:Loopback,1,0"
format S32_LE
rate {
@func igetenv
vars [ JACK_SAMPLE_RATE ]
default 44100
}
period_size {
@func igetenv
vars [ JACK_PERIOD_SIZE ]
default 1024
}
buffer_size 32768
}
}

# ------------------------------------------------------
# alsa_out -j alsa_out -dploop -q 1
pcm.ploop {
type plug
slave.pcm "hw:Loopback,1,1"
}[/SIZE]



```

---

