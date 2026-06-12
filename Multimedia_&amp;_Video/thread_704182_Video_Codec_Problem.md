---
title: "Video Codec Problem"
date: 2008-02-22
forum: Multimedia &amp; Video
---

### Post by nikhil bhat on 2008-02-22
Hi,
    I am an ubuntu beginner, I tried to get videos to play in ubuntu using the vlc player.The audio was fine but the video was almost non-existent.
     I then installed some codecs for video formats using:
             sudo apt-get install w32codecs libdvdcss2
It got installed but still the video was not playing.
        I then repeated the same process with mplayer and totem..still the same problem..
    Should i install any more codecs?
             Thanks..

---

### Post by cozmicharlie on 2008-02-22
I suggest you add the "Ubuntu Restricted Extras" [https://help.ubuntu.com/community/RestrictedFormats#head-e69e0c62de07b1e2b560c1ad6b68823328906067](https://help.ubuntu.com/community/RestrictedFormats#head-e69e0c62de07b1e2b560c1ad6b68823328906067)

Post back if it still does not work.

---

### Post by nikhil bhat on 2008-02-22
I installed the restricted formats..still the same problem....PLEASE HELP..

---

### Post by yabbies on 2008-02-22
what do you mean by non-existent?

---

### Post by nikhil bhat on 2008-02-22
well only some colored stripes is getting displayed ..but it is not the actual video..

---

### Post by nikhil bhat on 2008-02-22
I think the codecs are installed properly..there is some other problem..
is it a hardware related problem?

---

### Post by cozmicharlie on 2008-02-22
Agree - sounds like you have all the codecs.  

Try this in vlc:   click settings>preferences> video>output modules - click Advanced options (check box in bottom right) then try selecting a different output - x11 vid output is a safe bet.

---

### Post by nikhil bhat on 2008-02-23
THANKS!!! it is now working like a charm:)

---

### Post by cozmicharlie on 2008-02-23
great! - please mark the thread as solved.

---

