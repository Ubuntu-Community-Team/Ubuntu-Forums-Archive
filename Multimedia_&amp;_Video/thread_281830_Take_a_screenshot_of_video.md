---
title: "Take a screenshot of video?"
date: 2006-10-21
forum: Multimedia &amp; Video
---

### Post by kasra on 2006-10-21
Hi all,
I need a way to take a screenshot of a single frame of video. How would I go about doing this? Whenever I take a screenshot (PrtScr button on the keyboard), the video screen shows up as completely black.

Can anyone help? Thanks!

---

### Post by SendDerek on 2006-10-22
I'm not sure if it's the same thing, but have you tried the gnome screenshot utility?

In the terminal type this:
gnome-panel-screenshot 

you can also add a delay to it by typing this:
gnome-panel-screenshot --delay 5  (5 is the seconds)

Does this help at all?  Like I said, I don't know if this is the same thing or not.

---

### Post by Roger Mudd on 2006-10-22
How about pausing the video and then taking a screenshot?
Kind of a blunt force method, but it's worked for me in the past.

---

### Post by kasra on 2006-10-22
Thanks for your responses.
However, taking a screenshot did not work for me (even when it was paused) -- it was still black.

I installed Avidemux, went to the frame I wanted and then File > Save > Save JPEG Image. Hope this helps someone!

---

### Post by sparkplug on 2006-10-22
Try the X11 not xv if you want 2 take screenshot of video.If you play the video with mplayer,you can use the command like :mplayer -vo x11 xxx.avi.
Do u know what I mean?Sorry for my poor English.

---

### Post by chrx on 2006-11-09
i dont understand..? how do i take a snapshot with mplayer?

---

### Post by zgornel on 2006-11-10
You take the screenshot with PrtSc keyboard key :) You just have to have the video output driver set up to X11 instead of xv.

---

