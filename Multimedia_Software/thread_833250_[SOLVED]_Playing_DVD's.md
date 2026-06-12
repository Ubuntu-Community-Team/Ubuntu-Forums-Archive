---
title: "[SOLVED] Playing DVD's"
date: 2008-06-18
forum: Multimedia Software
---

### Post by M4rotku on 2008-06-18
Hello all,

I have tried to play several DVD's on my laptop.  Whenever I try to open the DVD with Totem, it tells me:

> [SIZE="4"]An error occured[/SIZE]

Could not read from resource.

Is there any way I can install something that will allow me to read it?

I was able to watch DVD's back when I had Vista, but I don't want to have to boot into it just to watch a DVD b/c it will try to upgrade itself.

Much thanks,
M4rotku

---

### Post by Pjotr123 on 2008-06-18
Apply this:
[http://ubuntutip.googlepages.com/multimediaubuntustep2](http://ubuntutip.googlepages.com/multimediaubuntustep2)

That should take care of encrypted DVD's.

---

### Post by Fingers &amp; Thumbs on 2008-06-18
This is likely to be due to a lack of suitable codecs/libraries,

  Make sure you have universe enabled in software sources and look for a suitable gstreamer library in synaptic, or try this :- [http://ubuntu.wordpress.com/2005/12/04/libdvdcss2-and-w32codecs-for-ubuntu/](http://ubuntu.wordpress.com/2005/12/04/libdvdcss2-and-w32codecs-for-ubuntu/)

---

### Post by phoenix_abhi on 2008-06-18
View this everything u can find there

[m player and multimedia codec for dvd ]("http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-804-hardy-heron.html")

---

### Post by M4rotku on 2008-06-18
OK, it works now, thanks for the tips websites.

Much thanks,
M4rotku

---

### Post by M4rotku on 2008-06-19
Ok, the DVD's play now, but they do not come up with a menu.  This was not a problem until I tried to watch a DVD that contained several episodes of a tv show.  It just plays all of the video content without giving me the menu to select which show I want to play.

What do I need to do to get a menu?

Much thanks,
M4rotku

---

### Post by mc4man on 2008-06-19
> What do I need to do to get a menu
either install and use totem-xine or vlc
edit:
As far as totem - on _hardy_ just install totem-xine then run 
```
sudo update-alternatives --config totem
``` and choose 2 to set totem-xine as totem player
On _gutsy_, in synaptic remove totem-gstreamer and then install totem-xine
If you have any navigation issues with vlc then go to edit menus (right click on applications or go system -> preferences -> main menu), expand sound and video, and on right side right click on vlc -> properties. Change the launcher command to vlc %m

---

### Post by M4rotku on 2008-06-20
Much thanks Mc4

---

