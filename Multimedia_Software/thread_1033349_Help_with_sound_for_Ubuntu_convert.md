---
title: "Help with sound for Ubuntu convert"
date: 2009-01-07
forum: Multimedia Software
---

### Post by pramsay13 on 2009-01-07
My windows vista crashed so rather than fart about getting it sorted I tried out Ubuntu, and I liked it so much that I have installed it and scrapped Windows once and for all.
Everything works great and anything that doesn't I normally find a quick-fix for it. Only problem I have is with the sound, and I've followed a lot of the fixes online, but I think most of them are machine specific so I've mucked everything up.
Recently I've changed from ALSA to OSS which is helping somewhat but I'm not totally happy so any help would be appreciated.
The reason I started mucking about with it was that none of the movie players I had (totem, vlc, banshee) would play sound for my movie files (mostly .mp4s or DVDs). In trying to sort it I mucked up all sound completely.
Since changing to OSS I can play .mp4s and DVDs and .mp3s etc in VLC player. When I try to play anything in totem (which is still the default) or banshee these programs freeze and turn gray and I have to force quit.
I don't mind using VLC for videos but I'm wanting something else for music to use with my ipod (banshee seems a good one). Sound does work on seamonkey and firefox but doesn't work on BBCi player desktop version.
I don't mind sticking with OSS if I can get these things working or going back to ALSA.
My laptop is acer aspire 5720. (sound wheel now doesn't work at all although worked originally)
My audio device is Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03) 
I can get any other info that is needed.
Thanks for the help.

---

### Post by namdung on 2009-01-07
This seems to be ur 1st post here and we'll definitely try to resolve ur issue.

In terminal
```
less /proc/asound/card0/pcm0p/info
```

Check *subdevices_avail*, it if's zero it means that ur sound card is captured by some other device. Stop any other devices and try again.

In *System==>Pref==>Sound*, ensure that **Master** is selected for *Default Mixer Tracks==>ALSA Mixer* for ur sound wheel to work.

Try this for multiple sound solution:
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by pramsay13 on 2009-01-07
Hi there, this is indeed my first post, as I've found that for most issues a solution can be found online. Sound issues seem to be specific to machines however so there is not a one-size fits all solution. 
When I type the above code in I get No Such File or Directory.
I don't have an asound directory.
"In System==>Pref==>Sound, ensure that Master is selected for Default Mixer Tracks==>ALSA Mixer for ur sound wheel to work."
I don't have ALSA mixer option in Default Mixer Tracks, I've only got an OSS mixer and an OSS v4 mixer option. This will be because I disabled the ALSA mixer when things were not going well.
I'm happy using either OSS or ALSA but I'll need to re-instate ALSA if it's better for my machine.
Thanks

---

