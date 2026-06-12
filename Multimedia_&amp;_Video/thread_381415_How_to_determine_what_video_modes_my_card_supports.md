---
title: "How to determine what video modes my card supports"
date: 2007-03-10
forum: Multimedia &amp; Video
---

### Post by paulm on 2007-03-10
I have a Nvidia Riva TNT2 (ultra I think) card and am thinking of getting a new LCD monitor.

Can anyone tell me how to determine what video modes my card will support?

Obviously I can see the list in System->Preferences->Screen resolution but I suspect that this list is a list of the modes that **both** the video card and the monitor support. 

My current monitor is a CRT that does a maximum of 1600x1200 and I am looking at widescreen LCD that does 1680 x 1050.

If I grep my Xorg log for that resolution I see

(II) NVIDIA(0): Not using default mode "1680x1050" (width too large for virtual size)

but I am not sure if the "width too large for virtual size" means the card doesn't support it, or it isn't supported in conjunction with the monitor (or something else!)

---

### Post by jellyfisharepretty on 2007-03-11
Can you post the contents of /etc/X11/xorg.conf ?

I think that certainly your video card should be able to produce that resolution, however maybe the X server settings are not configured properly.

---

### Post by paulm on 2007-03-12
A copy of my xorg.conf is [http://paulmcgarry.com/stuff/xorg.conf]("http://paulmcgarry.com/stuff/xorg.conf")

I just added the 1680x1050 bits to the

Modes		"1680x1050" "1600x1200" "1024x768" "800x600" "640x480"

lines.

Now when I start the log file says

(WW) NVIDIA(0): Not using mode "1680x1050" (width 1680 is larger than
(WW) NVIDIA(0):      EDID-specified maximum 1600)

which I think happens because my current monitor won't support it.

---

### Post by jellyfisharepretty on 2007-03-12
Well, you may be right.  Your xorg.conf looks okay.  Are you trying to do this still with your CRT, or are you trying it with your new LCD monitor ?

A way to verify the supported modes of your monitor is to go on the manufacturer's website.  They usually lives the specifications for their products.

Maybe you also want to look at the NVIDIA's drivers documentation.  If you are sure your monitor supports it, you have some options to force it to do 1680x1050 :

[http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9746/README/appendix-d.html]("http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9746/README/appendix-d.html")

---

### Post by paulm on 2007-03-13
I haven't bought the new monitor yet, I wanted to check before I spent the money :)

I'm pretty confident it will all work now.

---

