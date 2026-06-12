---
title: "VT1723 issues on 10.04"
date: 2011-08-04
forum: Multimedia Software
---

### Post by PIDGINZ on 2011-08-04
I tried posting this in the general hardware section in the hopes that it would be seen by more people, but I got no responses there.

So basically I have a cheapo sound card with a VT1723+VT1618 chipset, which works fine in Windows 7 64bit. On Ubuntu it's a different story. More often than not, I get absolutely no sound whatsoever, and if I'm lucky, I'll get sound through my right headphone speaker only. Usually a reboot would fix it, but that stopped working for an unknown reason.

Using the ice1724 driver. I read that it is supposed to support the 1723 with generic code, but apparently that doesn't work for me. On boot I get this in my kernel log:
```

ice1724: No matching model found for ID 0x12140324
ice1724: Invalid EEPROM version 1

```I'd hoped that recompiling the 2.6.32.33 kernel would give me some success with sound, but it behaves exactly the same as the 2.6.32.32 kernel. Sometimes there's sound, other times there's not, while other times I only get one channel of audio.

The next thing I'm planning on trying is downloading the driver source and compiling it myself, unless anybody has any suggestions on what I can do. For now I've taken the card and am using onboard intel hd sound (which I think sounds better on ubuntu than it does on windows) but I miss the extra bass and high ranges that I get on my VT1723 card.

The card itself has a sticker on the back that says "ENM232-8VIA" and google pointed me to a thread somewhere on here about the same card, but the OP stopped replying in that thread.

Help is appreciated :)[FONT=monospace]
[/FONT]

---

### Post by PIDGINZ on 2011-08-05
Bump. I'm really losing hope with this forum.

---

### Post by PIDGINZ on 2011-08-07
Some more googling lead me to this very old bug: [https://bugs.launchpad.net/ubuntu/+bug/627038](https://bugs.launchpad.net/ubuntu/+bug/627038)

But it was useful: sudo /sbin/alsa force-reload worked in getting my sound back [IMG]http://www.overclock.net/images/smilies/biggrin.gif[/IMG]

I do wonder why this happens, that a simple reload of all the modules can fix it. Now how do I fix this permanently? I could make a script to execute that every time I start my PC up, but it'd be better if I could fix the cause of the problem.

---

### Post by lethalfang on 2012-12-23
Anyone with anything new on this issue? I'm running into the same problem, and can fix it with "sudo /sbin/alsa force-reload" command at the start of every boot.

---

