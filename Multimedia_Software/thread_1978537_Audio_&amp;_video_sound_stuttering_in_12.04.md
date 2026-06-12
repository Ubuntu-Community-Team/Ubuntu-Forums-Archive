---
title: "Audio &amp; video sound stuttering in 12.04"
date: 2012-05-11
forum: Multimedia Software
---

### Post by andrewdied on 2012-05-11
In a new 64 bit install of ubuntu 12.04 I get randomly choppy / stuttered sound in videos like [http://watchtheguild.com](http://watchtheguild.com) and with ogg and mp3 sound playback. I only get the stuttering with the unity/gnome desktop, not if I log in with KDE. 

I've seen this with previous versions of ubuntu, so it's not necessarily a new issue with 12.04. I've uploaded my also info as a gzipped text file since I was 1k over the text file limit.

I used thi  script to generate the file: ```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh
```

UPDATE: In case it was 64 bit not being ready for prime-time, I removed it and installed 32 bit ubuntu 12.04. I get the same exact issue. I'm attaching the 32 bit alsa debug file, too.

---

### Post by RudyG on 2012-05-23
Do you have pulseaudio installed on your system?

Rudy

---

### Post by andrewdied on 2012-05-24
Yup. I'd tried disabling it based on some other posts, but all that did was make it so my laptop soft keys for sound didn't work -- sound was still stuttering.

---

### Post by RudyG on 2012-05-25
I'm not sure what you mean by "disabling" it. You pretty much have to uninstall pulseaudio to get rid of it. Nothing else works in my experience.

Rudy

---

### Post by LillyDragon on 2012-05-25
Maybe this problem is similar to that adityeah was having a while ago? My sound through alsa was stuttering almost like his, and his fix did the trick for me. (Still no sound from the internal speakers on my laptop, but at least I can get consistent sound from my headphone jack all the time, instead of sometimes!)

[http://ubuntuforums.org/showthread.php?t=1979191](http://ubuntuforums.org/showthread.php?t=1979191)

---

### Post by andrewdied on 2012-05-27
> **RudyG said:**
> I'm not sure what you mean by "disabling" it. You pretty much have to uninstall pulseaudio to get rid of it. Nothing else works in my experience.

Rudy

I followed the steps from this post: [http://ubuntuforums.org/showthread.php?t=1471262&page=4](http://ubuntuforums.org/showthread.php?t=1471262&page=4)

What happened was I lost my soft keys for managing sound (volume, etc.) and it still stuttered. Looks like I'm using 1:1.1-0ubuntu15 version of pulseaudio (apt-cache showpackage pulseaudio).

---

### Post by andrewdied on 2012-05-27
> **johnluke728 said:**
> Maybe this problem is similar to that adityeah was having a while ago? My sound through alsa was stuttering almost like his, and his fix did the trick for me. (Still no sound from the internal speakers on my laptop, but at least I can get consistent sound from my headphone jack all the time, instead of sometimes!)

[http://ubuntuforums.org/showthread.php?t=1979191](http://ubuntuforums.org/showthread.php?t=1979191)

Thanks for the link. I tried it, and it caused what showed in gnome alsa mixer to be completely blank -- no buttons to click, no options dropdowns. Blank like that it shows I have "Realtek ID 768". If I've left the modprobe file alone it shows "Realtek ALC268".

Any idea how I otherwise tweak what drivers it's using, or why kde would work and not gnome/unity?

---

### Post by ptomasiewicz on 2012-11-27
Hi. I have similar problems with my IBM T60 with: "Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)" 

Sound works fine on Unity 2d and other non compiz shells.
When I use Unity 3d sound stutter while watching full screen movies in mplayer or from youtube, listenning to music on banshee an switching appilcation windows.

Trick with changing settings in /ets/modprobe.d/alsa-base.conf does not work.
Now I have:
snd-hda-intel model=thinkpad (sound stutter)
I also tried:
snd-hda-intel model=basic (sound works but still stutter)
and
options snd-hda-intel model=generic (sound does not work at all)

---

