---
title: "Bad video quality"
date: 2007-09-12
forum: Multimedia &amp; Video
---

### Post by otek on 2007-09-12
Hi, Ive been using Ubuntu now for 3 days but theres a lot of problems I just cant fix. Every video i play, regardless of videoplayer, regardless of format and bitrate looks like ****. Ive tried changing video output and fibble with post processing for 2 days now. It looks kinda ok in normal size, but in fullscreen its blurry and blocky. Im getting so frustrated that I just want to go back to an operating system that can actually play video.

The install is fresh, Ive only installed ati drivers throu envy and the gstreamer plugins to play video. Its like watching a bad vhs. How can the quality be as it was meant to be in windows and **** in ubuntu? Ive tried vlc, totem, xine and mplayer.

Update:
Ive recently installed drivers with automatix and tried gxine, no help. Video is noisy, blurry and blocky.. Please help me, im going insane because of this.

---

### Post by wieman01 on 2007-09-12
Have you tried Kaffeine as well? It might be a better choice.
> sudo apt-get install kaffeine

---

### Post by mysticmatrix on 2007-09-12
> **otek said:**
> Hi, Ive been using Ubuntu now for 3 days but theres a lot of problems I just cant fix. Every video i play, regardless of videoplayer, regardless of format and bitrate looks like ****. Ive tried changing video output and fibble with post processing for 2 days now. It looks kinda ok in normal size, but in fullscreen its blurry and blocky. Im getting so frustrated that I just want to go back to an operating system that can actually play video.

The install is fresh, Ive only installed ati drivers throu envy and the gstreamer plugins to play video. Its like watching a bad vhs. How can the quality be as it was meant to be in windows and **** in ubuntu? Ive tried vlc, totem, xine and mplayer.

Update:
Ive recently installed drivers with automatix and tried gxine, no help. Video is noisy, blurry and blocky.. Please help me, im going insane because of this.

Are you using desktop effects while trying to watch videos? Perhaps if you do, turning them off would result in better performance.

---

### Post by otek on 2007-09-12
No effects. Im reinstalling the system again, and im only going to use envy and automatix to get drivers installed this time, and hopefully this is just some small bug.

---

### Post by wieman01 on 2007-09-12
> **otek said:**
> No effects. Im reinstalling the system again, and im only going to use envy and automatix to get drivers installed this time, and hopefully this is just some small bug.
Is Automatix really necessary? Most of the stuff can be installed easily using Synaptic, etc. I have not heard anything good concerning Automatix. It can seriously hurt your system.

---

### Post by otek on 2007-09-12
Well, the system is totally blank now. Nothing except a clean install of ubuntu.. Im going to try automatix and envy, bevause that is all i need, and not f-up the install by typing thins into terminal that i dont understand. Ill let you know how it turns out :). If this doesnt work Ill go back to windows, unfortunately. Isnt not being able to play video, kind of a huge problem in an operating system?

---

### Post by otek on 2007-09-12
Hooray, it still doesnt work! Its still pixelated, blurry, noisy and blocky. I mean, ive got a intel single core 2.8ghz processor and a Ati Radeon 9500 (or 9700) TX card. A really basic system, and something as simple as normal video playback doesnt work. If ubuntu was a person, Id kick him in the nuts. Im getting sooo frustrated. Ive put 3 days into getting an operating system to work. Windows - Ubuntu = 0-0.

---

### Post by kelvin spratt on 2007-09-12
type in the terminal glxgears  and hit return and wait a few sec you should get 3 turning gears if they are not perfect your vid card is not set up right, try removing envoy etc until you get that part right you can't really move on. ATI can be a pain for a lot of people i was ok installs from the box for me,. do that test fist then work from their.

---

### Post by otek on 2007-09-12
The gears look "perfect", jaggy edges like normal 3d graphics without anti aliasing. It gets choppy when i make the window bigger (closer to fullscreen). I really appreciate all the help!

---

