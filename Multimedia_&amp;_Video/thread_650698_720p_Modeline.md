---
title: "720p Modeline"
date: 2007-12-26
forum: Multimedia &amp; Video
---

### Post by hairryjones on 2007-12-26
I have an [Envision L32W661 HDTV]("http://envisiondisplay.com/products/specsheets/l32w661-specs.pdf") connected by VGA to a [fitPC]("http://www.fit-pc.com/new/fit-pc/specification.html") running Gutsy. I am using the "amd" drivers. I have set the correct horizontal and vertical sync rates in my xorg.conf. However, I have not been able to use a widescreen resolution. When I try to use a custom modeline to get a higher resolution, the monitor gives me a "Mode Not Supported" message, and I can't see the login screen or a tty. When I log in, however, Ubuntu defaults back down to 800x600, and I have a chance to fix my xorg.conf so that I can get back up to 1024x768. I've hooked up the monitor to a different machine, and on Windows, using the Intel GMA driver, the resolution goes all the way up to 1360x768@60hz, however, when I boot to Ubuntu and run X -configure, it detecs the hsync and vrefresh properly (31-60, 50-75), but still defaults to 1024x768, and when I try to use a custom modeline, I still get the "Mode Not Support" message from my monitor.

I'm assuming that the Intel drivers know something about the monitor and what modes it can use that I don't. I tried several modes from [http://www.mythtv.org/wiki/index.php/Modeline_Database](http://www.mythtv.org/wiki/index.php/Modeline_Database), though I don't understand why there are so many different 720p modes, as well as modes I've found on forum posts and modes from online generators, such as [http://xtiming.sourceforge.net/](http://xtiming.sourceforge.net/) and GTF.

So: Why are there so many different ATSC 720p Modelines? How come a monitor that should be able to display 720p and above complains when I try to use a 720p mode? How come the Windows Intel GMA driver know what mode to use while X doesn't? Can anyone suggest a modeline I should try? Is this a mode issue at all, or am I not getting something? And, more generally, how can I get the monitor to display full resolution under X? Also, would a different monitor give me fewer problems? I'm currently looking into an LG-M3201C-BA.

Here are my [xorg.conf]("http://pastebin.ca/833064"), with a few modes I've tried commented out, and my [Xorg.0.log.old]("http://pastebin.ca/833069") from the last time I started X with a custom modeline. Any help would be very much appreciated.

---

### Post by hairryjones on 2007-12-27
I plugged the monitor back into the computer with the Intel card and got the following in my Xorg.0.log:
> (II) I810(0): Printing DDC gathered Modelines:
(II) I810(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) I810(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(II) I810(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) I810(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(II) I810(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) I810(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) I810(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(II) I810(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) I810(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) I810(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(II) I810(0): Modeline "1360x768"   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync
However, the Intel driver on that computer didn't recognize the "1360x768" modeline when I tried it, so I tried it on the fitPC. It recognized it, but when I restarted X I got a "Mode Not Support" message from my monitor again. Does this mean that the DCC information is invalid? Is there somewhere I can go to get more information about this? Here is the [Xorg.0.log from the Intel card-equipped PC]("http://pastebin.ca/833889") and here is the [Xorg.0.log from when I tried the "1360x768" modeline]("http://pastebin.ca/833895").

---

