---
title: "I can't get jackd2 to connect to alsa."
date: 2015-03-07
forum: Multimedia Software
---

### Post by guleblanc on 2015-03-07
I apologize in advance for what seems like a trivial and often asked question. But I can't seem to figure out even how to diagnose the problem.

I'm trying to configure my ubuntu 14.04 system to use my Akai EWI USB midi controller.  I am trying to use [Ted's Linux MIDI Guide]("http://tedfelix.com/linux/linux-midi.html")
to configure things.  But before I get midi working I need to test that jackd can route audio to alsa, and I can't get audio ouput from jackd.

I have verified that alsa works with pulseaudio, when pa is running.  I disabled pa and then made sure that pa did not autospawn (autospawn = no in /etc/pulseaudio/client.conf.)

I also verified that my hardware device is hw:0.  It's the only HW device in my machine. The EWI is not currently plugged in, and it's a MIDI device anyway.

When I run jackd from the command line I get this:

```
poppa@ossian:/media/biglocal/poppa/tmp$ jackd -d alsa --device hw:0 --rate 44100 --period 128
jackdmp 1.9.10
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2013 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
no message buffer overruns
no message buffer overruns
no message buffer overruns
JACK server starting in realtime mode with priority 10
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|128|2|44100|0|0|nomon|swmeter|-|32bit
configuring for 44100Hz, period = 128 frames (2.9 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback
```

I ran qjackctl with this server, and it seems to be connected.  The message window has no error messages:
```
12:36:17.044 Patchbay deactivated.
12:36:17.048 Statistics reset.
12:36:17.054 ALSA connection change.
12:36:17.063 D-BUS: Service is available (org.jackaudio.service aka jackdbus).
12:36:17.084 JACK connection change.
12:36:17.088 Client activated.
```

I then ran this command:
```
export JACK_PLAY_CONNECT_TO=system:playback_%d 
jack.play test.wav
```

I have played this .wav file before with aplay, so I know it plays, but no sound comes out of my speakers.  I think jack thinks it's playing, since qjackctl tells me this:

```
12:38:34.912 JACK connection graph change.
12:38:35.006 JACK connection change.
12:38:35.841 JACK connection graph change.
12:38:36.010 JACK connection change.
```

when I run jack.play.

Can anybody give me a clue?  Thanks.

P.S.
FWIW, alsa is working fine, so I don't think that's the problem.  But catting /proc/asound/cards gives me:
```
poppa@ossian:~/.config$ cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfdff4000 irq 16

```
I've also tried using "hw:SB" for "hw:0" in the jackd command, with no change in behavior.

Also, alsamixer tells me the levels are fine and not muted.

---

