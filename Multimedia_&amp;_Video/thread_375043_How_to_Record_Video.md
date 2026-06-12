---
title: "How to Record Video"
date: 2007-03-03
forum: Multimedia &amp; Video
---

### Post by daynah on 2007-03-03
I'd like to make a video blog but I can't figure out how to record video with my webcam. I have the webcam drivers working, I can use it in WengoPhone, and I can take pictures with it in Camorama... but all of the programs I've found just take pictures, they just don't record video. All of the guides I've found for how to make a vlog say "Once you've recorded a video..." :( but that's the step I'm having trouble with.

I never did it in Windows, so I don't know how to ask "what's the linux equivalent software?" Does anyone have a hint of what program records video?

---

### Post by tagra123 on 2007-03-03
I use mythtv usinga video card but tvtime can work too with a capture card.

the video device should be in /dev/vid0 or a similar path.   I believe you can capture directly from the /dev/vid and use it as in input for ffmpeg mencoder etc...

Google for one of these 
ffmpeg capturing video 
mencoder capturing video
mplayer capturing video

something useful for what you are wanting should turn up.

Pleas let us all know how you end up making it work.

---

### Post by daynah on 2007-03-07
I think there's some miscommunication (hopefully it's just me understanding you). I think you were trying to give me programs on how to capture video from the television... but I want to just capture video from my simple usb webcam :) Though it would be cool to watch tv on my computer, this is not the project for the week... ;)

I'm trying to make a video blog using my webcam is the end result. I want to record video on my webcam, but so far I can only take pictures. Unless mythtv has other features I don't know about, I don't think that's the right program.

---

### Post by tagra123 on 2007-03-07
[http://users.aber.ac.uk/cjs06/homepage/index.php?display=content/Timelapse%20Videos/timelapse.html](http://users.aber.ac.uk/cjs06/homepage/index.php?display=content/Timelapse%20Videos/timelapse.html)

The link above uses xawtv. I guess there's an archive option which saves the video. I believe these program should work even though TV is in the name.

---

### Post by macewan on 2007-04-05
as a short term fix you might want to consider using the video blogging feature found on youtube or dailymotion

---

### Post by human-ness on 2007-10-18
I know this thread is old now, but I thought this information may come in handy for people that have taken the plunge into Ubuntu, and use motion.

Those of you that use Motion ( "sudo apt-get install motion" and then "sudo kate /etc/motion/motion.conf" ) should know that you can set "ffmpeg_cap_new on" in the "motion.conf" and then set your threshold to 1, so "threshold 1" and you can record to an avi file like that.  If you run Audacity along side it, you can record sound and then later put it all together.  

I use a windows program to put it together, which is pretty useless information to those that only use Ubuntu, but if you come up with an idea, where I could do this in Ubuntu, I would be a very happy man.

Cheers all.

---

### Post by JBull on 2007-10-20
Same problem here.  its such a basic thing to record sound and video with a webcam but seems damn near impossible with Linux.  I've finally got one of my webcams working to take still pictures but I want to make a video for youtube and haven't found anything that actually works.  

I formerly used the Logitech software that came with my webcam under Windows Xp.  But still looking for something in Linux that does the same.  

Right now my microphone works for audio and my webcam works for still picturesusing software called "webcam".  Whats the next step?

Here's part of my webcam.conf file if this helps any:

[grab]
device = /dev/video1
width = 640
height = 480
delay = 1
input = camera
norm = ntsc
quality = 100
trigger = 0

---

