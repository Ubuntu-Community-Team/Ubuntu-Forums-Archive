---
title: "Amarok from SSH... or Shell-Based MP3"
date: 2007-08-02
forum: Multimedia &amp; Video
---

### Post by xMemphisx on 2007-08-02
Pretty much like the title states. I got an SSH client for my cell phone (which is REALLY nice), but i can't use commands like amarok --next or whatever, because it gives me problems with the x server. Is there a way around that? Or is there a good shell based mp3 player that i can control this way?

---

### Post by web_knows on 2007-08-06
Try executing this command:

```
DISPLAY=:0.0 amarok --next
```

At this moment I'm too sluggish to write down why you have to set the DISPLAY variable before the command himself. Be curious.

---

### Post by davem2312 on 2007-08-06
Ahh, neat.  Well I was trying to do the same from my laptop to an old server I had, but I have found some good software.  First, if your cellphone was really snazy... you could try

ssh -X <servername>

this forwards the x gui to the remote device.  However, I'm nearly positive this won't work.

But, for text based mp3 players, I have found mp3blaster and orpheus to be two of the best.  They allow full library and playlist support, all in text.

Here are some links.

[URL="http://mp3blaster.sourceforge.net/"]
http://mp3blaster.sourceforge.net/[/URL]
[URL="http://konst.org.ua/orpheus/"]
http://konst.org.ua/orpheus/[/URL]

---

### Post by xMemphisx on 2007-08-15
There's no 'terminal', so i can't forward the X server through SSH on my phone (it's a real bummer, it was actually one of the first things i tried :) ). Anyways, i ended up going with VLC, and it works really well via command line. Thanks a lot for your help guys.

---

