---
title: "Linux powered robot - webcam streaming under Linux - some help would be awesome!"
date: 2010-04-09
forum: Multimedia Software
---

### Post by never gonna give you up on 2010-04-09
Hello Ubuntu Community!

Jesus, I wrote you a novel. TL;DR how do I do a good job of low latency webcam streaming under linux. See the list at the very end of things I have already tried.

Now for some back story: This one is a tuffie. So I'm on a team that is building a hulking beast of a robot that is designed to rove the deserts near a country's border in search of illegal aliens / intruders / whatevers and conduct rudimentary surveillance on them and track their locations using vision and GPS. If you're interested, I'll link to the project page when we're all done. Fortunately, this is only a proof of concept so we have some slack, but we want to make this thing as bad *** as reasonably possible.

One of the things we would like to do is operate the robot over the internet from a computer out of line of sight. Since this a proof of concept, and we're broke college students, the bot is being controlled over our college's wifi. There is a small computer I own ([http://www.fit-pc.com/web/](http://www.fit-pc.com/web/)) running ubuntu linux that serves as the brains of the operation (running a small webserver, controlling microcontroller, logging GPS, etc). I have a lot of experience doing micro-controller programming / web-programming / regular-programming / all the GPS stuff associated with our project, so that is no big deal.

Where I'm getting tripped up is how to get this thing to properly stream video! I am stumped here, and have already tried the following options:

[LIST]
[*]Used python to take snapshots from webcam and store them as a static file on the webserver, have ajax loading image over and over. It works, but proved to be janky / too slow / randomly stops reloading the image
[*]VNC embedded in a web browser with the webcam feed running local fullscreen - worked surprisingly well with respect to everything else tried, but it still sucked. Horridly backwards  in terms of making sense and efficiency.
[*]Flash streaming (like whats on chatroulette, etc) is incompatible with linux, specifically the V4L2 libraries, as far as I can tell
[*]set up skype to auto-answer incoming calls with video - doesn't work b/c of latency issues with skype's servers / skype has poor linux support to begin with (only uses V4L I think for video)
[*]Ustream - broadcaster webpage straight up did not load properly, plus even if this did work we would have advertisements in our webcam feed, which is a no-no
[*]webcam_server, the java applet (see tutorial I followed here: [http://hacktivision.com/index.php/2009/06/16/setting-up-an-ubuntu-webcam-server?blog=2](http://hacktivision.com/index.php/2009/06/16/setting-up-an-ubuntu-webcam-server?blog=2) ) for linux, doesnt work - straight up does nothing upon opening up a webpage with the applet embedded in there
[*]VLC streaming - was the most promising, however HTTP streaming is the only way I could actually get a picture traveling from one computer to another. Frame rate / picture quality was good, however there is this massive delay (~7-10 seconds, even behind my own router) due to a buffer that i could not change without error - tried to get UDP and RTP streaming to work instead of HTTP, but couldn't manage it ( see: [http://www.videolan.org/doc/streaming-howto/en/ch04.html](http://www.videolan.org/doc/streaming-howto/en/ch04.html) ). Also, real-time transcoding of the video took up tons of cpu time, may be the source of massive delay
[*]SSH with X11 display forwarding didn't work either. VLC under X forwarding has a shared memory error. Mplayer kinda worked, was ultimately too delayed / choppy to be useful. There is no compression going on here so i'm not really surprised.
[/LIST]

Anyhow any help you guys can give me would be phenomenal

From A fellow Ubuntu enthusiast

---

### Post by no2498 on 2010-04-09
only 2 that come to mind i did not see you tried
1 is, motion 
2 is, wxcam has motion detection

hope this helps

---

### Post by never gonna give you up on 2010-06-03
Hello Ubuntu community! So it had admittedly been awhile -- the robot has been built and all the software on it works great. You can see the final product of my efforts here: [http://stonelinks.ath.cx/luke/School/College/ENGR%202050/IED%20Design%20Project/Final%20Report/IED_tech_report_final.pdf](http://stonelinks.ath.cx/luke/School/College/ENGR%202050/IED%20Design%20Project/Final%20Report/IED_tech_report_final.pdf)

Long story short the best thing for the webcam was a beautiful piece of software called mjpg streamer: [http://sourceforge.net/projects/mjpg-streamer/](http://sourceforge.net/projects/mjpg-streamer/)

---

### Post by nairatinu on 2010-07-11
I found the fix for webcam-server which involves the following "hack":

add the V4L1 compatibility wrapper to the command line

(sudo) LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so webcam-server .....options...

this assumes that v4l1compat.so is located in /usr/lib/libv4l of course.  Works like a charm for me.

nice work on the bot!

---

### Post by Frankels on 2013-03-07
I know this is an old thread but for anyone reading this: I had the same problem: tried to stream webcam from robot over wifi to other computer. It worked when i tried ssh - X [ip adress robot] , log in with password and then start cheese (a webcam viewer) remotely. It has some lag, but not to much for my purposes. There may be better solutions with less lag and such but this was a quick fix.

---

### Post by wildmanne39 on 2013-03-07
Thanks for sharing! Old thread closed!

---

