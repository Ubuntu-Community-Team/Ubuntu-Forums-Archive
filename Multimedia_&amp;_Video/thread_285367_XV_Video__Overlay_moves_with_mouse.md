---
title: "XV Video  Overlay moves with mouse?"
date: 2006-10-26
forum: Multimedia &amp; Video
---

### Post by ahsile on 2006-10-26
I just upgraded to edgy today, and I've come across a very strange problem. When I try to play a movie, totem will come up but it will start off with a blank screen. As I move the mouse cursor over to the left of the screen, the video overlay will show up on totem's window and stop where it's supposed to be. If I move the mouse back to the right, the video goes away.

Even stranger is that I can drag the totem window around, and the movie stays even though the mouse is moving. If I drag from the first monitor to the second (setup via aticonfig --initial=dual-head) the video disappears again. But, if I drop the window and move the mouse to the left again it shows up once more.

I've (partially) resolved this by turning off XV overlays in Xorg.conf, and turned on OpenGLOverlay. 

As well, I'm finding that totem-gstreamer is crashing playing movies. It will play correctly, but when it hits the end it just dies. I have had to install totem-xine (which works now, unlike in dapper).

Running: ATI X800XT, fglrx drivers

---

### Post by Jbloudg20 on 2007-03-22
I am having the same problem!

---

### Post by tehmatticus on 2007-04-02
Ditto here.  As far as I can tell, its interpreting the size of the smallest (probably primary) monitor, and if you move your mouse outside its dimensions, it'll start messing up.

I hope they make a fix soon as it can be rather annoying.

---

