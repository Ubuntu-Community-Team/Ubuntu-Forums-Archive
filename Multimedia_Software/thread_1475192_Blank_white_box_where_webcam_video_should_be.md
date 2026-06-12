---
title: "Blank white box where webcam video should be"
date: 2010-05-06
forum: Multimedia Software
---

### Post by *Legion* on 2010-05-06
(I originally posted this [here]("ubuntuforums.org/showthread.php?p=9251025") but I think that was the wrong place. This appears to be a software issue)


I have a Sager NP5797 running Lucid (32-bit) with a BisonCam NB Pro (V4L2) webcam on /dev/video0

In Flash (like Chatroulette.com), everything works great. My video appears to both myself and others, and I see incoming video. (I am using the 10.1 RC libflashplugin.so, downloaded from Adobe's site)

But in applications like Cheese, Skype, etc., **I get a big blank white box where video should be**:

[IMG]http://img144.imageshack.us/img144/7251/cheese1.png[/IMG]

Cheese (as well as every other app I try) sees the camera on /dev/video0:

[IMG]http://img571.imageshack.us/img571/5254/cheese2.png[/IMG]

In Skype, **the person I am calling sees my video perfectly fine**. So my camera is "working" and sending video. But I cannot see my video, **nor can I see *their* incoming video**. It's all a big white box just like the one in Cheese in the shot above. Taking the other person out of the equation, when I go to use the "test" in Skype, it's just a blank white box too. The video will not draw for me.

Again, I **do** see video in Flash-based web apps that use the webcam. And other people are seeing my video. But webcam video (both mine and the incoming stream) won't "draw" for me.

What makes V4L video not draw? I am using the binary NVIDIA driver for the GTX 280M chip in the laptop, and I am using Compiz. Though I tried turning Compiz off and Cheese still just showed the white box.

Any ideas?

---

### Post by *Legion* on 2010-05-06
Here's v4l2ucp and the attempt to use the Preview capability:

[IMG]http://img7.imageshack.us/img7/4366/cheese3.png[/IMG]

---

### Post by no2498 on 2010-05-07
this may or may not help

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese 



hope it helps

---

### Post by *Legion* on 2010-05-07
Unfortunately, no. I did try that, and I should have mentioned so.

But it's not a case of V4L not being able to interact with the device - it's working. 

For some reason, the video does not draw on my screen.

I think this may be a case where I need to do a fresh Lucid install. :(

---

### Post by no2498 on 2010-05-08
try setting the pic size smaller in cheese
edit preferences


cheese has all the settings for webcams now days

---

### Post by *Legion* on 2010-05-10
I just discovered that this is not limited to webcam video.

I tried to play a WMV file and got the same white box in VLC.

A reinstall is definitely in order. Sad! I had gone so long without a fresh install. Oh well, time to 64-bit this machine anyway. IF anyone asks, I'll say that's the reason I reinstalled. :)

---

### Post by zicofc on 2010-05-14
I've the same problem with Skype video, and with SMPlayer I hear the audio but I see a tranparent box (with other player like VLC all seems to be OK)

This has happened after an upgrade from 9.10 to 10.04

Anyone have a solution? Thanks
:(

---

### Post by *Legion* on 2010-05-14
> **zicofc said:**
> I've the same problem with Skype video, and with SMPlayer I hear the audio but I see a tranparent box (with other player like VLC all seems to be OK)

This has happened after an upgrade from 9.10 to 10.04

Anyone have a solution? Thanks
:(

My solution, which worked, was a fresh 10.04 reinstall.

Obviously there was something in the upgrade path from 9.04 or 9.10 to 10.04 that caused this issue for some of us.

---

### Post by M1ke on 2010-05-14
I have this exact issue on a fresh Lucid installation. I've seen the "LD_PRELOAD=" advice elsewhere but I don't understand exactly what it means - how do I run skype using that parameter to see if it helps?

I'm really trying to avoid a reinstall here as I didn't install via 9.10 upgrade. I should mention also that I have two machines with this same problem, both of which were clean 10.04 installations.

---

### Post by no2498 on 2010-05-14
M1ke open a terminal put it in it
and do not close it

---

### Post by Psychoscorpic on 2010-06-17
Don't reinstall! You're using Linux, not Windows.
Besides - Mine is a clean install of 10.04, and got the same white screen incoming issue.

Found this on the Swiss Ubuntu Forum:
```
export XLIB_SKIP_ARGB_VISUALS=1
```
Run it in Terminal, and close & restart Skype.

---

### Post by *Legion* on 2010-06-17
> **Psychoscorpic said:**
> Don't reinstall! You're using Linux, not Windows.
Besides - Mine is a clean install of 10.04, and got the same white screen incoming issue.

Found this on the Swiss Ubuntu Forum:
```
export XLIB_SKIP_ARGB_VISUALS=1
```
Run it in Terminal, and close & restart Skype.

Tried that. It did not work.

The only thing that worked was a complete reinstall.

Keep in mind that the white screen happened with all video, not just Skype.

---

### Post by M1ke on 2010-06-25
This won't be of any use to you now that you've reinstalled, but I did eventually find a fix that got skype working perfectly for me again! I found it trawling these forums but have unfortunately lost the thread so I can't give credit to the user I'm eternally grateful to.
 
It's basically the fix posted just above, with a slight alteration that specifically mentions skype.
 
```
 
export XLIB_SKIP_ARGB_VISUALS=1 && skype

```
 
To save some terminal leg-work each time I want to use skype, I edited the app's launcher in the Applications menu and replaced the command "skype" with the following:
 
```
 
sh -c "export XLIB_SKIP_ARGB_VISUALS=1 && skype"

```
 
I now once again have a clickable skype launcher and fully functioning video chat in Ubuntu 10.04 64-bit.
 
Thank you, whoever you are! You've saved me having to boot Windows 7 just for skype :)
 
Edit: Ah, I see your problem related to all video and not just skype. In that case I did also read a suggestion of a strange conflict with cairo dock running in GLX mode conflicting with some video resources during my fix-hunt. Just a pointer to a possible avenue to explore further for anyone who comes across this thread with the same problem in future.

---

### Post by managementboy on 2010-10-21
you can edit /usr/bin/skype-wrapper

and add
XLIB_SKIP_ARGB_VISUALS=1
to the beginning of the last command... no terminal needed after that

---

### Post by sleepee on 2011-02-21
i know this is old, but thanks so much Psychoscorpic, M1ke, and managementboy.  this fix worked perfectly for me.

---

