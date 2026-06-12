---
title: "Banshee and volume issues"
date: 2012-01-30
forum: Multimedia Software
---

### Post by Odexios on 2012-01-30
Hello!

I recently switched to lubuntu, and found it perfect for my needs in almost everything but sound and music management.

I have a quite large music library, and audacious isn't really working for me in managing it; I tried to install banshee, but I have a weird issue. When I try to play song, banshee somehow fails, and skips to the next one; it goes on like this, until it has cycled through all the library. I tried to start banshee with the --debug option, but it didn't give me any specific error message to look for.

If it can be of any help, using mocp music reproduction is fine, so it's an issue specific to banshee.

Besides problems with banshee, I have a kind of a deal-breaker issue with the volume; in ubuntu, I could easily boost the volume up beyond 100%, which was perfect for my wrecked netbook speakers. In lubuntu I didn't find any way to do the same thing, so I'm stuck with my headphones; I can survive without banshee, but if I don't find a way to solve the volume issue I'll be forced to switch back to ubuntu, and I kinda like the current speed and performance of my pc.

---

### Post by nothingspecial on 2012-01-30
Hi, not to sure about banshee but you might need the gstreamer alsa plugin to run it in lubuntu

```
sudo apt-get install gstreamer0.10-alsa
```

---

### Post by Odexios on 2012-01-30
> **nothingspecial said:**
> Hi, not to sure about banshee but you might need the gstreamer alsa plugin to run it in lubuntu

```
sudo apt-get install gstreamer0.10-alsa
```
Thanks, it worked like a charm!

Any idea for the 100%-volume-cap thing?

---

### Post by Odexios on 2012-01-30
Let's try with a bump.

---

### Post by Rodney9 on 2012-01-31
Install pavucontrol and padevchooser, they will help you control pulse sound.

alsamixer is always worth checking first, run in the terminal and check the levels.

For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by MoreOrLess on 2012-01-31
I thought lubuntu came without pulseaudio by default..?

---

