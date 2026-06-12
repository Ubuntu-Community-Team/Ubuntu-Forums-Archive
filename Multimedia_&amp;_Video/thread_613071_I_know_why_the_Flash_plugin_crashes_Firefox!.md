---
title: "I know why the Flash plugin crashes Firefox!"
date: 2007-11-14
forum: Multimedia &amp; Video
---

### Post by sgarman on 2007-11-14
Like many people here, I have experienced the problem of the Flash plugin causing Firefox/Epiphany/Mozilla to hang and have to be force-quit. Spending any time on YouTube is just a gambling session where I have a 1 in 4 chance of encountering a crash every time I watch a Flash video, it seems. I've encountered this problem ever since Adobe released the Flash 9 plugin and have experienced this annoying problem to this day with Ubuntu Edgy, Feisty, and Gusty. 

Forgive me for sounding so excited about this, but I am certain I know the cause of the crashing now. It's hardware-related, folks! Specifically, it's due to the sound card you're using.

I have a Sony laptop that for some strange reason never encountered this problem, but my work and home desktop systems have always had it. That was my first clue. But then on my home desktop system I decided to unplug my SB Live! external USB sound card and use my motherboard's sound card for a few days. Now the crashes have stopped!

Yes, I have switched back to the USB sound card, and confirmed the crashes happen again. 

Given this information, it would probably be a good idea to create a list of sound cards that don't cause this problem, and ones that do. Because now I want to get a new sound card for my work desktop system and I'm not sure what to buy. Currently it's using a PCI Sound Blaster Live! (a very common sound card, I might add). 

Can anyone confirm or contradict my findings? Should we start a page on the Ubuntu wiki with this proposed list?

Scott

---

### Post by kerry_s on 2007-11-14
make sure your /usr/lib/flashplugin-nonfree are both executable.
make sure your /etc/firefox/firefoxrc has " aoss " instead of auto, so it use the correct sound output.
make sure you have alsa-oss installed.

---

### Post by eevargas on 2007-11-14
I don't know. I think the problem is with YouTube ( an a few others) because i don't remember have crashes with Metacafe, for instance or any other flash web applet. I think if the way they compile the videos into the flash applet. Maybe it have to do with the audio driver, but it is a YouTube specific problem ( and a few others, probably using flash the same way).

---

### Post by sgarman on 2007-11-14
> **kerry_s said:**
> make sure your /usr/lib/flashplugin-nonfree are both executable.
make sure your /etc/firefox/firefoxrc has " aoss " instead of auto, so it use the correct sound output.
make sure you have alsa-oss installed.

It's true, I've seen these suggestions elsewhere. I will try them with my USB sound card now.

**ls -al /usr/lib/flashplugin-nonfree/libflashplayer.so**:

```
-rw-r--r-- 1 root root 7040036 2007-11-11 21:03 /usr/lib/flashplugin-nonfree/libflashplayer.so
```

**cat /etc/firefox/firefoxrc **:

```
# which /dev/dsp wrapper to use
FIREFOX_DSP="aoss"
# Note that "auto" and "esd" involve the use of esddsp, which
# is known to be buggy and to make Firefox unstable.
# See https://launchpad.net/bugs/29760.
```

**dpkg --list | grep alsa-oss**:

```
ii  alsa-oss                                   1.0.14-1ubuntu1                           ALSA wrapper for OSS applications
```

**Result:** On my third playback of a YouTube video, I experienced the crash while using my USB sound card. 

It's a shame I can't use that thing, because I definitely notice some hum/hiss while using the internal sound card. But being able to use Firefox without fear of crashing is more important to me. 

Scott

---

### Post by kerry_s on 2007-11-14
then i would say yours is definitely a hardware issue.
i can run several flash sites and watch flash vids at the same time. i have pandora, meebo, and youtube going at the same time.

vaio-pcg-f430
450mhz
256ram

---

### Post by johnwillyums on 2007-11-14
Hi. I seem to have found a solution by accident.
I installed Swiftweasel (32 bit) on my Gutsy 64x system and it runs perfectly and very fast. 
 I have had no problem with any of the flash sites and no crashes at all.
It also seems to be able to use all the firefox themes and addons so I'm going to stick with it until something better comes along.
In Vista 64x (dual boot) I use Opera but I can't seem to get it in Gutsy.
I'm a complete newbie in both so, as I say, this was an accidental discovery but it works great.

John Williams

---

### Post by sir-nix on 2008-01-06
im not sure if mine is the same problem but i can watch flash streams sometimes and then other times it will randomly fade out and become unresponsive, need to use kys gard to close it. 

I'm using the onbord sound on my GA965p-s3 mb any one have any ideas?

after this happens when i restart firefox and attempt to view a vid it will sometimes just close it's self without warning

and i end up booting into xp out of frustration

---

### Post by MethosCR on 2008-01-06
I have a PCI SoundBlaster Live! and I haven't experimented any problem (but I've only watched a couple of YouTube videos). I'll keep you posted if there are any changes.

---

