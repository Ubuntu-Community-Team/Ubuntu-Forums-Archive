---
title: "problems with streaming radio .aspx"
date: 2010-02-15
forum: Multimedia Software
---

### Post by Yohai on 2010-02-15
Salut!

I have problems with streaming a radio station ([http://glz.co.il/Audio_galaz.aspx](http://glz.co.il/Audio_galaz.aspx)). It's not working directly on firefox, and I can't get it to stream through VLC or Amrok. 

Is there something special that I need to install?

Thanks.

---

### Post by BASH-full on 2010-02-15
The clue for me is the .aspx file extension on the page you're trying to open.  ASP is a M$-specific format for form pages.  It doesn't work on Linux.  There is a solution, however.  Install IE7 and use that to open the .aspx page.  PlayOnLinux is a program that allows you to install IE on Ubuntu.

Open your terminal and copy/paste the following commands:

```
sudo wget http://deb.playonlinux.com/playonlinux_karmic.list -O  /etc/apt/sources.list.d/playonlinux.list
```

After that finishes:

```
sudo apt-get update
```

And finally:

```
sudo apt-get install playonlinux
```

Type "y" at the " y/n?" prompt and close the terminal after the process completes.  Start PlayOnLinux from Applications>Games and follow the instructions for installing IE.

You *should *be able to open the streaming page from within IE but it's not guaranteed.:(

Good luck...

---

### Post by Yohai on 2010-02-15
thanks a bunch!

---

### Post by mc4man on 2010-02-15
> ASP is a M$-specific format for form pages. It doesn't work on Linux
In most cases that shouldn't matter, I think the posted url was slightly wrong, this may be what it should be
```
http://glz.co.il/media/glz.asx
```

Try anyplayer [http://glz.co.il/media/glz.asx](http://glz.co.il/media/glz.asx) - you'll get a short 'splash' audio and then the stream

May be easier to just  make a .m3u file to load into players using the mms (vlc, amarok, mplayer, totem,  ect.

```
#EXTM3U
#EXTINF:0,2 http://glz.co.il/media/glz.asx
mms://213.8.138.13/glz-stream

```

---

