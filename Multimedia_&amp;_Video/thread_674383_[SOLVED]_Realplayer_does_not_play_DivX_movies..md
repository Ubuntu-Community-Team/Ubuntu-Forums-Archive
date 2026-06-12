---
title: "[SOLVED] Realplayer does not play DivX movies."
date: 2008-01-21
forum: Multimedia &amp; Video
---

### Post by Fraser from Scotland on 2008-01-21
I followed this guide [http://ubuntuforums.org/showthread.php?t=661833&highlight=DivX](http://ubuntuforums.org/showthread.php?t=661833&highlight=DivX)
and it all worked great but... realplayer won't play DivX files, which is my main filetype. And I have just checked another website and it does not seem to be playing any kind of filetype :( Any help? I don't know what to do or how to fix this! There is a screenshot of what comes up at the bottom; I have tried looking for updates but it says I'm upto date, also It's any kind of file not just DivX or avi.

EDIT: here is another screenie of what I get if I try to stream from the internet.

---

### Post by Fraser from Scotland on 2008-01-21
Argh! I really really want this to work, if it does It's one more thing I won't have to depend on windows for!! 1 step closer to removing that XP partition!

---

### Post by wolfen69 on 2008-01-21
did you install the gstreamer ffmpeg codecs?

---

### Post by Fraser from Scotland on 2008-01-21
yeah i did :/

---

### Post by Fraser from Scotland on 2008-01-21
it still says it needs the components and the component is whatever filetype i try to play.

---

### Post by Fraser from Scotland on 2008-01-21
bump :( :( :(

---

### Post by joshuachad on 2008-01-21
Dude dont use RealPlayer it sucks anyway. Use Mplayer. It plays Divx great!  Also quit being such a noob and bumbing posts after 17 mins. Also google is your friend. So if you must use RealPlayer here you go.If that doesnt work keep googling. Youll learn more that way. And then you can come here and help other folks. Pretty cool eh?

[http://www.cyberciti.biz/tips/linux-play-divx-mpeg4-video-stream-files.html](http://www.cyberciti.biz/tips/linux-play-divx-mpeg4-video-stream-files.html)

---

### Post by Fraser from Scotland on 2008-01-21
Yeah but I wanted it to be able to stream from the internet, like without using my browser just taking the link then loading it then watching on my desktop.

---

### Post by Fraser from Scotland on 2008-01-21
I treid "play url" in mplayer and it said couldnt resolve name for AF_INET6:joox.net

---

### Post by ron999 on 2008-01-21
ditto @ joshuachad

I have RealPlayer installed. But I only use it for such things as BBC radio.
There's nothing wrong with my RealPlayer but if I try to play an avi file I get the same result as you.

When I watch those divx/avi files I use VLC player - that's the best.
And sometimes I use Totem.

---

### Post by ron999 on 2008-01-21
> **Fraser from Scotland said:**
> Yeah but I wanted it to be able to stream from the internet, like without using my browser just taking the link then loading it then watching on my desktop.

Yes, you can do that by copying and pasting the link.
But that's different to playing divx files from your hard drive.

---

### Post by joshuachad on 2008-01-21
Thats because you should tell mplayer not to use IP V6. I guess you still dont like google. Anyway stick this in your mplayer config. 

prefer-ipv4 = yes

Dont ask where it is just google it.

---

### Post by joshuachad on 2008-01-21
I just realized by looking at your screen shot that the link you are copying into RealPlayer is an html file. So you might want to check your links

---

### Post by Fraser from Scotland on 2008-01-21
yeah im using vlc now. Thanks for the replies.

---

