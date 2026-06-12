---
title: "GStreamer vs. Xine"
date: 2007-06-11
forum: Multimedia &amp; Video
---

### Post by kombucha on 2007-06-11
I'm not even sure I'm using this terminology correctly, but here's my problem:
Music played with Rhythmbox is crackly and tends to skip a lot, while music played with Amarok is wonderfully flawless. I'm guessing the difference is between GStreamer and Xine engines? Again, that's just a stab in the dark from a relatively new Linux user. When I switch between OSS and ALSA and the like, I don't notice any difference within Rhythmbox. Is there any way I can fix the GStreamer plugin, if that truly is the culprit? I'm just used to Rhythombox, and I'd prefer to stay with it.
Thanks!

---

### Post by kevinlyfellow on 2007-06-11
If its gstreamer specifically, you'll also have a problem with playing music on totem.

---

### Post by trippinnik on 2007-06-11
I haven't really noticed this with MP3s but with video if I use totem-xine instead I get much smoother video compared to gstreamer or even Mplayer.

---

### Post by robertmf on 2007-08-21
Using Totem, how do I change from xine to gsteamer ?  

(Not having any success at playing mpeg nor .avi)

Thanks in advance :)

---

### Post by racoq on 2007-08-21
> **robertmf said:**
> Using Totem, how do I change from xine to gsteamer ?  

(Not having any success at playing mpeg nor .avi)

Thanks in advance :)

install the totem-xine package, it will remove totem-gstreamer package, and install that one.

---

### Post by ausmuso on 2007-08-21
I've also had problems with GStreamer.
I then installed Totem-Xine, which automatically remover Totem GStreamer and multimedia life has been bliss ever since.
As ever, I've also got a complete set of codecs for the MPlayer-plugins.
Actually, I've never been able to figure out just what we need this GStreamer thing for. Multimedia life was quite OK before GStreamer came along.

---

### Post by robertmf on 2007-08-21
GStreamer no doubt has something to do with your Mr. Rudd visiting NYC :-P  Or maybe your Hansen should be your next PM ? **snicker** :lolflag:

---

### Post by robertmf on 2007-08-21
Right-O.  Works with xine, not with gstreamer.  Thanks.

---

### Post by sicofante on 2007-09-28
I have also had to remove Gstreamer in favour of Xiine to be able to fast forward DVDs properly in Totem. What's the benefit of Gstreamer? Why is it the one chosen by default?

---

### Post by robertmf on 2007-09-29
> **sicofante said:**
> I have also had to remove Gstreamer in favour of Xiine to be able to fast forward DVDs properly in Totem. 

What's the benefit of Gstreamer? 
Why is it the one chosen by default?

[COLOR="DarkRed"]I certainly hope you're not asking me ... I don't have enough **knowledge** to answer.  Perhaps a sound developer will read your queries;  I too am interested.

BTW Since I've installed Feisty I get no sound out  of SB EMU10K1 card whatsoever.  Which is another and well-posted-about  problemo with Feisty.
[/COLOR] :confused:

---

