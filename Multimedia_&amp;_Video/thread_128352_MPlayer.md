---
title: "MPlayer"
date: 2006-02-11
forum: Multimedia &amp; Video
---

### Post by xmenu43 on 2006-02-11
I have been trying to find a video player for movies, etc...
Has anyone ben successful with this, and if so, what did you get to work, Real, Mplayer or Totem?

I found that Mplayer requires GCC 3.0 or better. (not wanting to install that myself).

---

### Post by bluevoodoo1 on 2006-02-11
I usually use xine. Vlc is another alternative. Both are available with Synaptic. Xine I believe is called "xine-ui" and vlc is simply "vlc" I don't know what GCC they require, but for me, mplayer has always been a pain.

---

### Post by xmenu43 on 2006-02-11
:) Thanks, xine works, although it is a little jumpy in play mode, although the lead ins are smooth. Must be a setting I need to adjust.
At any rate, I now have video on ubuntu... thanks again.

---

### Post by bluevoodoo1 on 2006-02-11
[QUOTE=xmenu43]:) Thanks, xine works, although it is a little jumpy in play mode, although the lead ins are smooth. Must be a setting I need to adjust.
At any rate, I now have video on ubuntu... thanks again.[/QUOTE]

Is it jumpy while watching a DVD?

---

### Post by xmenu43 on 2006-02-13
Yes, DVD play is jumpy. I tried installing libdvdcss2   but it didn't help.

---

### Post by bluevoodoo1 on 2006-02-13
[QUOTE=xmenu43]Yes, DVD play is jumpy. I tried installing libdvdcss2   but it didn't help.[/QUOTE]

That might be a DMA problem. You can find a lot of info about that about here... just search titles for "DMA" 

you can see if you have it enabled by typing...

```

sudo hdparm /dev/cdrom

```

this link might be useful... [http://doc.gwos.org/index.php/DMA](http://doc.gwos.org/index.php/DMA)

---

