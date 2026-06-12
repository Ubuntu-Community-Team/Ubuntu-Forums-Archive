---
title: "CS46xx Sound problem"
date: 2007-12-17
forum: Multimedia &amp; Video
---

### Post by bigmo9 on 2007-12-17
I have an IBM thinkpad t22 and it has a Cirrus Logic CS4614/22/24/30 and I'm having a problem getting sound to work.  When the computer starts up the login screen produces a crackle and my system beep also works.  The output of aplay -l shows that the card, lspci also shows the card there.  The unusual thing that I see is the output of dmesg:
```
dmesg
[   27.896000] cs46xx: failure waiting for FIFO command to complete
```
I'm not sure but I think this may be the problem.

---

### Post by bigmo9 on 2007-12-18
Does anyone have any suggestions?

---

### Post by tgalati4 on 2007-12-18
Try the following:  (in a terminal)

>sudo modprobe snd-cs4236 isapnp=0 port=0x530 cport=0xf00 irq=5 dma1=1 dma2=0

If that works, then put that line (minus the sudo modprobe) as the last line off your /etc/modules file.

>sudo cp /etc/modules /etc/modules.bak
>sudo nano /etc/modules

---

### Post by bigmo9 on 2007-12-18
That didn't work but thank you for the suggestion.  I feel like I may be missing something.  I've followed this guide

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

I get the dmesg start up error.  No error trying to run a music program from the terminal, I've checked all the channels I can find and none of them are muted

---

### Post by bigmo9 on 2007-12-18
I just looked in /etc/modprobe.d/blacklist-oss and find that the snd_cs46xx was listed in there, but the output of ```
lsmod | grep snd
snd_cs46xx             86120  1 
gameport               16776  2 snd_cs46xx
snd_ac97_codec        101284  1 snd_cs46xx
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            43008  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80004  5 snd_cs4236_lib,snd_cs4231_lib,snd_cs46xx,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  3 snd_mpu401_uart,snd_cs46xx,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53360  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  4 snd_opl3_lib,snd_cs4231_lib,snd_pcm,snd_seq
snd_seq_device          9228  6 snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54788  18 snd_cs4236,snd_opl3_lib,snd_hwdep,snd_cs4236_lib,snd_mpu401_uart,snd_cs4231_lib,snd_cs46xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  3 snd_cs4231_lib,snd_cs46xx,snd_pcm

```
shows it loaded.

---

### Post by tgalati4 on 2007-12-18
I believe it is only blacklisted for the Open Sound Server (OSS).  You can forcefully remove it with:

>sudo modprobe -r snd_cs46xx

Then add your favorite sound module

>sudo modprobe yourfavoritesoundmodule yourfavoriteswitches

I used to have a T22 machine.  Solid, generic hardware.  Try being more creative with your sound module selection and switches.  A google search will give you some clues.  There are lots of Linux tutorials for Thinkpads.

You need to reboot to reset the sound hardware once you get a working modprobe configuration.  Don't forget to put the working combo in /etc/modules.

Try blacklisting snd_cs46xx in /etc/modprobe.d/blacklist

Then manually load the command I gave earlier.

---

### Post by bigmo9 on 2007-12-18
Thanks I really appreciate the help

---

### Post by tgalati4 on 2007-12-18
Of course you said crackle.  That could be a burned out sound chip.  The start up beep will work since that is just a piezo buzzer.  A crackle could indicate the amp or speakers are blown.  Did you try headphones?  A crackle in the headphones could indicate a blown final stage amp.  Thinkpads are generally tough, but have pretty crappy sound chips and speakers.

---

### Post by bigmo9 on 2007-12-18
I don't think that is the problem I know the sound works under windows 2000, my wife feels more comfortable using it for the time being.

---

### Post by bigmo9 on 2008-01-01
I'm still having a problem with my sound it no longer crackles and I know the speakers aren't blown as I was setting up some of the shortcuts for volume I started getting some sound out of the speaker, it was just noise.  I tried testing it and no sound came out other then the that white noise.  I've tried several different combination of modules and none of them seem to work.  I don't have alsa muted or the program or the system.  Does anyone have a suggestion?  Thanks in advance

---

