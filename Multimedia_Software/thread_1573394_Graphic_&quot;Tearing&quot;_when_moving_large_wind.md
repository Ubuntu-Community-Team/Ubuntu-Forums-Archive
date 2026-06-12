---
title: "Graphic &quot;Tearing&quot; when moving large windows, video playback also having same problem."
date: 2010-09-12
forum: Multimedia Software
---

### Post by myandylai on 2010-09-12
I am new to Ubuntu. I start using Ubuntu from Karmic 9.04 starting with my HP laptop with Intel Dual-Core and integrated Intel graphic processor. Now using Lucid 10.04 so far all was out-of-box. Graphics and video run smooth.

My problem is now I put Ubuntu Lucid 10.04 into my desktop PC,

Core2Duo E8400
ASUS P5QL Pro
4GB DDR2
ATI HD 5670
SAMSUNG 2233SW (1920x1080)

and it is giving some minor "tearing" on gnome desktop. I don't know how to express the problem so I just call it "tearing". When I move a large window (like 3-4 times the size of "Calculator" in Ubuntu) it's like the upper part moving faster and the lover part like 0.1 sec slower and you can actually see a horizontal line appear. Or I should say it's like the window is breaking apart. I move the window faster and is more noticeable.

I can live with some "tearing" on my gnome desktop but when I playback video the "tearing" do happen if the scene moving fast and it is very annoying. I notice the "tearing" is there right after I finish install Ubuntu Lucid 10.04 before I enable "System > Administration > Hardware Drivers.

I need to explain that the video playback is smooth. Just there was some horizontal "tearing" when the scene moving fast. So I Google for answer and found lot of issue with ATI graphics. I just try all I can,

1. I upgrade my ATI Catalyst to 10.8 from ATI Website.

   fglrxinfo
   display: :0.0  screen: 0
   OpenGL vendor string: ATI Technologies Inc.
   OpenGL renderer string: ATI Radeon HD 5600 Series
   OpenGL version string: 4.0.10151 Compatibility Profile Context

2. I try put Kernel Options like "nomodeset" "radeon.modeset=0" in GRUB
3. I try use aticonfig --sync-vsync=on
4. I try use aticonfig --sync-video=off
5. I try play video with VLC 1.1.2 using "GLX Video Output (XCB)
6. I try gstreamer-properties and use
   X Windows System (No XV) - video choppy but the "tearing" still there
   X Windows System (X11/Shm/Xv) - Video smooth but "tearing" is there
7. I try put Option "AccelMethod" "EXA" into Device section of my /etc/X11/xorg.conf
8. I try put Option Option "RenderAccel" "off" into Device section of my /etc/X11/xorg.conf
9. I try put Option Option "XAANoOffscreenPixmaps" "true" into Device section of my /etc/X11/xorg.conf
10. I disable Compiz by "metacity --replace" "killall compiz compiz.real"
11. I put an old ATI HD 2600 XT into the system for testing (same problem)

After all the above didn't give me any luck. I come to ask for help here and see if someone using ATI cards having the same issue. If none then I will try my luck on Ubuntu 10.10 at October. Thanks in advance.

---

### Post by tuempeltaucher on 2010-11-20
Hello,

i know it's a old thread but I have exactly the same problem and I have pretty similar hardware, too. The only difference is that I have an ati 4850 card and a 24" 16:10 Samsung display.

Yesterday I fixed the problem, but after I booted the system today it's still happening. Yesterday I played with compiz settings and follwed the steps under (and maybe something else):

[http://www.*****************/driver/articles/fix-video-tearing-with-amd-proprietary-driver-on-ubuntu-10-10.html](http://www.*****************/driver/articles/fix-video-tearing-with-amd-proprietary-driver-on-ubuntu-10-10.html)

Did you have any luck?

---

### Post by strongface on 2010-12-09
I also seem to be having this problem.

I've installed the very latest version of the Proprietory ATI catalyst driver and I'm getting the flickering/tearing edges to windows when I move them fast around the screen.

Are there any threads that address this, or has anyone come across a solution?

Thank

---

### Post by ricky222 on 2010-12-09
I stopped video tearing when using VLC media player by selecting Open GL in tools, preferences, video, output and turning off Compiz, I changed it to Metacity using Compiz Fusion Icon, some times it starts again when I start to play a dvd but if I just switch back to Compiz then back to Metacity and restart there's no tearing, just two clicks of the mouse.

I do have ATI HD 3200 integrated graphics though and not a graphics card, also tried Compiz Switch, works to with just one click.  Also stopped video tearing using SMPlayer to open MPlayer, selecting Open GL, but it has to be played in full screen. Found it here, just scroll down to the bottom of the page,

[http://ubuntuforums.org/showthread.php?t=1616047&highlight=video+tearing](http://ubuntuforums.org/showthread.php?t=1616047&highlight=video+tearing)

---

