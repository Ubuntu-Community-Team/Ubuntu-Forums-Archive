---
title: "Toshiba no sound half solved"
date: 2008-01-10
forum: Multimedia &amp; Video
---

### Post by Crusty Juggler on 2008-01-10
I've been working for a week or so on sorting the sound out on my Toshiba A200.  I've been following [this]("http://ubuntuforums.org/showthread.php?t=205449&highlight=toshiba+a200") and [this]("http://ubuntuforums.org/showthread.php?t=539595&highlight=toshiba+a200") guide.  

Recently, I was able to get Ubuntu to recognise my sound card, in that the volume control icon did not have the cross through it and I was able to control the volume level, though no sound came out.  After continuing to mess around with it, I now have the red cross back, but when I am prompted for my login and password, the drums play.  

aplay -l gives:
```
aplay: device_list:204: no soundcards found...
```

lspci -v gives:
```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at f0b40000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

```

alsamixer gives:
```
alsamixer: function snd_ctl_open failed for default: No such device
```

I could really use some help.  I have no idea what to try next and am getting frustrated.

---

### Post by neilsoncarlos on 2008-01-11
Yep, I having the same, exactly the same problem... all commands have the same output and I getting crazy... hehehehe
please guys, if anyone knows the solution for this problem, tell us because I have followed all "how to"s and anything works...
tnx a lot ;)
neilson

---

