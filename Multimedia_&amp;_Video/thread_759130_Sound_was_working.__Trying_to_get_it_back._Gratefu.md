---
title: "Sound was working.  Trying to get it back. Grateful for any ideas!"
date: 2008-04-18
forum: Multimedia &amp; Video
---

### Post by briwood on 2008-04-18
I had sound working on my thinkpad T40p running 7.10. I tried using the alsa - jack plugin, but couldn't get it working (details on what I did below).  I've reverted to my old set up, but something is wrong. Thanks kindly inadvance for any ideas.

My current problem:

My sound applications all appear to work.  Rhythmbox, Rosegarden, Audacity will play files, but no sound comes out of the speakers. 

If I do

```
cat 1b.wav > /dev/dsp
``` 

I get garbled sound from the speaker.

Things I've checked:

Nothing muted in Volume Control or alsa mixer

```
~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

```
$ lspci |grep audio
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)

```

```

$ lsmod |grep snd
snd_rtctimer            4384  1 
snd_intel8x0           34972  1 
snd_ac97_codec        100644  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  2 snd_pcm_oss
snd_pcm                80388  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  3 snd_rtctimer,snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  11 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  2 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm

```

(Alsa-project says that snd_intel8x0 is correct for my card.)

I've rebooted and restarted alsa-utils a number of times.  No luck.

Anyone have any other ideas for me?  

If you are interested here's what I did when trying to use the Alsa Jack plugin:

I was having trouble switching between applications like Audacity and Rhythmbox.  In an attempt to remedy that I was experimenting with using the ALSA JACK plugin.  I while trying to get that to work I attempted to install the latest libasound from debian.  I was doing that because of what I read here [https://bugs.launchpad.net/ubuntu/+source/alsa-lib/+bug/148510](https://bugs.launchpad.net/ubuntu/+source/alsa-lib/+bug/148510)

Here's what I did:

```
brian@diz:~/Desktop/dl$ sudo dpkg -i libasound2_1.0.16-2_i386.deb 
[sudo] password for brian:
(Reading database ... 136544 files and directories currently installed.)
Preparing to replace libasound2 1.0.14-1ubuntu8 (using libasound2_1.0.16-2_i386.deb) ...
Unpacking replacement libasound2 ...
dpkg: dependency problems prevent configuration of libasound2:
 libasound2 depends on libc6 (>= 2.7-1); however:
  Version of libc6 on system is 2.6.1-1ubuntu10.
dpkg: error processing libasound2 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libasound2
brian@diz:~/Desktop/dl$ 

```

I then tried to figure out if I could upgrade libc6 so that the package could be configured.  I could not acertain if that is possible, so I decided to undo my changes.  Here's what I did:

```
sudo dpkg --force-depends -r libasound2
```

I then fixed the dependancies that were broken in about 30 sound packages by using Synaptic to reinstall just one package, XMMS.  The synaptic details were:

```
libasound2 (version 1.0.14-1ubuntu8) will be installed
xmms (version 1:1.2.10+20070601-1) will be re-installed

```

After that I had 0 broken packages and things looked cool. 

Thanks for reading!

---

### Post by briwood on 2008-04-19
I fixed this. I was just trying to break it again to verify what, exactly fixed it, but I'm not exactly sure and I don't want to know badly enough to risk messing everything up again.

I knew that sound was working on 4/14, so I went back through /var/log/apt/term.log and looked closely at everything I'd installed since then.  I used synaptic and purged the following packages.  After each purge I did

[CODE]
sudo /etc/init.d/alsa-utils restart
timidity /home/brian/Desktop/dl/Jinriksha.mid 
[CODE]

* libasound2-plugins
** purged. restart alsa. NO
** libasound2-dev
** purged. restart alsa. NO
* libpulse0, libpulse-dev, libpulse-browse0, libpulse-mainloop-glib0 ... 
** purged. restart alsa.  **YES timidity plays!**

I remember a while ago when I tried to install PulseAudio I broke stuff and removing the packages fixed things.  This time around I think pulse got installed as a side effect of some other install.

Anyway, maybe this info will help someone in the future.

---

