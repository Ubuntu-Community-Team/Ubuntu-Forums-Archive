---
title: "ALSA pcm multi problem"
date: 2007-10-24
forum: Multimedia &amp; Video
---

### Post by flash3843 on 2007-10-24
A few specifics first:

I'm running Ubuntu 7.04 (Feisty Fawn), JACK 0.102.20, and ALSA Driver Version 1.0.14rc4.

My audio cards are an onboard Intel I82801DBICH4 and an Audigy 2 ZX Notebook.  Each "card" has 6 channels.  The Intel has four capture and 2 playback channels, and the Audigy has 3 capture and 3 playback channels.  Only one capture channel in each card is usable for my purposes.  

Based on a previous suggestion I'm trying to create a virtual soundcard that is a combination of the above two.  I've made a number of efforts to create the necessary ~/.asoundrc file, but all have failed.  

The following is my latest .asoundrc, followed by the messages when I run qjackctl and hit start:



# The ALSA pcm_multi plugin is used to merge several cards
# into one large virtual card. This allows programs
# like jackd, which only can handle one card at a time,
# to deal with them.

# .asoundrc for Intel 82810DB-ICH4 and Creative Soundblaster Audigy2 ZS Notebook
#
# Create virtual devices out of multiple soundcards.
# The Intel has 4 capture channels and 2 playback channels.
# The Audigy has 3 capture channels and 3 playback channels.

pcm.multi_capture {
        type multi
        slaves.a.pcm hw:0  
        slaves.a.channels 6
        slaves.b.pcm hw:1
        slaves.b.channels 6

# 2 channels of first soundcard (capture)
        bindings.0.slave a
        bindings.0.channel 0
        bindings.1.slave a
        bindings.1.channel 1
    
# 2 channels of second soundcard (capture)
        bindings.2.slave b
        bindings.2.channel 2
        bindings.3.slave b
        bindings.3.channel 3
}

ctl.multi_capture {
        type hw
        card 0
}

pcm.multi_playback {
        type multi
        slaves.a.pcm hw:0
        slaves.a.channels 6
        slaves.b.pcm hw:1
        slaves.b.channels 6

# 2 channels of first soundcard (playback)
        bindings.0.slave a
        bindings.0.channel 0
        bindings.1.slave a
        bindings.1.channel 1

# 2 channels of second soundcard (playback)
        bindings.2.slave b
        bindings.2.channel 2
        bindings.3.slave b
        bindings.3.channel 3
}

ctl.multi_playback {
        type hw
        card 0
}


Messages after running qjackctl and hitting start:

14:34:06.367 Patchbay deactivated.
14:34:06.390 Statistics reset.
14:34:06.431 MIDI connection graph change.
14:34:06.597 MIDI connection change.
14:34:24.889 Startup script...
14:34:24.889 artsshell -q terminate
can't create mcop directory
Creating link /root/.kde/socket-shiloh.
14:34:25.156 Startup script terminated with exit status=256.
14:34:25.156 JACK is starting...
14:34:25.156 /usr/bin/jackd -v -dalsa -r48000 -p1024 -n2 -D -Cmulti_capture -Pmulti_playback
14:34:25.169 JACK was started with PID=12981 (0x32b5).
getting driver descriptor from /usr/lib/libjack0.100.0/jack_freebob.so
getting driver descriptor from /usr/lib/libjack0.100.0/jack_alsa.so
getting driver descriptor from /usr/lib/libjack0.100.0/jack_oss.so
getting driver descriptor from /usr/lib/libjack0.100.0/jack_dummy.so
jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
server `default' registered
loading driver ..
apparent rate = 48000
creating alsa driver ... multi_playback|multi_capture|1024|2|48000|0|0|nomon|swmeter|-|32bit
configuring for 48000Hz, period = 1024 frames, buffer = 2 periods
ALSA: no playback configurations available (Invalid argument)
ALSA: cannot configure capture channel
cannot load driver module alsa
registered builtin port type 32 bit float mono audio
registered builtin port type 8 bit raw midi
clock source = system clock via gettimeofday
running with uid=0 and euid=0, will not try to use capabilites
new client: alsa_pcm, id = 1 type 1 @ 0x806c318 fd = -1
starting server engine shutdown
freeing shared port segments
stopping server thread
last xrun delay: 0.000 usecs
max delay reported by backend: 0.000 usecs
freeing engine shared memory
max usecs: 0.000, engine deleted
no message buffer overruns
cleaning up shared memory
cleaning up files
unregistering server `default'
14:34:25.429 JACK was stopped successfully.
14:34:25.430 Post-shutdown script...
14:34:25.431 killall jackd
jackd: no process killed
14:34:25.657 Post-shutdown script terminated with exit status=256.
14:34:27.207 Could not connect to JACK server as client. Please check the messages window for more info.


If anyone can shed some light on my problem I would really appreciate it.

Thanks.

flash3843

---

### Post by Aliby on 2008-01-15
I am starting to look at this as I am also trying to couple the "on-board audio" with a "SoundBlaster Live".

As there is an older thread with a slightly clearer thread description, it would be great if we can continue discussion there ...

[http://ubuntuforums.org/showthread.php?t=224102]("http://ubuntuforums.org/showthread.php?t=224102")
[I]
[SIZE="1"][COLOR="Gray"]PS. Post your code using the  CODE tags (use the Hatch web button #) - it make s it clearer and confined.
[/COLOR][/SIZE][/I]
:)

---

