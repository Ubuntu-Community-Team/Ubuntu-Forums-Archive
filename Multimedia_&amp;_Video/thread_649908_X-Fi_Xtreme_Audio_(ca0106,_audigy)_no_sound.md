---
title: "X-Fi Xtreme Audio (ca0106, audigy) no sound"
date: 2007-12-25
forum: Multimedia &amp; Video
---

### Post by bruno321 on 2007-12-25
Hi. I got a new sound card: Creative X-Fi Xtreme Audio. I was using the onboard audio. I installed the new card, disabled onboard audio from the BIOS (azalia codec: disabled), and booted Kubuntu 7.10. I get no sound. 

First of all, KMix shows the little loudspeaker greyed and crossed out.

aplay -l outputs:

```
tarjeta 0: CA0106 [CA0106], dispositivo 0: ca0106 [CA0106]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: CA0106 [CA0106], dispositivo 1: ca0106 [CA0106]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: CA0106 [CA0106], dispositivo 2: ca0106 [CA0106]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: CA0106 [CA0106], dispositivo 3: ca0106 [CA0106]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0

```

Which seems fine, but I wonder why display the same card 4 times.

Then lspci -v shows:

```
05:01.0 Multimedia audio controller: Creative Labs SB Audigy LS
        Subsystem: Creative Labs Unknown device 1013
        Flags: bus master, medium devsel, latency 32, IRQ 17
        I/O ports at d000 [size=32]
        Capabilities: <access denied>

```

Which doesn't seem so fine. Unknown device?

I've tried messing around with the sound controls with alsamixer. I've tried running an audio app like amarok as root with sudo to see if it was a permissions problem. I've followed the "comprehensive sound problem solutions guide" on this forums; I've compiled the latest alsa driver following this guide's instructions. Everything seems just fine, except for the "unknown device" thing going on and KMix which is greyed and crossed out. The little icon shows up as normal when I turn on IEC958 on the "parameters" tab, but no sound comes out.

Thank you.

---

### Post by Existentialist on 2007-12-25
The driver release by Creative for the x-fi line for linux is crap.  To start, you can try this thread to get it working:

[http://ubuntuforums.org/showthread.php?t=571656&highlight=xfi](http://ubuntuforums.org/showthread.php?t=571656&highlight=xfi)

---

### Post by bruno321 on 2007-12-25
I'm not sure that would work... First of all, I'm using Kubuntu 32-bit. And second, that's X-Fi beta driver, ok, but the X-Fi I have is not really an X-Fi: it's an Audigy (as it was recognized) with some modifications, so...

Thanks anyway :)

---

### Post by bruno321 on 2007-12-25
Some extra info:

```
$ cat /proc/asound/cards
 0 [CA0106         ]: CA0106 - CA0106
                      AudigyLS [Unknown] at 0xd000 irq 17

```

Also, under KMix parameters, the only option available is IEC958...

EDIT: More info: after doing "modprobe -r snd-hda-intel", I get this:

```
$ alsamixer
alsamixer: function snd_ctl_open failed for default: No such device
```

```
$ sudo /etc/init.d/alsasound restart
Shutting down sound driver: /usr/sbin/alsactl: save_state:1251: No soundcards found...
done
ALSA driver is already running.
```

Before doing that I had perfect access to alsa... Now KMix is shown with a cross. Makes more sense. But how can I direct alsa to the soundcard?

2nd EDIT: Okay, I found out about this alsaconf command. It perfectly recognized the Audigy LS:

```
Now ALSA is ready to use.
 For adjustment of volumes, use your favorite mixer.

 Have a lot of fun!

```

but when I run alsamixer I get the same "alsamixer: function snd_ctl_open failed for default: No such device" error.

---

### Post by bruno321 on 2007-12-25
Well, after doing what I detailed in my last post and rebooting, it worked! :)

---

### Post by canadalinux on 2008-01-26
I was having the same problem and I found this post on the alsa-user mailing list:

[http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg21618.html](http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg21618.html)

Just downloading and compiling the latest version from the alsa-project website fixed the problem for me right away.  Once I installed it and rebooted the sound card was automatically detected and sound was working right away.

---

