---
title: "Codecs only working some of the time in Gutsy"
date: 2008-02-23
forum: Multimedia &amp; Video
---

### Post by will61 on 2008-02-23
I'm reasonably new to ubuntu I'm using gutsy gibbon 64bit at the moment >The problem I'm having is that video only works once in a while I have all the codecs needed for dvd playback and watching xvid format and most of the time everything works just fine without any probs but quite often it happens that I get a bunch of colored stripes instead of watchable video, I usually fix this by restarting the X server (ctrl+alt+backspace) any advice on this would be greatly appreciated

---

### Post by ioluas on 2008-02-23
ok, i had the same problem before. it turned out it wasn't the codecs fault. just a matter of how the player outputs the video.  i learnt that it is best to output to X11, it's fast and safe.  

so depending on which player you use, look to change that in the options/preferences dialogue. i use vlc, and to change it you go; Settings --> preferences --> (check advanced options on) on the left pane choose video --> Output modules --> change video output module to X11 video output.

this did the trick for me. hope this helps

---

### Post by will61 on 2008-02-23
I can't find that setting in totem player But I tried in mplayer and video playback fails in that too with the video set to X11

I also have the same problem in mythtv at times if I try to watch live tv the whole screen just turns pink and the computers locks up (hard lockup witch requires the power cord to be pulled to be able to start the pc again)

---

### Post by will61 on 2008-02-23
another thing that may be worth mentioning is,That if I watch live tv in mythtv I have no problems but if after that I try to watch video I just get colored stripes however if I watch video first and then try to watch live tv in mythtv after that it fails in short it seems which ever I use first (mythtv or totem,mplayer,...etc) what i use first works and what i use after that fails

---

### Post by will61 on 2008-02-24
does anyone have any suggestions???

---

