---
title: "Mplayer fatal error"
date: 2007-01-10
forum: Multimedia &amp; Video
---

### Post by Redeyes_Gambit on 2007-01-10
}{i,

I recently re-installed ubuntu and Mplayer and have been having some problems getting Mplayer back up to a functional state. Every time I try to play a movie in Mplayer I get a "Fatal error!" window that states:

"Error opening/initializing the selected video_out (-vo) device."

VLC media player is working and playing the same files I'm trying to get working in Mplayer but it's a no-go in Mplayer.

Any ideas?

---

### Post by taurus on 2007-01-10
Look in ~/.mplayer/gui.conf to see which video driver you use for video_out!  If it uses "xv", then change it to "x11" but if it uses "x11", then change it to "xv".  Then start gmplayer again from a terminal.

Applications -> Accessories -> Terminal
```
gedit ~/.mplayer/gui.conf
gmplayer
```

---

### Post by Redeyes_Gambit on 2007-01-11
No joy sadly. The default setting was xmga which I changed to both X11 and xv (one at a time of course.) Using x11 or xv the error now reads:

"cannot find codec matching selected -vo and video format 0x33564D57"

Though I DO have audio now.

Just a little more info, the movie file I am trying to play is a .wmv (not encrypted/ DRMed) which I am pretty sure I have played in Mplayer before I re-installed Ubuntu. I am also using Beryl however the video will not play when I am using metacity either.

I followed the guide located at [http://doc.gwos.org/index.php/BerylOnEdgy#Intel](http://doc.gwos.org/index.php/BerylOnEdgy#Intel) for installing beryl with my Intel integrated graphics chip. One thing of note, I did put a "tab" indent before the "option" lines specified in the guide for my X11 config because I notices that every other "option" line in the file had a tab before it and figured the guide had omitted it. Beryl runs fine so I assumed this was not the culprit. Was I incorrect in putting an indent before the "option" line? I have included my X11.conf file just in case.

---

### Post by taurus on 2007-01-11
Did you remember to reinstall codecs after you installed Ubuntu again?

---

### Post by Redeyes_Gambit on 2007-01-11
Re-installed all but "ugly." Let me jump on synaptic and grab that... Just a question, but should I go with the "multiverse" variant of the gstreamer plugins or standard?

---

### Post by Redeyes_Gambit on 2007-01-11
Still no joy with the "ugly" gstreamer plugin installed.

---

### Post by taurus on 2007-01-11
What if you install automatix2 and use it to install the codecs and mplayer (and other media players) for your machine?

[http://www.getautomatix.com](http://www.getautomatix.com)

---

### Post by Redeyes_Gambit on 2007-01-11
AHA!!!

... No. Still nada :P . Same errors on X11, XV and xmga.

---

### Post by taurus on 2007-01-11
How did you install mplayer anyway?

---

### Post by Redeyes_Gambit on 2007-01-12
Through synaptic.

---

### Post by taurus on 2007-01-12
Remove it with synaptic and try the version from automatix2!

---

### Post by Redeyes_Gambit on 2007-01-12
Mmm... Nope. Same error.

---

### Post by Redeyes_Gambit on 2007-01-12
Hmm... Well I just tried a .mov video file in mplayer and I have video and audio, but I got another error stating "Requested audio codec family [mp3] (afm=mp3lib) not available. Enable it at compilation." If I close the error box the movie keeps on playing, but if I pause it and hit play again the error pops back up.

So .movs sorta work... WMVs not so much. The WMV WILL play in VLC however....

Odd.

---

### Post by Redeyes_Gambit on 2007-01-12
DOH! Problem found. Didn't have w32/libdvdcss installed. Mplayer playing now. Sorry for wasting your time! On to new issues and a new thread...

---

