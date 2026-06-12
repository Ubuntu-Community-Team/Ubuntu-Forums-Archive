---
title: "Unable to see video"
date: 2008-11-12
forum: Multimedia Software
---

### Post by apparle on 2008-11-12
I have an onboard ATI Radeon Xpress 200 and have installed fglrx.
I have installed the codecs for xine. Also i have VLC.
I have desktop effects enabled using KWin (KDE4).
When I play the video in any xine based player(video driver :auto) I see a blue screen with audio playing.
Now when I write this or something like this in xorg.conf
############################
Section "Extensions"
         "Composite" "false"
End Section
##################
the video plays fine. But the desktop effects are disabled as compositing is disabled.



Same is the case with VLC.
But when I have desktop effects enabled("Composite" "true")
and when I select the openGL driver in VLC the video plays but flickers. If I select X11 driver then the video plays but is choppy when fullscreen. Please help....... I want to watch movies

I am going to try Mplayer today and also add a line "Textured video" "off" in xorg.conf.
I'll also post my xorg.conf shortly.


What is compositing and is there any way I can use desktop effects when composite is disabled in xorg.conf

---

### Post by Crafty Kisses on 2008-11-12
Do you have the proper codecs installed?

---

