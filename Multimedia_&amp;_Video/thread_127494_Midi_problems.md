---
title: "Midi problems"
date: 2006-02-09
forum: Multimedia &amp; Video
---

### Post by mrhelpman on 2006-02-09
I have had ubuntu running now for about a week. Most of setup has gone well but I am having problems getting the midi working on the sound card.  I can play other sounds, such as .ogg or .flac files, through the sound card successfully. At the moment I am trying to use pmidi to play midi files. The sound card is a Sound Blaster Live.

I found this article on the forums.

[http://ubuntuforums.org/showthread.php?t=30963](http://ubuntuforums.org/showthread.php?t=30963)

and still there is no midi from the soundcard.

The process does make some difference. Before going through the above process I get the following when I try a file:

johnt@tomo001:~/Desktop$pmidi -p64:0 example-1.midi
Could not open sequencer: No such file or directory

After going through the process I get:
$ pmidi -l
 Port     Client name                       Port name
 62:0     Midi Through                      Midi Through Port-0
 64:0     EMU10K1X MPU-401 (UART)  

Then, when I try and play a midi file there are no error messages, the cursor just returns after a period of time - the time it would take to play the midi file I guess.

However when I try and load the soundfonts as described in the article I get:
$ asfxload FluidR3GM.SF2
No Emux synth hwdep device is found

Thanks for taking the time to read a rather long posting.

The volume control - either the native gnome or alsamixer do not appear to have a channel for synth/midi output.

John T.

---

### Post by ajgreeny on 2006-02-09
I had exactly the same error problems with my setup but it was all solved when I installed timidity, timidity-interfaces-extra, and freepats, using synaptic.  I can't promise, but it's worth a try if you have not already got those on your computer.

Good luck!

---

### Post by mrhelpman on 2006-02-10
> but it was all solved when I installed timidity, timidity-interfaces-extra, and freepats, using synaptic.

This may work but timidity is midi to wav converting software and as the sound blaster live cards have wave tables build onto the card it should not be needed. However I notice that my card is a sound blast live "value" card if this makes any difference.

I have also noted that when I look at /dev/sndstat I see that the synth  device is not available in config:
johnt@tomo001:~$ cat /dev/sndstat
Sound Driver:3.8.1a-980706 (ALSA v1.0.9 emulation code)
Kernel: Linux tomo001 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686
Config options: 0

Installed drivers:
Type 10: ALSA emulation

Card config:
Dell Sound Blaster Live! at 0xece0 irq 16
USB Device 0x471:0x311 at usb-0000:02:0a.1-1, full speed

Audio devices:
0: EMU10K1X Front (DUPLEX)
1: USB Audio

Synth devices: NOT ENABLED IN CONFIG

Midi devices:
0: EMU10K1X MPU-401 (UART)

Timers:
7: system timer

Mixers:
0: SigmaTel STAC9708,11
1: USB Mixer

---

### Post by FarEast on 2006-02-10
Hi,
I have googled and found this.
[http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg14526.html](http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg14526.html)

---

### Post by mrhelpman on 2006-02-10
Thanks for doing my googling for me!:) 

This confirms my suspicions that the DELL SB Live card which is what I actually have does not behave like a normal SBLive card. I wonder if, when the card is working under MS windows, it is actually using software to create the sounds rather than wavetables in the sound card hardware.

I have tried to load the snd_emu10k1x_synth instead of the standard snd_emu10k1_synth and of couse I get:

> johnt@tomo001:~$ sudo modprobe snd_emu10k1X_synth
FATAL: Module snd_emu10k1x_synth not found.


So I suspect my choices are to use timidity or to go down to the shops tomorrow morning and buy a propper SBLive card.

Thanks for everyones input.

John T.

---

### Post by mrhelpman on 2006-02-10
OK people

I have just downloaded timidity and the midi now works - very well actually - I think it sounds better then when the machine is booted in Windows, but I have to becuase I have been working at this a few hours.;) 

Sorry Ajgreeny for not taking your advice earlier.:( 

IMHO the Dell version of the soundbaster live card (emu10k1x) does not have on board wave tables and this is why I was having problems getting it going.

Many thanks to all who have looked and contributed to the thread.

JT

---

