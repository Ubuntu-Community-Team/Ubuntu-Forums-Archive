---
title: "Problems with Jack"
date: 2006-10-13
forum: Multimedia &amp; Video
---

### Post by hAPPY_mAJA on 2006-10-13
This is the messages in Jack control.

What do I do? ](*,) 


06:43:46.762 Patchbay deactivated.
06:43:46.875 Statistics reset.
06:43:46.880 Could not open ALSA sequencer as a client. MIDI patchbay will be not available.
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: Filen eller katalogen finns inte
06:43:48.129 Startup script...
06:43:48.129 artsshell -q terminate
sound server terminated
06:43:48.574 Startup script terminated successfully.
06:43:48.587 JACK is starting...
06:43:48.591 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p1024 -n2 -D -C/dev/dsp -S -i5 -o5
06:43:48.614 JACK was started with PID=6095 (0x17cf).
jackd 0.100.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|/dev/dsp|1024|2|44100|5|5|nomon|swmeter|-|16bit
control device hw:0
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM /dev/dsp
ALSA: Cannot open PCM device alsa_pcm for capture. Falling back to playback-only mode
configuring for 44100Hz, period = 1024 frames, buffer = 2 periods
ALSA: cannot set channel count to 5 for playback
ALSA: cannot configure playback channel
cannot load driver module alsa
06:43:50.128 JACK was stopped successfully.
06:43:50.828 Could not connect to JACK server as client. Please check the messages window for more info.

---

### Post by jakoblund on 2006-10-14
The jack daemon can't use the alsa driver/hardware. This could mean that some other program is hijacking the sound card. KDE? aRTs? some music player, a flash plugin?
Also the line 
ALSA: cannot set channel count to 5 for playback
suggests you have set the number of out channels to five... You do have a surround card?

---

### Post by dolson on 2006-10-14
Also, the following error messages mean you have not loaded the ALSA sequencer, which you may or may not need (you will if you plan on doing any MIDI work):

06:43:46.880 Could not open ALSA sequencer as a client. MIDI patchbay will be not available.
ALSA lib seq_hw.c:456snd_seq_hw_open) open /dev/snd/seq failed: Filen eller katalogen finns inte

---

### Post by loboson on 2006-10-22
And.. what's the way of fixing it?

When will Ubuntu have easy midi support?? :confused: ](*,) 

> **dolson said:**
> Also, the following error messages mean you have not loaded the ALSA sequencer, which you may or may not need (you will if you plan on doing any MIDI work):

06:43:46.880 Could not open ALSA sequencer as a client. MIDI patchbay will be not available.
ALSA lib seq_hw.c:456snd_seq_hw_open) open /dev/snd/seq failed: Filen eller katalogen finns inte

---

### Post by zettberlin on 2006-10-23
> **loboson said:**
> And.. what's the way of fixing it?

When will Ubuntu have easy midi support?? :confused: ](*,)

It has. Unfortunately sombody has decided not to switch in on by default. Though it is easy to fix this:

# sudo bash
# modprobe snd-seq
# echo snd-seq >> /etc/modules
# exit

piece of cake eh?

Get the details and much more in the ubuntu studio wiki:

[http://wiki.ubuntustudio.org/index.php?title=Studio_Preparation#ALSA_Sequencer](http://wiki.ubuntustudio.org/index.php?title=Studio_Preparation#ALSA_Sequencer)

especially you should mention th part regarding /dev/rtc

For the latter and for reasonable work with jack you`ll need a usable kernel. I made very good experiences with the one from the french ubuntumusique-repo:

[http://www.ubuntuforums.org/showthread.php?t=261821](http://www.ubuntuforums.org/showthread.php?t=261821)

the kernel from testing can be used in edgy also :-)

good luck

---

### Post by gareththegeek on 2006-11-06
THANK YOU!!

Finally an answer to this damn sequencer error I have been getting in more apps than I can count!

Thanks!

---

### Post by content on 2006-11-27
> **zettberlin said:**
> 
# sudo bash
# modprobe snd-seq
# echo snd-seq >> /etc/modules
# exit



When I try this I get this 
> 
WARNING: Could not open '/lib/modules/2.6.17-10-generic/kernel/sound/core/snd.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.17-10-generic/kernel/sound/core/seq/snd-seq-device.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.17-10-generic/kernel/sound/core/snd-timer.ko': No such file or directory
FATAL: Could not open '/lib/modules/2.6.17-10-generic/kernel/sound/core/seq/snd-seq.ko': No such file or directory


I am using Edgy.  I had this working before but then I reinstalled for some reason or another and now this is happening. 
Does it have something to do with my hardware? 

Thanks

---

