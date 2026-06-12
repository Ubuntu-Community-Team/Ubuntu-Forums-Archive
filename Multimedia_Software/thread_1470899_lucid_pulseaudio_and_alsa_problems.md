---
title: "lucid pulseaudio and alsa problems"
date: 2010-05-03
forum: Multimedia Software
---

### Post by johnh10000 on 2010-05-03
Hi I use idjc, and audiacity alot. With just alsa on it all works fine ecept the mic on idjc, which use jack.

I'd like just to be able to use alsa. if not how do i configure pulseaudio, so it works with audiacity?

here's the output from a command promt

```


johnh@tux:~$ idjc -p new
Internet DJ Console Version 0.8.1
Copyright 2005-2009 Stephen Fairchild
Released under the GNU General Public License V3.0

Language translation: en_GB
no message buffer overruns
cannot lock down memory for jackd (Cannot allocate memory)
JACK: unable to mlock() port buffers: Cannot allocate memory
JACK: unable to mlock() port buffers: Cannot allocate memory
cannot lock down memory for RT thread (Cannot allocate memory)
shout_initialiser: shout_init called
jack error: cannot lock down memory for RT thread (Cannot allocate memory)
started 6 encoders, 6 streamers, 2 recorders
threads initialised
jack sample rate is 44100
Restoring previous session
stream-mon was toggled ON
Metadata source was changed. Before: 3
Metadata source was changed. Now: 4
crossfader pattern changed
Track history text is more than six hours old.  Disregarding.

ALSA lib pulse.c:229:(pulse_connect) PulseAudio: Unable to connect: Connection refused

ALSA lib pulse.c:229:(pulse_connect) PulseAudio: Unable to connect: Connection refused

Toggle ON recieved for signal: Play
player_startup left
Seek time is 0 seconds
final gain value of -2.000000 dB
player context id is 1

Player has started
ALSA lib pulse.c:229:(pulse_connect) PulseAudio: Unable to connect: Connection refused

Mic Open was toggled ON
Mic L Open was toggled ON
Mic R Open was toggled ON
ALSA lib pulse.c:229:(pulse_connect) PulseAudio: Unable to connect: Connection refused

Mic Open was toggled OFF
Mic L Open was toggled OFF
Mic R Open was toggled OFF
ALSA lib pulse.c:229:(pulse_connect) PulseAudio: Unable to connect: Connection refused

ALSA lib pulse.c:229:(pulse_connect) PulseAudio: Unable to connect: Connection refused

Toggle OFF recieved for signal: Play
player shutdown code was called
finished eject
ALSA lib pulse.c:229:(pulse_connect) PulseAudio: Unable to connect: Connection refused

ALSA lib pulse.c:229:(pulse_connect) PulseAudio: Unable to connect: Connection refused

Toggle ON recieved for signal: Play
player_startup right
Seek time is 0 seconds
final gain value of -2.000000 dB
frames 396
bytes 165928
toc has been read
lame tag found
frames to drop 1104 and 1728
player context id is 1

Player has started
ALSA lib pulse.c:229:(pulse_connect) PulseAudio: Unable to connect: Connection refused

finished eject
termination due to end of track
Stopping in accordance with manual mode
Toggle OFF recieved for signal: Play
player shutdown code was called
Toggle ON recieved for signal: Play
player_startup left
Seek time is 0 seconds
final gain value of -2.000000 dB
player context id is 3

Player has started
ALSA lib pulse.c:229:(pulse_connect) PulseAudio: Unable to connect: Connection refused

ALSA lib pulse.c:229:(pulse_connect) PulseAudio: Unable to connect: Connection refused

Toggle OFF recieved for signal: Play
player shutdown code was called
finished eject
ALSA lib pulse.c:229:(pulse_connect) PulseAudio: Unable to connect: Connection refused

Toggle ON recieved for signal: Play
player_startup left
Seek time is 0 seconds
final gain value of -2.000000 dB
player context id is 5

Player has started
ALSA lib pulse.c:229:(pulse_connect) PulseAudio: Unable to connect: Connection refused

finished eject
termination by check mixer signal
Stopping in accordance with manual mode
Toggle OFF recieved for signal: Play
player shutdown code was called
Toggle ON recieved for signal: Play
player_startup left
Seek time is 0 seconds
final gain value of -2.000000 dB
player context id is 7

Player has started
ALSA lib pulse.c:229:(pulse_connect) PulseAudio: Unable to connect: Connection refused

ALSA lib pulse.c:229:(pulse_connect) PulseAudio: Unable to connect: Connection refused

Toggle OFF recieved for signal: Play
player shutdown code was called
finished eject
ALSA lib pulse.c:229:(pulse_connect) PulseAudio: Unable to connect: Connection refused

threads_shutdown commencing
Mixer module has closed
threads_shutdown finished
johnh@tux:~$

```

---

### Post by malangaman on 2010-10-09
Did you solve the problem?
I found this:
Audacity has now been packaged with a proper "alsa: pulse" device listed, in a ppa for ubuntu intrepid. See [https://launchpad.net/~diwic/+archive](https://launchpad.net/~diwic/+archive)

---

### Post by johnh10000 on 2010-10-09
> **malangaman said:**
> Did you solve the problem?
I found this:
Audacity has now been packaged with a proper "alsa: pulse" device listed, in a ppa for ubuntu intrepid. See [https://launchpad.net/~diwic/+archive](https://launchpad.net/~diwic/+archive)

I basically use sam brodcaster now on a dedicated windows box.  but will checkout your link thanks

---

