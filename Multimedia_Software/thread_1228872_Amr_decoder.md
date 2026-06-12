---
title: "Amr decoder"
date: 2009-08-01
forum: Multimedia Software
---

### Post by praveesh on 2009-08-01
Which package should I install to get amr playback (amr decoder). Iam installing in a computer without internet connection . So I can't use synaptic. Need to download .deb file manually. Thanks in advance.

---

### Post by vinutux on 2009-08-01
The only player capable of playing amr (.3gp files) for me is Realplayer

download deb from here..**[www.real.com/linux/]("www.real.com/linux/")** But onlu 32 bit version no native version for 64...so use [COLOR="Red"]dpkg --force--architecture [/COLOR] cammand in terminal

---

### Post by praveesh on 2009-08-01
> **vinutux said:**
> The only player capable of playing amr (.3gp files) for me is Realplayer

download deb from here..**[www.real.com/linux/]("www.real.com/linux/")** But onlu 32 bit version no native version for 64...so use [COLOR="Red"]dpkg --force--architecture [/COLOR] cammand in terminal

Thanks . But I am able to play 3gp files in totem . But no sound. It tells me to install amr decoder.  Thats why I have asked.Is there any decoder/plugin for gstreamer or anything like that. For vcd I had installed gstreamer0.10-plugins-bad . Anything like that?.

---

### Post by mc4man on 2009-08-02
There are many threads in this forum about 3gp (an advanced search in the Multimedia & Video forum should provide a lot.

What I've found is in this post
[http://ubuntuforums.org/showthread.php?p=7682868#post7682868](http://ubuntuforums.org/showthread.php?p=7682868#post7682868)

(( gstreamer apps **no**, a medibuntu, ppa, or built mplayer is your easiest path, vlc with some work, xine players with some possible add. work.

There may be a possibility in karmic or beyond that gstreamer will support the open source amr libs

---

### Post by vinutux on 2009-08-02
> **praveesh said:**
> Thanks . But I am able to play 3gp files in totem . But no sound. It tells me to install amr decoder.  Thats why I have asked.Is there any decoder/plugin for gstreamer or anything like that. For vcd I had installed gstreamer0.10-plugins-bad . Anything like that?.

the 3gp video is fine in vlc,xine,totem,totem-xine,Dragon...etc but realpalyer is the only app able to play amr....othervice you want to compile...ffmpeg,mpalyer [not recommended for newbies].....

---

### Post by andrew.46 on 2009-08-02
Hi vintux,

> **vinutux said:**
> realpalyer is the only app able to play amr....othervice you want to compile...ffmpeg,mpalyer [not recommended for newbies].....

I believe that the Medibuntu MPlayer will in fact play files containing amr sound. This is true for Jaunty Jackalope and earlier, Medibuntu does not have an MPlayer build for Karmic Koala at the moment.

Andrew

---

