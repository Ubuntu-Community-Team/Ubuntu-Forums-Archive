---
title: "Help!! Sound Settings crashes with USB sound card (12.10 64 bit)"
date: 2012-11-04
forum: Multimedia Software
---

### Post by The Bright Side on 2012-11-04
Hey guys,

I'm having the same problem Def Sum describes in comment 3 of this bug report:
[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1067700](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1067700)

When my USB sound card is plugged in, the Sound Settings crash when clicking on them.

The sound card (Creative Sound Blaster X-Fi Surround 5.1 pro) works fine. I can listen to 5.1 surround using VLC. But when I play back stereo, it's all messed up. Sound only comes through my system's tiny stereo speakers instead of the 5.1 spread Ubuntu does when you define analogue 5.1 as your sound output option (which I can no longer do).

It used to work fine until a couple days ago, too!

I'm at the end of my wits. I did something yesterday (don't remember what) that caused apport to report a system program error at every login. Now I uninstalled apport, but yeah, the Sound Settings are broken.

Is there an alternate way to control my sound card? How can I get this back? Any files I could perhaps look into? Logs? Anything?

Hope you guys can help me.

---

### Post by The Bright Side on 2012-11-04
Oh btw, I tried the commands the guy in this thread did:
[http://ubuntuforums.org/showthread.php?t=2056497](http://ubuntuforums.org/showthread.php?t=2056497)

Check them out:

```
thebrightside@FRIENDLY-SATAN:~$ cat /proc/asound/cards
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfe87c000 irq 19
 1 [Pro            ]: USB-Audio - SB X-Fi Surround 5.1 Pro
                      Creative Technology Ltd SB X-Fi Surround 5.1 Pro at usb-0000:00:13.0-2, full sp

thebrightside@FRIENDLY-SATAN:~$ cat /proc/asound/modules
 0 snd_hda_intel
 1 snd_usb_audio
```

---

### Post by The Bright Side on 2012-11-04
Okay, so anybody who has this problem, here's a workaround.

[http://freedesktop.org/software/pulseaudio/pavucontrol/](http://freedesktop.org/software/pulseaudio/pavucontrol/)

Readily available in the Ubuntu repos. Look for pavucontrol. Shows up as "PulseAudio Volume Control" in your applications after installation. Works perfectly. Since this is technically not a *solution*, I'll not mark this thread as solved though.

---

