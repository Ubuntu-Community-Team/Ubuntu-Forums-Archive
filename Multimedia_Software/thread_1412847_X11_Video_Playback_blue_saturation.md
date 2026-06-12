---
title: "X11 Video Playback blue saturation"
date: 2010-02-21
forum: Multimedia Software
---

### Post by mmillman on 2010-02-21
Ok, so here is my problem.  I have followed all the tutorials and guides that I could find, but I am still having DVD playback issues...

When trying to playback DVDs in VLC media player, I have to switch the video output driver to get any playback.  If I leave it on "Default" (which I think is defaulting to "XVideo Extension Video Output"), I get a solid green or blue screen (which I also get with "Xvideo Extension Video Output")...

If I switch it to "OpenGL Video Output", I get proper DVD playback but it is kind of pixelated and ugly... see attached screenshot.

If I switch it to "X11 Video Output", I get DVD playback that is very crisp and sharp, the image quality is great... unfortunately, the colors are completely messed up and the blue is completely saturated...  I've played with the color settings (especially the Hue setting), but I can't get the colors to look right...

I'd really like to use the x11 video output since the quality is the best, but I can't get the colors right... can anyone help?

See the attached screenshots... the first one (Screenshot.png) is OpenGL output, and the second (Screenshot-1.png) is X11 output.

It's also worth noting that I am on an IBM ThinkPad R32 with an ATI Mobility Radeon 7000 (or M6, or M6 LE, whatever you wanna call it).  I'm running a fully updated 9.04 Jaunty installation.

Here is a copy of my Xorg.conf in case it matters:
```
Section "Device"
	Identifier	"radeon"  
        Driver		"ati"
        BusID		"PCI:1:0:0"
	Option          "AccelMethod"   	"XAA"
	Option          "EnablePageFlip"	"true"
	Option          "TripleBuffer"  	"true"
        Option          "AGPMode"		"4"
	Option		"DRI"			"true"
	Option		"AGPFastWrite"		"yes"
	Option		"RenderAccel"		"true"
	Option		"DynamicClocks"		"true"
	Option		"BIOSHotkeys"		"true"
EndSection 

Section "Monitor"
        Identifier      "Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "radeon"
        Monitor         "Generic Monitor"
        DefaultDepth    16
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection
```

---

### Post by andyt05 on 2010-02-21
Try this out:

[http://ubuntuforums.org/showpost.php?p=5760573&postcount=3](http://ubuntuforums.org/showpost.php?p=5760573&postcount=3)

Changing the default video output to "X Window System (No Xv)" solved the problem for me.

---

### Post by mmillman on 2010-02-22
No such luck...

X11 Video output is still completely saturated blue (but with perfect quality otherwise)

OpenGL Video output is still perfect color wise (but completely pixelated and ugly otherwise)

XVideo output is still a solid green or blue screen with no video at all.

I tried to use xine-ui to see if it made a difference, but it's the same story with the exception that the quality in OpenGL is SLIGHTLY better...

Any other ideas????

It's also worth noting that I have all desktop effects turned off...

Another thing that I find strange is that when searching the internet, it seems that everyone says that for them the "X11 video output" is blocky and ugly, but for me it seems that its the exact opposite of that (opengl is the one that is blocky and ugly).

Any other help would be great... I'm very comfortable running commands from a terminal so feel free to post any suggestions.

Edit:

I just realized that "X11 video output" is very slow even though the quality is very good...

So my new goal is to get the "XVideo extension video output" to show something other than a solid green screen...

---

### Post by mmillman on 2010-02-24
I'm bumping this...

I've tried absolutely everything I could find online, to no avail...

I've changed the hue settings in totem: no luck
I've changed the video output to "X Window System (no Xv)": no luck
I've used custom pipeline settings in gstreamer-properties: no luck

Does anyone have a solution for this???

It's worth noting that I am using the open-source radeon driver (ati wrapper).

:confused:

Help!

---

### Post by mmillman on 2010-02-25
I just want to bump this one more time to say that I partially fixed this on my own...

I say partially, because the X11 video output (X Window System (No Xv)) is still tinted blue and I can't fix that no matter what I do... however, I got the Xv working right....

Turns out that my gstreamer is detecting 2 different "devices", and if I manually force it to use the second device ("device=1"), it works just fine... I'm not at the computer now, I think the two devices were something along the lines of "ATi Video Wrapper" and "Radeon Textured Video" or something like that... only one of them worked so i just force it to that one and everything is fine.

Update:

Ok so I found the REAL problem...

The real problem is that I had my depth set to 16bpp as opposed to 24bpp...  The reason is that on this card (the M6/7000/any other RV100 based chip), 16bpp gives MUCH better performance than 24bpp... therefore I made a custom xorg.conf using 16bpp...

That's all great and good... however the open source ati driver (at least the one in Jaunty) doesn't play well with Xv in 16bpp...

If I set my depth to 24bpp, I get perfect playback from both devices that I mentioned earlier (both "ATI video overlay" and "Radeon textured video")... as a matter of fact... with 24bpp depth on, the "ATI Video Overlay" (device="0") actually renders video much better than the Radeon Textured video (device="1") because it uses bicubic filtering and reduces screen tearing A LOT!!!!

It's really a catch-22... I can use 16bpp and get very good 3d performance with decent quality video playback (but with lots of tearing).
Or I can use 24bpp and get reduced 3d performance but with much better quality video playback (virtually no tearing)...

Quite a decision to make... I think I'll stick with the 24bpp and better video quality... i do much more video watching than I do 3d gaming anyway...  besides... with 24bpp I can actually use desktop effects! (on 16bpp, desktop effects make my windows all fudged up).

Que sera sera I suppose...

I hope this thread can help other people with this same card!

---

### Post by AndyCinDallas on 2010-02-25
I have the same thing happening - although mine occurs using an Nvidia graphics-card. 

The odd thing is that YouTube videos are perfect when played online - but once downloaded and played again, they turn blue. Weird.

---

### Post by mmillman on 2010-02-25
Unfortunately, I don't think my fix will work for you as I believe it is specific to my video chip... but I am willing to bet that one of the other methods will work for you since they seem to work for everyone else...

First, try opening up your preferences in totem (can't remember how to find them and I uninstalled totem since it's not working at all for me... sorry... but it should be pretty straight forward), and playing with the "hue" slider... try it set to 0 (all the way to the left), try it set directly in the center, and try it set all the way to the right... different people report that they need to move that slider to fix the color problem...

If that didn't work check this link and try the suggestions in there... one of them should work for you.
[https://answers.launchpad.net/ubuntu/+source/totem/+question/7373](https://answers.launchpad.net/ubuntu/+source/totem/+question/7373)

---

### Post by mmillman on 2010-02-26
Bumping this thread for updated problem/solution

---

