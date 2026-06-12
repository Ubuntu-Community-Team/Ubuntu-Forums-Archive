---
title: "Mouser cursor corruption on xinerama"
date: 2006-08-02
forum: Multimedia &amp; Video
---

### Post by mac on 2006-08-02
Hello;

I hope that some one can help on this. I did enable xinerama on my notebook so that I can have 2 monitor as one big screen, but the problem is that in my second screen (LCD monitor) the mouse pointer gets corrupted since it becomes a square of around 1 in. per 1 in.; but as soon that I move the mouse to my first screen (notebook) the mouse pointer becomes normal.

It only gets corrupted when I move the mouse to the second screen.

I have Ubuntu 6.06 AMD6 with an ATI Radeon 9600, I'm using the latest ATI drivers.

Thanks
Mario

---

### Post by marshallfox on 2006-10-07
Having similar problem here... did you find any solution?

marshall

---

### Post by mac on 2006-10-07
> **marshallfox said:**
> Having similar problem here... did you find any solution?

marshall

Marchall
I did remove xinerama setup and second video card/monitor from my xorg.conf, instead of xinerama I'm using ATI's big desktop, which I did enable adding the following lines to my device section:
	Driver      "fglrx"
	Option "VideoOverlay" "on"
	Option "OpenGLOverlay" "off"
	Option "MonitorLayout" "LCD,CRT"
	Option "MergedFB" "True"
	Option "OverlayOnCRTC2" "true"
	Option "CRT2Position" "RightOf"
	Option "DesktopSetup"  "horizontal"
	Option "MetaModes" "1280x800 1280x800-1280x1024"
	Option "Mode2" "1280x1024"

Hope that it help you.
mac

---

### Post by lehjr on 2006-10-19
I had that problem running Fedora Core 5 with xinerama. The fix was to simply to change the values for HorizSync and VertRefresh to the correct values for each display8) .

---

### Post by JojaCoder on 2007-01-04
> **mac said:**
> Marchall
I did remove xinerama setup and second video card/monitor from my xorg.conf, instead of xinerama I'm using ATI's big desktop, which I did enable adding the following lines to my device section:
	Driver      "fglrx"
	Option "VideoOverlay" "on"
	Option "OpenGLOverlay" "off"
	Option "MonitorLayout" "LCD,CRT"
	Option "MergedFB" "True"
	Option "OverlayOnCRTC2" "true"
	Option "CRT2Position" "RightOf"
	Option "DesktopSetup"  "horizontal"
	Option "MetaModes" "1280x800 1280x800-1280x1024"
	Option "Mode2" "1280x1024"

Hope that it help you.
mac

It helped me, but I can't get different resolution on my screens. I want 1680x1050-1600x1200 but get 1680x1050 on both. Both LCD.

In the Xorg log I get:
fglrx(0): Option "MetaModes" is not used

Everyhing looks ok with fglrx-driver as far as I can see!

---

### Post by mac on 2007-01-04
JojaCoder;

Since I've an ATI video card I did setup ATI's big desktop and with it I can have a different resolutions on my monitors.

I've ATI's drivers, I don't know if this works with open source drivers. If you want to setup big desktop try following instructions form this post: [http://ubuntuforums.org/showthread.php?t=301941&highlight=ATI+big+desktop](http://ubuntuforums.org/showthread.php?t=301941&highlight=ATI+big+desktop)

MAC

---

### Post by bunyip on 2007-02-15
mac,
hope you don't mind if i add my experience wth this issue, hopefully somebody will find it useful...
I've got a HP nx6125 laptop with 200M chip running fglrx drivers.
laptop lcd is 1400x1050
external lcd is 1280x1024.
xinerama with different resolutions gives me the corrupted cursor.

setting Option "SWcursor" "on" in device section gives me a good cursor but with artefacts when the image beneath the cursor changes. eg dragging a window.

xinerama with both screens running at 1280x1024 works fine.

mergedfb gives me a good cursor but two seperate desktops.

The Ati/linux bug entry is [here.]("http://ati.cchtml.com/show_bug.cgi?id=544")

---

### Post by itsdaveperdue on 2007-04-25
bunyip!

I've been searching for hours!

I have the exact same setting as you!  My nx6125 laptop is having issues with the external display.  Is it still working for you in Feisty?

Can you please send me your xorg.conf so I can see what I'm doing differently?

Thanks!

---

### Post by fadetoblack82 on 2007-06-21
> **lehjr said:**
> I had that problem running Fedora Core 5 with xinerama. The fix was to simply to change the values for HorizSync and VertRefresh to the correct values for each display8) .

im having the same issue.. how do i find the values for horizsync/vertrefresh, and how do i find out the correct values?

thanks

---

### Post by optimarcus_prime on 2007-08-20
Anyone find anything for this issue?  I've got the same deal going on?

---

### Post by mac on 2007-08-20
I did fix my issue a while back ago.

Here I did post how to setup xorg.conf to have 2 monitors in feisty it works on gutsy too, but the post is in spanish, anyway you will see there the sections device and display, use them as a guidelines to setup your xorg.conf file

[http://mario-chavez.blogspot.com/2007/05/configurar-x-server-para-2-monitores.html](http://mario-chavez.blogspot.com/2007/05/configurar-x-server-para-2-monitores.html)

Mario

---

### Post by travelinman on 2007-09-23
Anyone ever figure this out I can't keep my mouse from being corrupted on my TV which is my secondary display

---

### Post by HyperHacker on 2008-04-18
Yep, same problem with a Radeon 9550. The instructions in [this thread](http://ubuntuforums.org/showthread.php?t=301941&highlight=ATI+big+desktop) only made things worse. aticonfig tells me "unable to open display `'" and then I just have one image mirrored across both screens or (seemingly random) X starts in "low graphics mode". On the right screen the cursor becomes a big square bunch of random pixels from the left screen. There are a bunch of similar problems with redrawing windows. If I open a terminal on the right screen it also frequently gets drawn at the same spot on the left. Sometimes the contents of other windows get drawn in it.

I've spent the past 6 hours or so Googling things and trying just about every solution imaginable, switching drivers and changing options in xorg.conf and running and installing things that don't work and this is the closest I've been able to get to actually working. This is before I even think about getting 3D or compositing to work. I can use the SWcursor option and then the cursor looks fine but when I drag windows around they get corrupted, and it doesn't fix the terminal redrawing issues.

Also people keep referring to "the device section" in xorg.conf, as if there should only be one. I seem to have two or three.

---

