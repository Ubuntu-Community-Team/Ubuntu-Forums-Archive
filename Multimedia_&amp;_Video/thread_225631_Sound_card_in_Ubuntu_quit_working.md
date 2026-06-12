---
title: "Sound card in Ubuntu quit working"
date: 2006-07-30
forum: Multimedia &amp; Video
---

### Post by grapnell on 2006-07-30
Hi, 
I have just reinstalled dapper on my thinkpad laptop, and now I can't get sound to work.

If I go to a terminal, and type gnome-alsamixer, it shows that my sound card is recognized, and it lets me adjust the levels. and if do:
```

jeff@legend9:~$ cat /proc/asound/modules
0 snd_cs46xx

```

but if I try to play something with xmms, i get:
Could not open audio
Please check that:
Your sound card is configured properly,
You have the correct plugin selected,
No other program is blocking the soundcard

or if I try to use the volume control on the task bar I get:

The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

What gives?

---

