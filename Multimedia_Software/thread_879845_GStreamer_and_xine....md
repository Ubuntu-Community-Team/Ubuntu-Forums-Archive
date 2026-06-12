---
title: "GStreamer and xine..."
date: 2008-08-04
forum: Multimedia Software
---

### Post by xeriouxi on 2008-08-04
Hi!

I read somewhere that xine is that bit better than GStreamer at the moment when it comes to DVD's etc. so I removed totem-gstreamer and installed totem-xine.

Will I have any problems now that I removed GStreamer outside of using Totem? I wouldn't mind having them both together (if there was any benefit) but I couldn't find anywhere on my system an option to tell Totem to use xine instead of GStreamer in any options. The reason I bring this up is that there's some flickering going on when I'm watching movies in Totem (could be releated to Compiz apparently) and VLC is a little iffy playing files too as it sometimes gets weird artifacts.

Is this possibly an issue because i removed totem-gstreamer and replaced it with totem-xine? I'm pretty rusty on the 2 backends because I can't find any options for either of them anywhere...

Any help is most appreciated! =)

---

### Post by Vivaldi Gloria on 2008-08-07
> **xeriouxi said:**
>  and VLC is a little iffy playing files too as it sometimes gets weird artifacts.

Is this possibly an issue because i removed totem-gstreamer and replaced it with totem-xine? 

Nope. Which totem you have can't effect vlc.

You can try installing totem-gstreamer back. Then install gxine. So you'll both have totem-gstreamer and a xine player (gxine) at the same time. Also try gnome-mplayer.

---

### Post by Melcar on 2008-08-07
I prefer gstreamer since it tends to work better with my ATI cards (both with fglrx and the open source driver).  Xine does not work with TexturedVideo (most newer ATI cards use this) and suffers from massive flickering with accelerated videos when I have Compiz on.  Gstreamer works fine with both VideoOverlay and TexturedVideo (except for the image tearing) and suffers from no video flickering in Compiz when I use the open source driver.  The only plus Xine has for me is the ability to use DVD menus, but I don't use my computer for watching DVDs.
As for playback quality of both, they are pretty much equal now.  When using Xine I prefer to use either Kaffeine or Gxine as video players, since these can easily changes engine settings (Totem can't).

---

