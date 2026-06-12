---
title: "WebcamStudio - choppy broadcast video"
date: 2009-08-07
forum: Multimedia Software
---

### Post by MaindotC on 2009-08-07
I use WebcamStudio which is awesome and I enjoy being able to share stuff w/ friends.  However, there is a noticeable choppiness that appears when it is running.  When I try and play a video file, observers report choppy video.  Has anyone else experienced problems streaming?

I am using the ATI proprietary driver on what is now considered a "legacy" video card so it is no longer supported.  I mention that because I wonder if my video driver settings could be causing an issue - but I rarely have any other problems.  Of course, it's proprietary so I have no way to configure it :(

---

### Post by markbuntu on 2009-08-09
Are you still using hardy?
I am too but i also have jaunty installed which will soon be updated to karmic.
Which driver are you using 9.3?

You can fix choppiness with that driver in gstreamer apps by changing System/Preferences/Multimedia Systems Selector/Video Default Output Plugin to

X Window System (No Xv)

If Webcam studio is using the xine engine you need to change the xine video driver to xv which you can do in vlc if you have it installed or in the xine player if you have that if there is no way to do it in Webcam studio.

You can also try turning off the desktop visual effects.

---

### Post by MaindotC on 2009-08-09
I'm not precisely sure what version I have installed.  I can't recall if I was experiencing some issues w/ 9.3 and rolled back to 9.1.  Thank you so much for the suggestions - I'm going to try them!  How can I tell which video driver WCS is using?

---

### Post by markbuntu on 2009-08-09
I think I am also using the 9.1 driver on this hardy install I am running right now because I cannot find anything newer in my download folder. Anyway, that should work for that driver also.

In the information section of the catalyst control center the 2D driver version should be 8.59.2 for the catalyst 9.1 driver package.

---

### Post by MaindotC on 2009-08-09
Ah, good call.  It says 8.57.2.  I'll try different versions of the ATI driver - all I have to do is install, restart, and if it doesn't look better then use the uninstall script and reboot.

In VLC, I did go to Settings -> Preferences -> Video -> Output Modules -> and selected XVideo extension video output.  I also disabled desktop effects.  I'm not really sure it was different - I'll stream and ask one of my friends how it looks.

---

### Post by loell on 2009-08-09
I don't think it has something to do with your video driver or even webcamstudio. 

it may be that the medium for the broadcast isn't really for high resolution video stream.

---

### Post by MaindotC on 2009-08-10
When I broadcast from my webcam or my desktop the video is just fine.  When I play videos is when this happens.

---

### Post by loell on 2009-08-10
> **strAlan said:**
>  When I play videos is when this happens.

you mean when you broadcast the clips / movies using webcamstudio? this is when they say that they see a choppy video at the other end?

---

### Post by MaindotC on 2009-08-10
Here, tell me what you think: [http://www.livestream.com/asymptote](http://www.livestream.com/asymptote)  Yes, when I stream movie files through webcam and through livestream or ustream, the users say they're choppy.  When I switch to streaming my desktop, it doesn't appear choppy.

I just installed the 9.3 driver and in the CCC it says 2D Driver Version 8.58.2.  How can I tell if WCS is using xine or any other type of video driver?

---

### Post by loell on 2009-08-10
it's definitely the medium, livestream as your medium can only take part of the frames , videos from movies have much higher frame rate than that of livestream. hence the other end see some chopiness.

---

### Post by kavoura on 2010-04-15
> **markbuntu said:**
> ...If Webcam studio is using the xine engine you need to change the xine video driver to xv which you can do in vlc if you have it installed or in the xine player if you have that if there is no way to do it in Webcam studio...

How do I do that in VLC? I see no option anywhere for changing which video driver it uses or what Xine will use.

I am using VLC 1.0.2 on Ubuntu 9.04 (AMD64).


I came across this thread as I am trying to get live video streaming to work with livestream.com but so far have had no success.

---

### Post by ky5u on 2010-04-20
Can anyone explain how "broadcaster" works.  I entered the desired port (8080) in both boxes and it chokes saying it can't open something.  Of course the error prints out where I can't see it and the window can't be resized.  

I love webcamstudio.  Have it working with uStream and all other functions work.  I want to put out a picture to http//<myhostname>:8080 .  I use WebcamXP in windows and Evocam in OSX.  Both work good.  But so far nothing on uBuntu.  THANKS!!

---

