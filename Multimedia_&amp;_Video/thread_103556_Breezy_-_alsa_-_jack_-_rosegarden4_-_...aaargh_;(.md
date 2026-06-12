---
title: "Breezy - alsa - jack - rosegarden4 - ...aaargh ;("
date: 2005-12-14
forum: Multimedia &amp; Video
---

### Post by eliaz on 2005-12-14
My mission:

- to make rosegarden4 to work
- to make roland-keyboard and midi-interface to work with rosegarden4

My hardware:

- Acer Aspire laptop 3000 (SIS7012-sound chipset)
- M-Audio MIDISPORT 2X2
- Roland PC-180 keyboard

My OS:
- Ubuntu Breezy Badger 5.10

The brief description of problem:  

- it seems that JACKD starts normally both as a user 'user' and 'su' (qjackctl, sudo only in realtime-mode, see log below)
- while running JACKD it seems that Rosegarden4 GUI starts normally but there is no sound at all 
- while "playing" rosegarden4 JACKD crashes (see error messages below)
- Rosegarden4 regonized M-audio midisport, it seems ok ([http://usb-midi-fw.sourceforge.net/](http://usb-midi-fw.sourceforge.net/))
- aplayer sounds good while JACK IS NOT running ("aplay something.wav")
- aplayer DOES NOT work with -Djackplug while JACK IS running because libasound_module_pcm_jack.so is missing ("aplay -Djackplug something.wav",  ~/.asoundrc created)

I installed (apt-get) alsa- whatever including asoundlib2 and many related packages but alsa-lib (and libasound_module_pcm_jack.so) is still missing. 

I assume that there is no sense to continue rosegarden4 configuration until alsa-lib exist (and "aplay -Djackplug something.wav" works properly). Am I right? 

Questions:

Why alsa-lib does not appear after libasound2* installation?

Is it possible to apt-get needed ALSA functionality for breezy without recompile and reinstall it completely?

Can you see any other (easier) way to get roland - midisport - rosegargen4 to work in breezy?  




********* JACKD message *************

19:52:44.175 Patchbay deactivated.
19:52:44.536 Statistics reset.
19:52:44.552 Startup script...
19:52:44.552 artsshell -q terminate
19:52:44.638 MIDI connection graph change.
19:52:44.948 Startup script terminated with exit status=256.
19:52:44.949 JACK is starting...
19:52:44.950 /usr/bin/jackd -dalsa -dhw:0,0 -r44100 -p1024 -n2 -i2 -o2
19:52:44.960 JACK was started with PID=11488 (0x2ce0).
jackd 0.99.0
Copyright 2001-2003 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0,0|hw:0,0|1024|2|44100|2|2|nomon|swmeter|-|32bit
control device hw:0
configuring for 44100Hz, period = 1024 frames, buffer = 2 periods
Couldn't open hw:0,0 for 32bit samples trying 24bit instead
Couldn't open hw:0,0 for 24bit samples trying 16bit instead
Couldn't open hw:0,0 for 32bit samples trying 24bit instead
Couldn't open hw:0,0 for 24bit samples trying 16bit instead
19:52:45.161 MIDI connection change.
19:52:45.363 MIDI connection change.
19:52:47.177 Statistics reset.
19:52:47.183 Client activated.
19:52:47.183 Audio connection change.
19:52:47.185 Audio connection graph change.
**** alsa_pcm: xrun of at least 29.796 msecs
19:52:49.210 XRUN callback (1 skipped).
19:52:58.751 XRUN callback (2).
**** alsa_pcm: xrun of at least 11.503 msecs
**** alsa_pcm: xrun of at least 2.598 msecs

...


********* aplay -Djackplug something.wav *************

 
ALSA lib pcm.c:2052:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_jack.so
aplay: main:533: audio open error: No such file or directory

********* JACKD error message while playing rosegarden4 *************

Sound server informational message:
Error while initializing the sound driver:
device: default can't be opened for playback (Device or resource busy)
The sound server will continue, using the null output device.

********* Information - rosegarden4 after JACKD crash *************


JACK Audio subsystem is losing sample frames.



********* ~/.asoundrc *************

pcm.jackplug {
    type plug
    slave { pcm "jack" }
}

pcm.jack {
    type jack
    playback_ports {
        0 alsa_pcm:playback_1
        1 alsa_pcm:playback_2
    }
    capture_ports {
        0 alsa_pcm:capture_1
        1 alsa_pcm:capture_2
    }
}

---

