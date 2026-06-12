---
title: "MythTV double image/corruption"
date: 2008-09-22
forum: Multimedia Software
---

### Post by incrediclint on 2008-09-22
Been searching all over for a fix for this. First when viewing live tv it would freeze up. ONLY in mythtv though. Totem playing the stream worked fine. 

Then I installed the latest driver from ATI for my card and that problem went away but a new problem was introduced. 

In fullscreen 1080 I get this image: [img]http://img218.imageshack.us/img218/9454/dsc00030di6.th.jpg[/img]

If I use -geometry 1919x1079 the double screen garbleygoo clears up however when i watch live tv i get 2 images stacked horizontally. 

If I use -geometry with any other res (1024x768) that is smaller then my desktop everything is fine. 

If I change my desktop to 1024x768 and run mythtv fullscreen i get corruption again, no double image but the screen is smeared diagonally. 

PVR-250 
ATI x1550 AGP with latest driver from ati (8.9, but ATI control panel shows it as 8.5x) 
Ubuntu 8.04LTS 
Mythtv .21 

Everything plays fine in all other players on the system, including XBMC.

---

### Post by incrediclint on 2008-09-22
Thought I'd add that switching to opengl presents other problems:

Loading screen remains unchanged, same corruption. Once the skin is loaded though it displays fine until I watch live tv... then there is sound but no image, the menu stays on screen.

---

### Post by LinuxPS2 on 2008-11-17
I too have the same problem... weird thing is with my old ati graphics card this didn't happen... its only once i updated from the old 9800se to my new HD3870 that it started having problems (well i guess its a whole new rig, mobo, proc, ext... but the same tuner cards) I am running two Win-TV-Go-FMs (yes they are shitty i know but my AMD 9950 should be able to handle the load if my old 3400+ could)...

Here's my desktop

---

### Post by aviynw on 2008-11-23
I too have this problem with my ati 9550/x1050 card with intrepid 8.10 installation.  I've tested it with the proprietary ati drivers 8.54.3 and 8.55.something.  I've found that a number of people have had this problem online.  
One example:  [http://www.phoronix.com/forums/showthread.php?t=10940&page=8](http://www.phoronix.com/forums/showthread.php?t=10940&page=8)

I have one line added to my xorg.conf in the "device" section
Option	    "TexturedVideo" "on"

Unlike most people with this problem, for me playing the troubling program at a lower resolution yields the same split screen / double screen.  So far the only program I've found to have this problem is mythtv.  The problem is consistent when I attempt to watch tv but when I watch a dvd I get different results depending on the part of the dvd I am watching.  On the two dvds I tested one is split the whole time, while the other is split only during the intro and the rest of the movie plays fine.  What does this say about what is causing this?  I've seen in related threads people mention vertical synchronization.  I've tried mythtv with opengl synchronization both on and off yielding the same results.  What else can I try?
thanks.

---

### Post by LinuxPS2 on 2008-11-24
i wonder if there is a way to "trick" mythtv to thinking there is only one monitor - when i ran it with only one monitor configured i did not get the same error w/ the same hardware... of course i also tried 32-bit ubuntu instead of 64-bit... time to try 32-bit w/ 2 monitors...

---

### Post by SteveGodfrey on 2009-01-14
Hey aviynw did you ever fix this?

---

### Post by AKADAP on 2009-01-14
Same problem on HD4850.
I think we need to wait for the next update to the ATI drivers.

---

### Post by Pat Reynolds on 2009-01-30
I had the same problem when I updated driver for ATI graphics Raedon 3200.
Resolved by changing the Playback Profiles in Mythtv set-up.
See the answer in full as posted by "Davmac" at 

[http://davmac.wordpress.com/2008/04/06/ati-driver-woes/](http://davmac.wordpress.com/2008/04/06/ati-driver-woes/)

Hope this helps.

Pat R

---

### Post by leprasmurf on 2010-03-12
That source link is all well and good but alot of unnecessary information.  The short answer is that deinterlacing is causing the problem.

Digging around with google I finally found that in mythtv 0.22 you have to set the deinterlace by going to "Utilities/Setup > Setup > TV Settings > Playback".  You then go to page three and modify each playback profile to a different deinterlace setting (I used Greedy HiMotion where I could and linear or One Field where I could not).  This has solved the problem for me.

---

