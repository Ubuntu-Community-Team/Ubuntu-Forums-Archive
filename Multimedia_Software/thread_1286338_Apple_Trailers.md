---
title: "Apple Trailers"
date: 2009-10-08
forum: Multimedia Software
---

### Post by StonePiano on 2009-10-08
I used to watch Apple movie trailers fine.  But since upgrading to Ubuntu 9.04 with Firefox 3.0.14, I cannot watch the trailers.  When I click on a movie trailer, I get the message:

[B]Search for suitable plugin?
The required software to play this file is not installed...[/B]

I've searched for firefox plugins and installed this "Embedded Objects" one:
[https://addons.mozilla.org/en-US/firefox/addon/5258](https://addons.mozilla.org/en-US/firefox/addon/5258)
(Then restarted firefox.)

But I still get the same error message.

Does anyone know what plugin is required?

Many thanks,
Stone

---

### Post by Arquis on 2009-10-08
The Apple trailer site changed its detection so to block any incoming Linux player connection. I found a workaround on the net, but I found it easier to seek another trailer site.

Cheap move from Apple... :(

---

### Post by qyot27 on 2009-10-08
Actually, they aren't discriminating against Linux (they're forbidding non-Quicktime access).  Windows also got the shaft, depending on how you look at it.

(I always just straight downloaded the trailers through Firefox, which stopped working - the solution is to give wget the proper info with the -U and --header options.)

---

### Post by mc4man on 2009-10-08
long thread with many different ways from wget to cli vlc and mplayer and firefox stuff
[http://ubuntuforums.org/showthread.php?t=1245441&highlight=apple+trailers](http://ubuntuforums.org/showthread.php?t=1245441&highlight=apple+trailers)

Of note is that one of the few things totem does well in karmic is play directly from apple site
I just right click on the trailer of choice ->  open link in new window. Plays very well in a fullsized  window

---

### Post by qyot27 on 2009-10-20
A solution I found a couple days ago is the HeaderControl extension, which allows Firefox to use an identifier on just certain sites:
[http://mirzmaster.wordpress.com/2009/10/09/helpful-hints-apple-movie-trailers-download-using-firefox-greasemonkey-and-user-agent-hack/](http://mirzmaster.wordpress.com/2009/10/09/helpful-hints-apple-movie-trailers-download-using-firefox-greasemonkey-and-user-agent-hack/)

It's experimental, but I had no problem downloading the Stan Helsing trailer using it (admittedly, under Windows, but the dialogs in that blog post are clearly from a Linux build).  The blog post above outlines that it works for simply watching the trailers too.  The actual page for the extension:
[https://addons.mozilla.org/en-US/firefox/addon/11327](https://addons.mozilla.org/en-US/firefox/addon/11327)

The Greasemonkey script isn't necessary for this, just HeaderControl is.  I know the filename syntax Apple uses for the trailers so I don't need an extension to let me download them.

---

