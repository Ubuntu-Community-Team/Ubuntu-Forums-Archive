---
title: "Three media questions"
date: 2008-05-05
forum: Multimedia Software
---

### Post by chimerical_brio on 2008-05-05
So I'm interested in building a media server, with attached speakers and a monitor, to be controlled through SSH. It would serve as backup as well as a way to play music/movies independent of my laptop. Questions:

1. Does anyone know of any text-based MP3 players reminiscent of Rhythmbox/iTunes? I'd like to control my music through SSH, but I'm not a huge fan of playlist-based music players like mpd.

2. Are there any good CLI-based burning/ripping tools? For both CD and DVD.

3. Is there any way for me to control a video player through SSH? Ideally, I would SSH into the media server and through my SSH terminal start a movie, presumably on tty7, which would output to my monitor. Is there some sort of a movie daemon that would let me do this? Or, is there a way for me to launch a media player in an X session? For instance, I could have X running with something like ratpoison or wmii, and open up mplayer in that session, through SSH? Is that possible?

Thanks a lot.

---

### Post by Ptero-4 on 2008-05-05
2. For burning bashburn with cdrkit.
3. If you can use X. ssh -X appname will do it.

---

### Post by chimerical_brio on 2008-05-05
Thanks for the bashburn/cdrkit recommendation; looks good.

That would work, but I think I explained myself poorly. What I'd like to do is have a media server connected to a monitor, and control what is playing on the monitor through SSH. So I'd be able to do the equivalent of saying, "play this video file with mplayer in the X session." Almost like VNC except...controlled from SSH. Possible?

---

### Post by Ptero-4 on 2008-05-08
that's exactly what ssh -X is for.
Basically you issue ssh -X mplayer from the PC you'll be using to control your server and mplayer will appear in that PC's desktop, but it'll be running on the server. Offcourse you'll need to set your server's display manager to autologin first and throw you into a minimal wm (wmii, dwm, ratpoison, etc), after that you can safelly remove both monitor and keyboard/mouse from the server and control your apps through ssh -X appname.

---

