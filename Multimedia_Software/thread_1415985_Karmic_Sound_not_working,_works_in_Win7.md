---
title: "Karmic Sound not working, works in Win7"
date: 2010-02-25
forum: Multimedia Software
---

### Post by Oriana on 2010-02-25
In reference to: [Comprehensive Sound Problem Solutions Guide v0.5e]("http://ubuntuforums.org/showthread.php?t=205449")

Toshiba Satellite A135-S2276
Dual-boot with GRUB2: Ubuntu 9.10, Windows Seven


What I've done so far: 

1. Step One, check what soundcards are installed on your system.

```
Terminal:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
Terminal:~$
```

...this is neither success nor failure. Um...

2. Step Two, find data on soundcard

```
Terminal:~$ lspci -v
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at c0500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
Terminal:~$
```

(there was more stuff, but that seems to be what I was looking for)
Hm. Capabilities denied? Perhaps.... Still...

3. Check to see if Alsa Driver exists.

Google Chrome: 
ATI-IXP southbridge AC97 audio
ATI-IXP southbridge AC97 modem
ATI-IXP southbridge HD-audio and modem
Me: Why are there so many options for my card? Audo, modem, and HD-audio and modem?! Well, I guess it's time to try them all. Surely one of them will work.

4. Load Alsa Driver.

```
Terminal:~$ sudo modprobe snd-hda-intel
[sudo] password for oriana:
Terminal:~$
```

What? Was it supposed to do something?

5. Use Alsamixer.

```
Terminal:~$ alsamixer
No mixer elems found

Terminal:~$
```

6. Follow Getting the ALSA drivers from a *fresh* kernel
No change.

7. Retried 1-5.
No change.

In reference of [Uninstall PulseAudio]("http://ubuntuforums.org/showthread.php?t=603598"):
8. Removed PulseAudio and installed esound. (sudo apt-get remove pulseaudio, sudo apt-get install esound.)
No change. Should I use "purge" command instead? Interestingly, Pulse was still a user on my computer according to:

```
Terminal:~$ grep 'audio' /etc/group
audio:x:29:pulse,oriana
Terminal:~$
```
"audio" was returned in bold red though.

9. Re-installed PulseAudio. (sudo apt-get install pulseaudio) Perhaps there was an error somewhere? Should I have "removed" or "purged" esound?
No change.

10. Looked at [PulseAudio PerfectSetup]("http://www.pulseaudio.org/wiki/PerfectSetup"). It might as well be in Mandarin Chinese, except then I could ask my roommate or Google Translate for help.
-Installed: pavucontrol pavumeter paman padevchooser paprefs.

NO CHANGE.


I'm blank and tired and late for class. Help?

---

### Post by mörgæs on 2010-02-25
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats](https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats)

- or switch to Ubuntu 9.04, if everything else fails.

---

### Post by Yellow Pasque on 2010-02-25
I would try fresh ALSA one more time (BTW, your driver is snd-hda-intel)
[http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

If that fails, try OSS4: [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

If that fails.. maybe you're stuck with Windows 7

---

### Post by Oriana on 2010-02-26
The Karmic Caveats site did not help. Some of the ideas would not work, many of the ideas returned no data.

However, updating Alsa using that script did. 

Thank you both for your help!

---

