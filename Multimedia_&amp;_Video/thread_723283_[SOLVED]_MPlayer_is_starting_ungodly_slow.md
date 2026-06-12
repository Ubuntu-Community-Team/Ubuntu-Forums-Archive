---
title: "[SOLVED] MPlayer is starting ungodly slow"
date: 2008-03-13
forum: Multimedia &amp; Video
---

### Post by tenjin1 on 2008-03-13
I had MPlayer running fine for a long time but decided to uninstall recently and used a compiled version. So I uninstalled in Synaptic and downloaded the binary package from Mplayer download page. I then used the new compiled version fine for some time and realized I didn't like it and went back to the one in the repositories. Now everything is working fine except when I click on a video file to play it takes about 30 seconds to open and play. Around 20 seconds I can see the player come up and then about 10 seconds later the video screen window comes up and the video is playing fine. If I start Mplayer from commad line it starts instantly with no errors. Other video players work fine, vlc etc 

Not sure what is causing the problem. Don't know if it has something to do with compiling mplayer in the beginning that messed some file up somewhere? I also did a sudo make clean in the directory after I complied too.

---

### Post by tenjin1 on 2008-03-13
Ok I removed my /.mplayer settings.

Did a 
```
rm -R ~/.mplayer
```

and is starting instantly, must have been a bad config file from compliing, uninstalling, installing mplayer.

---

