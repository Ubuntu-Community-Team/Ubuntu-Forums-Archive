---
title: "two screen widths from same monitor on web page"
date: 2010-11-30
forum: Multimedia Software
---

### Post by johnmay on 2010-11-30
It is quite interesting really, and I am interested in the video.
I have apache set up on my 10.04 64 bit system. I am serving a web site that I am developing and I have noticed a situation that Alice might describe as curious.

When I access the site from the domain name, I get 1024 screen width. when I access the site locally with my computer name, I get 1264 screen width. The image actually changes, and I of course prefer the larger width.

The 'curiouser and curiouser' part is that the native driver will only show the monitor as 1024 as the largest possible width. I have a dual monitor, and while one is at 1960, the other is limited to 1024 in the current setting. 

It is capable of 13xx when the nVidia driver is installed. (I was not happy with the screen settings available in their driver.) 

So, somewhere, there is a file/setting/routine which allows for the larger res to be seen, if only through a locally accessed website. I have looked in the /etc/x11 files and folders and nothing screamed at me. If there are any suggestions about where to look under the hood to get the larger image for more or most and hopefully all the time, even through firefox. 

Thanks!

I am using an nVidia GeForce:

lspci -v -s 03:00.0
03:00.0 VGA compatible controller: nVidia Corporation G73 [GeForce 7600 GS] (rev a1)
    Subsystem: eVga.com. Corp. Device c549
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at b1000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at b0000000 (64-bit, non-prefetchable) [size=16M]
    I/O ports at 1000 [size=128]
    Expansion ROM at <ignored> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: nouveau
    Kernel modules: nvidiafb, nouveau

---

### Post by johnmay on 2010-12-01
Here are two images of what I ma talking about. The desktop extents much further than the visible portion, for both width and height. This suggests that the code for the larger desktop has already been written, is in place, and I just need to tweak some settings. 

In short, if the lsd that I am seeing is 14 x 22 in, and ubuntu is generating a desktop of 18 x 26 inches, then why am I limited to a 1024x768 display? In most situations? 

The first pic, the logo is in the center of screen, and the black represents, I guess part of the Bermuda Monitor. The second, I have pushed the logo to the left and top as far as it will go, and that apparently is what my computer thinks is the display limit. 

I would like to get suggestions regarding the weirdness, to fix it for one, and cause I don't like pure darkness hanging around just out of sight. 

[ATTACH]177080[/ATTACH]

[ATTACH]177081[/ATTACH]

---

### Post by johnmay on 2010-12-02
Well, just for fun, and because I got new information regarding the issue, I thought I would post again. HAHAHAHA!

I was at the coffee shop, and used VNC to remote into the desktop I keep mentioning in the thread. The remote desktop had two interesting behaviors which apply to my question. 

The first: The desktop that opens is the 'smaller' (1024) even though the larger (1920) is the primary desktop when I am logged on physically. Also, the VNC provided th larger pixel 'workarea' because when I moved  a web page to the top of the VNC viewer, upon returning to the physical machine, the top of the window was out of the viewable area. 

Does anyone know the binaries that run the video? I would really like to start banging my head against metaphorical trees, because the neighbors are complaining about my Charlie Brown routine. AARRGGHHH

---

### Post by johnmay on 2010-12-04
Awesome! 

As I guessed, the answer was there somewhere...

Found it here: [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

and used the  xrandr --addmode VGA-2  command to fix the resolution. 

Now, I am using the nVidia card with the default driver and the system is rockin!

I also just found out that the problem I have seen some in other threads regarding movie player not being supported in larger resolution has been solved as well. 

So for anyone who has a problem with totem/movie player I am now able to use it full screen at 1920x1080 with no image problems at all. Guess I will have to start viewing in hidef!

Ubuntu ROCKS!

Thanks!

---

