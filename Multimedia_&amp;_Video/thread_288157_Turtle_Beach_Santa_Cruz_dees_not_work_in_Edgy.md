---
title: "Turtle Beach Santa Cruz dees not work in Edgy"
date: 2006-10-29
forum: Multimedia &amp; Video
---

### Post by musicinmybrain on 2006-10-29
I have a Turtle Beach Santa Cruz sound card that uses the CS46xx driver. It worked perfectly in Hoary, Breezy, and Dapper. In a fresh install of Edgy, I get no sound. Master and PCM are unmuted in alsamixer, and external amplifier is muted. The snd-cs46xx module is loaded. If I turn up the PCM volume and the headphone volume to the max, I hear a hiss in the headphones, so the volume control is doing *something*.

This is a critical problem for me, as bad as no Internet access, for example. I will downgrade to Dapper as soon as I get a chance if I can't straighten out this problem, which is a huge disappointment since Edgy is otherwise faster and better for me.

Does anybody have any ideas? I'm desperate here.

P.S. I do hear the "ding" during boot... I just can't produce any sounds after I boot and log in.

---

### Post by musicinmybrain on 2006-10-30
Here's an update: The sound works from the live cd, so there's apparently some sort of configuration problem. Any ideas? This is a clean install with a preexisting home directory. Sound doesn't work when I boot to a recovery console either; I assume that since I'm working as root in the recovery console and sound still doesn't work, the settings in /home/username/ are ruled out as a factor.

---

### Post by musicinmybrain on 2006-11-02
So it seems that "external amplifier" has to be UN-muted. Odd. I thought I had tried that.

---

### Post by citizenkeith on 2006-11-04
I have this card, but I can't get any input via the Line Input. I'm trying to record off my stereo amp with Audacity. I'm using Alsamixer and the input isn't muted.

This setup works great in Windows, but so far no luck with Edgy.

---

### Post by musicinmybrain on 2006-11-20
> **citizenkeith said:**
> I have this card, but I can't get any input via the Line Input. I'm trying to record off my stereo amp with Audacity. I'm using Alsamixer and the input isn't muted.

This setup works great in Windows, but so far no luck with Edgy.

I tried to get recording working on either Breezy or Dapper and had no luck. Haven't tried it on Edgy; if I get around to it, I'll try to remember to post results here.

---

### Post by musicinmybrain on 2007-03-03
[Still no luck on Edgy.]("http://ubuntuforums.org/showthread.php?t=255071&page=2")

---

### Post by musicinmybrain on 2007-04-28
[http://ubuntuforums.org/showthread.php?t=255071&page=3]("http://ubuntuforums.org/showthread.php?t=255071&page=3")

---

