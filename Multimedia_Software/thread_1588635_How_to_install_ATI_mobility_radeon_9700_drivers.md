---
title: "How to install ATI mobility radeon 9700 drivers"
date: 2010-10-05
forum: Multimedia Software
---

### Post by Mortesins93 on 2010-10-05
Hello,
I have a Xubuntu 9.10 which works pretty fine, the only problem I have is watching videos through VLC or mplayer. If I try watching a video I get a black screen instead of the video, even though the sound works. The only way I can see something is by using Avidemux. If I try opening the file with mplayer I get this "Error opening/initializing the selected video_out (vo) device." If I try typing "mplayer -vo gl movie.avi" in the terminal the video works, why? What does the option "-vo gl" do? 
Another problem I have is playing, through wine, some Windows games. If I try launching a game through wine I get a black screen even though I can hear the game working. Then if I press Alt+F1 I can see the tty1 and after typing "sudo pkill wine" I can go back to the desktop environment. 
Could installing the video card drivers help? How do I do it? I tried going to Applications>System>Hardware Drivers but nothing shows up.
Thanks in advance.
I hope you can help me.

---

### Post by Mark Phelps on 2010-10-05
There are no current AMD proprietary drivers that will work with your card and current versions of Ubuntu.  AMD (formerly, ATI) dropped proprietary driver support for your card a long time ago.

The only working drivers now are the open-source drivers and they are installed by default during initial setup.

So basically, you already have the only working drivers installed.

---

### Post by Mortesins93 on 2010-10-06
Ok, thank you very much. So my problem isn't the video card drivers. Have you got a clue on what I try to do to solve it?

---

### Post by Mark Phelps on 2010-10-07
Can't help you with Wine.  Don't use it.  Found it to be a waste of time when I tried it a while back.

As to the black screen, that generally means you're missing a video codec.  Have you installed ubuntu-restricted-extras ?

---

### Post by Mortesins93 on 2010-10-07
No, I'll try that, but why would Avidemux show me the video just fine if I am missing a codec?

---

