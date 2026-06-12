---
title: "Video Playback Flickers"
date: 2009-01-24
forum: Multimedia Software
---

### Post by psychobot on 2009-01-24
I'm running Ubuntu 8.10 with desktop effects fully enabled. My problem is that the visualizations and video playback flickers but when I disable compiz, the problem is resolved. I've went into gstreamer-properties and selected (X Window System no Xv) but that only helps with the visualizations in Rhythmbox and Totem but DVD playback is still choppy and out of sync. Also, the visualizations in Exaile still flicker. Just playing around, I downloaded VLC and changed the output mode to X11 and the DVD played fine.

Right now I'm dual-booting XP/Ubuntu and eventually want to cut XP from my system. However, I use the system for multimedia purposes and cannot do so until I get the problems I'm encountering resolved. 

I'm running a FX-60 cpu with a X1600XT graphics card. Let me know if you need more information. 

Thank you


**update**
I can play a video file saved to the hdd flawlessly. Any help with this is greatly appreciated.

---

### Post by psychobot on 2009-01-26
Nobody has any help on this issue?

---

### Post by psychobot on 2009-02-07
Anyone?

---

### Post by Yink on 2009-02-07
I got this from another post.

Open up terminal by going into Applications > Accessories > Terminal

Then type in

gstreamer-properties

and a window titled Multimedia Systems Selector will load up. Click the second tab titled Video. And change the first option which says plugin to

X Window Systems (No Xv)

Click close and then try your video. It sorted it for me.

---

### Post by hunterGT on 2009-02-09
This working on mine. Thanks.

---

### Post by psychobot on 2009-02-09
I've done that and it works. However, when I play a movie, it doesn't sync video with sound and playback stutters. This is the outcome in Totem as I have not tried any other players. Visualization playback works fine in Totem/ Rhythmbox but still flickers in Exaile. I'm trying to keep a lighter installation so getting the video to work with Totem is my goal. 

I've read that the newest ATi drivers fix all the problems Linux users have had with compositing and Xv so I'd like to give them a try. However, I'm not quite sure how to get them installed. I installed the current FGLRX drivers "The Ubuntu Way" so would I just need to deactivate the driver through System ---> Administration ---> Hardware Drivers and then make an install script with the downloaded drivers? In Windows it was advised to completely remove all traces of a driver before upgrading. Is it the same case with Linux? If so, how do I need to prepare the system to properly install the new drivers?

Thank you

---

### Post by libihero on 2009-02-09
this one worked for me: [http://ubuntuforums.org/showthread.php?t=754712](http://ubuntuforums.org/showthread.php?t=754712)

---

### Post by shak3800 on 2009-02-09
thanks it works!

---

### Post by psychobot on 2009-02-10
I got the 9.1 driver package installed and it FIXES the flickering with Xv enabled and compiz running. I can even go into cube and the video still plays. However, it didn't fix the stuttering problem with Totem and movies. Disabling Xv doesn't make any diffenece.

Another problem I have is that any embedded video will not properly fit inside windows or its set boundaries (visualization covers other spots on the screen or it doesn't scale to fit inside its boundaries). How can I fix the embedded video problem? 

I thank everyone for your help so far.

---

### Post by bronxbomberz41 on 2009-03-08
This worked for me thank you!!

---

