---
title: "Working live CNN video environment"
date: 2007-04-18
forum: Multimedia &amp; Video
---

### Post by GaTk on 2007-04-18
I would like to hear from anyone who has a working environment that plays live video from CNN with an EDGY 6.10 KUBUNTU distro.  I have tried (in LINUX) everything I could find but
nothing I've tried WORKS.... from Amarok- to Xmms... havent' tried anything Y or Z yet !!
I have a working WINXP setup that uses REALPLAYER.  I will change distro if necessary.

Thanks

Ted in Atlanta

---

### Post by DirtDawg on 2007-04-20
Have you tried using the Linux port of [RealPlayer]("http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Multimedia_Player_.28RealPlayer_10.29")?

---

### Post by ronocdh on 2007-04-21
[See here]("http://ubuntuforums.org/showthread.php?t=371093"). CNN.com video works swell for me now.

---

### Post by mindracer on 2008-05-28
I have Hardy 8.04 and CNN Live video doesnt work.  They require you to install a plugin in Windows and maybe MAC.

Please use this form to let them know you miss CNN Live Video on Ubuntu/Linux:

[http://www.cnn.com/feedback/forms/form9d.html](http://www.cnn.com/feedback/forms/form9d.html)


If you have found a workaround, please let us know..

---

### Post by Turkten on 2008-07-10
Well, you can't view it in your browser but... I have a way to watch it. As far as media players go, I prefer VLC. This may or may not work with others. I have not tested it. I am using 8.04.

Here's my steps..

1) Open Terminal
2) sudo apt-get install vlc
3) run vlc
4) File -> Open Network Stream
5) In the HTTP/HTTPS/FTP/MMS field, put in the following address:

[http://www.cnn.com/video/live/cnnlive_1.asx](http://www.cnn.com/video/live/cnnlive_1.asx)

This worked for me and, once it starts playing, if you go into View -> Playlist, you can click Manage -> Save Playlist. I just save it as CNN Live Stream and then it's always there.

---

### Post by billybob123 on 2008-07-12
Thanks for the tip.  When I try this though, all I end up with is the red CNN logo in the corner over a black screen, with no sound.  Something's coming though, since the logo is there, but clearly not what I want.  Did you have to fiddle with VLC settings?  Same thing in mplayer.

---

