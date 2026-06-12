---
title: "zoom webcam"
date: 2010-03-16
forum: Multimedia Software
---

### Post by DanBender on 2010-03-16
I'm trying to use Skype video chatting on a Mythbuntu box hooked up to my big-screen TV. The problem I'm running into is since the TV (and thus the camera) are across the room, the camera picks up a lot of "extra picture" around the edges and the subjects (me and my family on the couch) are quite small.

I'm using a Logitech C500. In Windows, this camera came with a utility that took the output of the camera and transformed it (zoom, pan, etc.). In fact, that was the default way of using the camera (Skype, at least, used the ouput of that utility, not the camera feed itself). So I'm looking for a utility that does something similar in Linux. At the very least if there's some tool that takes the 1280x1024 /dev/video1 stream, crops it to just the center 640x480, and dumps it to /dev/video2 that would be just about perfect.

I've gotten effecttv, vloopback, and gstfakevideo as suggested in [this thread]("http://ubuntuforums.org/showthread.php?t=725179"), but haven't gotten them all working yet because of some video assignment and compiling issues. However, while I've found plenty from Google on how to get and compile these tools, there's precious little information about *what they're actually supposed to do.* [rant] For crying out loud, people, at least write a man page.[/rant] So I'm not even sure any of those tools actually would do what I want here. Does anyone here know about doing this kind of thing?

Thanks a bunch,
-Dan

---

### Post by no2498 on 2010-03-17
if your on 910 karmic cheese is loaded
you can set the size of the video
it may set the size in all programs 
hope this helps

---

### Post by DanBender on 2010-03-20
I'm not trying to "change the size" on the stream (Skype's settings.conf can change the resolution if I want). I'm trying to apply a transformation (uhhh...maybe filter is a better word?) to it in real-time, and have the result of that available to Skype. The camera I'm using is a simple, fixed-zoom camera.

*EDIT 11:20 PM*
Okay, here's pictures to describe exactly what I'm trying to accomplish. These images are at half-scale so they'll fit well on the page.

My camera outputs this in 1280x1024:
[IMG]http://img.photobucket.com/albums/v119/pincushionman/linux_needs/cam-output-sm.jpg[/IMG]

And cropped to the center 640x480:
[IMG]http://img.photobucket.com/albums/v119/pincushionman/linux_needs/skype-input-sm.jpg[/IMG]

THAT'S what I want. Obviously I'll re-aim the camera.

---

### Post by no2498 on 2010-03-22
see if you set the size in cheese to 320x240 if it helps you any
i know what your trying to do
my webcam does it on its own and i cant get the 640x480 pic back
you can also try the settings in ekiga softphone
or xawtv if it opens for you
but on 910 karmic they/ubuntu give the settings to cheese
hope this helps

---

### Post by DanBender on 2010-03-24
Perhaps there is another control in Cheese that I'm missing here? The only control I find is edit->preferences, where there is a drop-down box for the video source and for the resolution. Changing the resolution drop-down to a smaller size still gives the same picture, except lower quality. It's scaling the (whole) picture, not doing a digital zoom or a crop.

I will try those other tools you suggested, though. Are they available in Synaptic?

Hey, thanks for your help so far.

-Dan

---

