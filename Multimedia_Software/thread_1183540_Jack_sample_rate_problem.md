---
title: "Jack sample rate problem"
date: 2009-06-10
forum: Multimedia Software
---

### Post by Jamesss on 2009-06-10
For quite a while now, I have had an issue relating to jack where I select a sample rate of 44100 in the setup, and it always runs at 44099 hz. This means that whenever I import anything into Ardour, it tries to resample it,  so as a workaround I just tell Ardour to not copy the files and use them at the current rate. Now in Pure Data I'm trying to play an ogg stream using oggamp~ and it works fine running on Alsa sound, but won't work with jack because of the sample rate mismatch.

```
oggamp~: resampling from 44100 Hz to 44099 Hz not supported !
```

Actually I've just noticed that if I start PD with no audio driver specified, load the patch and ogg streams and *then* select jack from the PD audio driver menu it works!

It's a bit annoying having to do this - any ideas about this problem? 
The closest thing I can find to my problem is this post here:

[http://www.mail-archive.com/alsa-devel@lists.sourceforge.net/msg01320.html]("http://www.mail-archive.com/alsa-devel@lists.sourceforge.net/msg01320.html")

Something to do with set_rate() ...? I've no idea where to find this or how to change it!

Any help appreciated!

thanks

James

Ubuntu 9.04 Jaunty
Kernel 2.6.28.12=generic
1.5GB RAM
AMD Athlon XP 2400+

Jack 0.3.4
Pure Data 0.40.3-extended
Ardour 2.7.1

```
james@james-desktop:~$ lspci -v -s 00:05.0
00:05.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 08)
	Subsystem: Ensoniq ES1371 [AudioPCI-97]
	Flags: bus master, slow devsel, latency 32, IRQ 16
	I/O ports at d800 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: ENS1371
	Kernel modules: snd-ens1371
```

---

### Post by Jamesss on 2009-06-10
Well to reply to my own post it looks like this has fixed it! -

[http://ardour.org/node/1280](http://ardour.org/node/1280)

Basically, selecting "plughw:0" instead of "default" in the interface option of qjackctl sets the sample rate to 44100.

---