### Post by wieman01 on 2007-09-12
> **otek said:**
> The gears look "perfect", jaggy edges like normal 3d graphics without anti aliasing. It gets choppy when i make the window bigger (closer to fullscreen). I really appreciate all the help!
You should have posted a bit earlier... :-) Makes things a lot easier for you. Now let's get back to the topic.

---

### Post by otek on 2007-09-12
If the video is displayed in its orignal format, it looks sharp and i see no noise and blocking, but when i make it bigger (but you cant really tell when the video is small), its like the player shrinks to the video to half its original size, then rezises it bigger.

---

### Post by kelvin spratt on 2007-09-12
mine are perfect with sharp edges and no jagged edges even on full screen looks like you have a problem with vid acceleration witch i can't help you with as i have never encountered this problem. mine just runs from the box. i do video and photography for a living so it has to be right. there are a lot of good threads on the forum and i'm sure you can get it sorted or try another Distro if all else fails.

---

### Post by otek on 2007-09-12
The ati catalyst display center cant be opened, "no ati driver or driver isnt functioning". Video looked like **** before i installed the drivers and after, and the last time i installed ubuntu the control center worked but the video still looked like **** :). Can you install some unofficial drivers maybe?

---

### Post by wieman01 on 2007-09-12
Tried this one?

[http://ubuntuforums.org/showthread.php?t=515573]("http://ubuntuforums.org/showthread.php?t=515573")

---

### Post by otek on 2007-09-12
Now the video looks ever worse, i uninstalled the ati drivers via envy and installed fgrlx or what its called by the instructions. It looks like its scaled wrong, like you output the wrong resolution to the monitor, this is regardless och what video player i use. This is just when you watch video, everything else looks like normal.

Edit: This is only when you enlarge the video or make it fullscreen, it looks normal if you dont.

---

### Post by otek on 2007-09-12
Is it possible to view video without any hardware acceleration?

I chose to not enable the restricted drivers and restarted and it looks exactly the same.

Without drivers: Blocky, noisy, unsharp and scaling issues
With restricted drivers: Blocky, noisy, unsharp and scaling issues
With Ati drivers installed with envy: Blocky, noisy and unsharp

Edit:

With this written in terminal when using restricted drivers "sudo aticonfig --overlay-type=Xv", the video hasnt got any scaling issues but still looks like crap in fullscreen or anything larger than normal size.

Im getting pretty tired of this.

Im installing windows xp now, unfortunately :(.

---

### Post by cisforcojo on 2007-09-21
Well I honestly think that Automatix and Envy broke you system like the others said. It's happened to me before, I stay away from them. Ubuntu isn't at a point yet where you can just point and click like with Windows. I stress YET. But that's actually one of the GOOD points of Ubuntu, using the command line, you have much much more control. Ubuntu might just not be a good fit for you.

If you want to give it another shot, I could walk you through it. I have a fully functioning Ubuntu system running on a 1.7GHz intel system with an ATi Mobility Radeon X600 card. I could help you with getting fglrx working and updating the video codecs and everything. You'll need patience when using Ubuntu though, I can't stress that enough :) In the end it pays out, if you stick around with it, there's a good chance you'll like it.

EDIT: For your purposes, I'd suggest trying a dual boot. Use BOTH Windows and Ubuntu. That's what I'm currently running. It helps for gaming and also if I mess up my internet connection or something in Ubuntu, I can switch to XP and read up on how to fix it.

---

### Post by ImALittleTeaPot on 2007-12-14
> Without drivers: Blocky, noisy, unsharp and scaling issues
With restricted drivers: Blocky, noisy, unsharp and scaling issues
With Ati drivers installed with envy: Blocky, noisy and unsharp


I think I'm having the same problem as you.  I have an ATI Radeon X1950XT, but I'm not sure if the card is the problem. If I don't use drivers, video is blocky, and audio has a fuzzy/"computer nioise" quality.....and same if I do use the drivers. And since the audio problem remains regardless, I have no clue what it is.  And as far as viewing video without hardware acceleration, should be no problem (I"m referring to streaming video, not DVDs). 

Also, I didn't think that catalyst worked in ubuntu anyways.

---

