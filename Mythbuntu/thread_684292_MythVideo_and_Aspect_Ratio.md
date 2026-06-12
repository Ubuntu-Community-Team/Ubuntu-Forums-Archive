---
title: "MythVideo and Aspect Ratio"
date: 2008-01-31
forum: Mythbuntu
---

### Post by RFinn on 2008-01-31
I've been trying to use MythVideo to watch downloaded content. Anything standard definition (4:3, I assume) like a TV show displays great, but any widescreen movies (16:9, I guess) get squished and cut off. How can I fix this so that it displays in a letterbox format? I have the video player set to "Internal", so I'm not sure whether it's using Mplayer, Xine, or VLC. Thanks.

---

### Post by ubnewbie2 on 2008-02-01
Standard Definition does not necessarily mean it's 4:3.  Most of our SD content (in Australia) is 16:9 now.

You could try telling myth to use mplayer, and adjust the command line to get the required aspect ratio.  Sometimes it is counter intuitive.  I have a 16:9 flat panel, but I have to set everything in myth (and mplayer) to 4:3, then it displays correctly !!

---

### Post by reclusivemonkey on 2008-02-01
> **RFinn said:**
> I've been trying to use MythVideo to watch downloaded content. Anything standard definition (4:3, I assume) like a TV show displays great, but any widescreen movies (16:9, I guess) get squished and cut off. How can I fix this so that it displays in a letterbox format? I have the video player set to "Internal", so I'm not sure whether it's using Mplayer, Xine, or VLC. Thanks.

Press the "w" key (or whatever this is mapped to on your remote) and you can cycle through the aspect ratios available.

---

### Post by RFinn on 2008-02-01
Hmmm... When I hit W to cycle through the aspect ratios with the player settings set to "Internal" nothing happens, it brings up the box saying the different ratios, but nothing changes.

When I change it to "mplayer", It comes up as loading but all I get is sound, could it be displaying in the background, behind the myth front end?

If I use VLC and set it to display fullscreen on startup it works, but I lose remote functionality and I have to switch to the keyboard to get it to close, pause, or fast forward.

If i set it to xine, it displays in a window and I get odd sideways playback on some videos, but I get remote functionality.

---

### Post by ubnewbie2 on 2008-02-01
What sort of TV?  Modern digital sets can scale and convert the video.  Maybe it is causing the problem.

---

### Post by RFinn on 2008-02-01
It's a 5 year old JVC 27" CRT.

---

### Post by RFinn on 2008-02-01
So I found a post about a similar problem that suggested doing this:

"In the xorg.conf, I added the XVideo Enable option:

Code:
Section "Extensions"
 Option "XVideo" "Enable"
EndSection
Section "Device"
   .....
   # === Video Overlay for the Xv extension ===
   Option      "VideoOverlay" "on"
EndSection

Then I ran this:
Code: sudo aticonfig --overlay-type=Xv"


I gave it a shot and sure enough I can now toggle between aspect ratios with the Internal player (using W) and use regular commands in the player box (ie -fs, -aspect, -zoom, etc...). However, now regular 4:3 videos stretch so that I get a black bar at the bottom and crappy quality, and all of my videos display at the top of the screen with one large black box on the bottom, rather than in the center of the screen like normal

Help!

---

### Post by RFinn on 2008-02-03
OK, so I took out the extra code from my xorg.conf because it didn't seem to make things any better and am back to widescreen videos being scrunched into the screen. Anyone have any other ideas?

---

### Post by dman777 on 2008-02-22
Does this help any?

[http://forums.nvidia.com/index.php?showtopic=17158&st=260](http://forums.nvidia.com/index.php?showtopic=17158&st=260)

---

