---
title: "Resolution Problems on New Dapper Install"
date: 2006-06-03
forum: Multimedia &amp; Video
---

### Post by iceswimmer on 2006-06-03
Hello everyone.  Long time reader, first time poster.  I have a Gateway M305 capable of displaying 1024x768 resolution at a refresh rate of 60.  When I go to the screen resolution menu, 800x600 is the highest it will go, and the refresh rate is stuck at 72.  I have ran through

sudo dpkg-reconfigure xserver-xorg

countless times, trying different drivers (although i810 is what is supposed to work), and other options to no avail.  I have also looked over my xorg.conf file multiple times, and everything looks as if there should be no problems at all.  I heard about 915resolution, so I installed it and tried to get it running, also to no avail.  I'm not exactly sure I set 915resolution up correctly, but then again, I tried doing my research and tried setting up 915resolution in many different ways, thinking that I might have messed up somewhere.  :-k 

So far I have dealt with setting up wireless, ati graphics cards, network printers, and all sorts of other "difficult" tasks in linux, but I had to break down and post on this one.  I know there are a lot of posts on similair topics already, but I cant get this to go for the life of me.  Any help would be appreciated, and maybe someone who has dealt with integrated graphics successfully could post a detailed step by step guide to help us all?  Thanks in advance. ;)

---

### Post by iceswimmer on 2006-06-03
One more thing perhaps someone could help me with...  I just tried playing sauerbraten (open source 3d shooter).  It started at 20-something fps, and eventually went down to about 2 fps.  I'm kind of thinking once the resolution gets figured out then the fps will as well, but let me know if I'm wrong.  Thanks.

---

### Post by jwl007 on 2006-06-09
A simple search for "Gateway M305" produced these other posts on Ubuntu's formums:

[http://ubuntuforums.org/showthread.php?t=174463&highlight=gateway+m305](http://ubuntuforums.org/showthread.php?t=174463&highlight=gateway+m305)
 	
[http://ubuntuforums.org/showthread.php?t=118614&highlight=gateway+m305](http://ubuntuforums.org/showthread.php?t=118614&highlight=gateway+m305)
 	
[http://ubuntuforums.org/showthread.php?t=117379&highlight=gateway+m305](http://ubuntuforums.org/showthread.php?t=117379&highlight=gateway+m305)

Likewise, if you google "Gateway M305", you will notice similar posts for other distributions such as Fedora, SuSe, et. all.

I've done a lot of looking into this issue with my gateway m305 as well, and it seems that this is a somewhat complex issue dealing with Gateway specific Intel 810 graphics chipset, Xserver, and the shared memory.

I've also tried everything you mentioned including the 915resolution as well as updating the bios, reconfiguring X, I even tried the demo of a commercial XServer others have had luck with (see: [http://www.xig.com](http://www.xig.com), XIGraphics)

Unfortunately I think Gateway M305 owners are up a crick without a paddle.
However, if you find anything, let me know, will ya? ;)

---

