---
title: "HDTV playback jerky / choppy 720p Gutsy"
date: 2007-11-10
forum: Multimedia &amp; Video
---

### Post by webjames on 2007-11-10
Hello Ubuntuers,
Yesterday i purchased a HDTV and installed ubuntu onto my computer:
P4 3.2 Ghz HT
512 ram
nvidia 6600le using restricted drivers:

> james@james-desktop:~$ glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: GeForce 6600 LE/PCI/SSE2
    GL_NVX_conditional_render, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod, 


The problem i am having is jerky or choppy HD video playback. i downloaded a movie trailer in 720p, a Matroska video file, and it is really jerky. any idea what the problem could be? i'm not sure if my computer is not good enough, or i need more memory?

many thanks!

James

**UPDATE**
Just booted into windows 2000 and playback is fine! so is not a hardware issue.

---

### Post by disturbed1 on 2007-11-10
Your specs might be fine. I play 1080P with out issues on the system in my sig. 720P plays fine using an AMD Sempron 3000+ 1gig RAM, nVidia fx5500.

512mb of RAM is on the low side, it might be enough, but more is better.

Do you have desktop effects enabled? Disable them.

Use mplayer to play back the video using the xv output option. Right click on the open mplayer window, choose preferences, then the video tab. I use both xv and gl for video output. xv does seem to be better/less resources.

---

### Post by webjames on 2007-11-10
thanks for your reply. i have no video tab on my movie player preferences, however turning off desktop effects di make a difference. but it's still jerky, whereas it's fine is win2000.
i wonder if it's to do with the hyper threading, when i open system monitor my core1 is at 100% but the other nothing, however i don't have two cores, just p4 with hyper threading. maybe ubuntu is confused about my processor?

is this possible?

James :)

---

### Post by disturbed1 on 2007-11-10
Hyper threading is seen as 2 cores. This is what hyper threading is. [http://en.wikipedia.org/wiki/Hyper-threading](http://en.wikipedia.org/wiki/Hyper-threading)

I never said anything about your movie player, mplayer is an actual program that plays back movies. I take it you're attempting to play the file with Totem.

Install mplayer.

---

### Post by webjames on 2007-11-11
well i turned hyper threading off so now i have one CPU core, totem is still jerky. however mplayer works perfectly, i was getting some errors which were sorted by enabling the software mixer. so many thanks for the suggestion!

---

### Post by disturbed1 on 2007-11-11
:guitar:

Glad you got everything sorted.

---

### Post by sparkov on 2007-11-29
Switching desktop effects off did the trick for me, playback is now very smooth - I'm sure I can live without fading windows.  Cheers guys.

---

### Post by mirzmaster on 2007-12-30
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/162343](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/162343) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **webjames said:**
> well i turned hyper threading off so now i have one CPU core, totem is still jerky. however mplayer works perfectly, i was getting some errors which were sorted by enabling the software mixer. so many thanks for the suggestion!

The slow HD video playback in totem is apparently a known issue.  Take a look at this thread:

[http://ubuntuforums.org/showthread.php?t=603585](http://ubuntuforums.org/showthread.php?t=603585)

---

### Post by yemu on 2008-01-07
i also suffer from choppy hd 720p playback, also the synchronization between audio and video is lost. my system specs are amd barton @2100MHz and 190FSB, 768 MB RAM. nvidia card with nv or nvidia driver (effects almost the same)
during playing i watched usage of CPU  in top, and it was about 75-95% when using mplayer, and 80MB of RAM were free. 
any ideas?
y

---

### Post by yemu on 2008-01-10
all issues with choppy playback are gone with the newest nvidia drivers 169.something. i installed them manually and mplayer playback is completly smooth and video and audio are in sync. it means that drivers supplied by restricted driver manager in gutsy are broken, at least for my fx5600 card.
best regards
y

---

