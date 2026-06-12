---
title: "mplayer SSA/*** weird bug"
date: 2007-07-09
forum: Multimedia &amp; Video
---

### Post by lbelloq on 2007-07-09
Gentlemen:

I recently installed mplayer with Synaptic and works great. With the w32codecs package even better.
My problem is, the default configuration doesn't enable support for SSA/*** styled subs.
I edited ~.mplayer/config and added "***=1" and "sid=0", and each time I open a Matroska video with SSA/*** styled subs, it gives me an error saying "Couldn't load *** filter" but the styled subs are displayed correctly.
If I remove the "***=1" line, the error disappears, but it doesn't show the styles and such.
What can I do to fix this problem?

Thanks in advance.

Léster

P.D.: By the way, the asterisks are the word blocker's fault. It's supposed to say A_S_S (without the underscores); Advanced Substation Subtitle format.

---

### Post by Gremlinzzz on 2007-07-09
Maybe give smplayer a try 
[http://smplayer.sourceforge.net/linux/index_en.php](http://smplayer.sourceforge.net/linux/index_en.php)

---

### Post by shirilover on 2007-07-10
this is the section in my ~/.mplayer/config I use for stylized subs
```

## Enable stylized fonts

embeddedfonts=yes

***=yes

```
I tend not to use the sid switch, but rather use 'j' to cycle through the available subtitle streams.

Also, smplayer is just a Qt frontend to mplayer. It even states so on the website.

Note: if you also installed the mplayer gui, SSA subtitle support can be enabled from the preferences dialog.

---

