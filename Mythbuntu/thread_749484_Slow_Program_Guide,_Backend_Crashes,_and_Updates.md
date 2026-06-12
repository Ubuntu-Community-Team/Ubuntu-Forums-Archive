---
title: "Slow Program Guide, Backend Crashes, and Updates"
date: 2008-04-08
forum: Mythbuntu
---

### Post by Mrbbad on 2008-04-08
I decided to merge all of my teeth-grinding issues into one post here.  Before that, I'll list my specs here:

Dual-core AMD processor, 1GIG RAM, 330GB HD space (2 hard drives), external DVD drive, Sabrent TV Tuner (saa7134 card=42 tuner=2), on a BIOSTAR TF7050-M2 motherboard with an integrated NVIDIA GeForce 7050 PV graphics card.  All running the latest MythBuntu 8.04 BETA, updated via update manager just once.

 [B][SIZE=3]Slow Program Guide Browsing [/SIZE]
[/B]I know there are issue with channel changing being slow, but this isn't that.  I'm talking strictly about the program guide browsing, in theory a simple task, up and down, look at what's on, but for some reason it moves ungodly slow, even lagging up to a good 5-10 seconds just to go from one block of text to another.  

Whatever could cause this?  All it's doing is cycling through simple data (I guess, not a programmer), I don't even know where to begin in diagnosing why the program guide is laggy.


[B][SIZE=3]Updates[/SIZE]
[/B]Yes, I'm currently using MythBuntu 8.04 BETA.  I also used the 7.10 series, and I tried the 8.04 ALPHA.  Regardless of alpha/beta/standard I run into the same problem repeatedly:  _**UPDATES KEEP BREAKING MY MYTHBUNTU SYSTEM**_.

In fact, the reason I tried 7.10 then 8.04 ALPHA then 8.04 BETA was because on each updates broke my system and I had to reinstall.

I'm not talking about the strange NVIDIA resetting display issue.  That isn't a problem, I can get that back in order in no time.  I'm talking about:

- Sound stops working after update; ripped my hair out on this one, had to reinstall, getting sound to work in Linux is a nightmare I couldn't google or anything.
- HAL errors occurring after update.  
- MythBuntu corrupting random database areas after update.
- MythBuntu breaking in whole after update, forcing a complete uninstall and reinstall of MythTV itself. 

Seriously, [COLOR=Red]**I live in fear of updating! **[/COLOR] After I installed 8.04 BETA this go-round (if you're really interested, I wrote it all up [here]("http://tf2.org/?q=node/187")) I updated ONCE because I had to for known stability improvements.  But at this point putting aside a laggy program guide and random backend crashes I've NO INTEREST in updating PERIOD.  I'm tired of reinstalling MythBuntu.

[SIZE=3]**Backend Crashes **[/SIZE]
I actually created a perl script to check the backend every 30 seconds to see if it's running, and to relaunch it if it is not.  Otherwise I'd have to SSH in and manually mess with that.

[B][SIZE=3]Final Comments[/SIZE]
[/B]I'm not doing anything unusual here, that I am aware of anyways, all I'm doing is using it normally and it breaks itself...

...for now I'd just be happy to figure out how to solve the laggy program guide...

---

### Post by laga on 2008-04-10
Slow program guide browsing:

Do you have any frame-doubling deinterlacers like bob2x enabled?
Is your frontend running with realtime priority in the video display thread?
Do you have references to channel icons in your database which don't exist on the file system?

Updates:
I've addressed that in another post. But I guess I forgot to mention that backups can be helpful, too :).

Backend crashes:
Report them! Segfaults just be caught by apport. Try playing with 'apport-cli' if you don' get a nice message asking you to report a bug.

> 
I'm not doing anything unusual here, that I am aware of anyways, all I'm doing is using it normally and it breaks itself...

Yeah, except for running a beta release and expecting 100% stability, there's nothing unusual here :)

---

### Post by Mrbbad on 2008-04-10
Yep, granted, it is beta as you said.

Interestingly, it isn't all that bad.  It just seems to get really out of whack with things having to do with the TV aspect.

I'm going to snoop around with your ideas in mind later and see what I find...after work...

Say any jobs for installing MythBuntu systems?  I'm a pro-ish now!  :) *G*

---

### Post by laga on 2008-04-10
> **Mrbbad said:**
> Yep, granted, it is beta as you said.

Interestingly, it isn't all that bad.  It just seems to get really out of whack with things having to do with the TV aspect.


Yeah, some of the multimedia things in the kernel can go wacky during a cycle, eg the sound. I was affected by that as well..

> 
Say any jobs for installing MythBuntu systems?  I'm a pro-ish now!  :) *G*

We always need beta/RC testers.. it doesn't pay a lot (read: nothing), but it's so good for your karma!

---

### Post by mikedirl on 2008-04-13
Slow Program Guide

I had issues with my program guide being slow recently.
It turned out the problem was that I renamed the folder with my channel icons and I had my guide setup to show icons. The guide still worked but was very slow and unresponsive. Try turning off the feature to show channel icons in the Program Guide settings to see if it makes a difference.

---

### Post by derrick81787 on 2008-05-01
I have the same problem with the slow program guide.  I also have channel icons installed, and after reading this, I think that may be the problem.  I'm running MythBuntu 7.10 (installed when a beta, but constantly upgraded).  Does anyone know how to remove the channel icons?  I really don't need them and would much rather have a more responsive program guide.

Mrbbad,

You may also like to know that I upgraded to Xubuntu 8.04 on my desktop whenever it was in alpha, and my sound died a lot too.  I think it was a core Ubuntu problem when Hardy was in the development cycle, and probably not an actual MythBuntu problem.  That is, unless this is still happening, in which case I have no idea what's going on.

---

### Post by uncle hammy on 2008-05-02
FWIW, I also have an issue with the slow program guide, with no channel icons.  

I am using the CPU+ display profile, and I realzied that the program guide is only slow when I am viewing a SD channel (which due to the profile is displayed with ffmpeg) and open the guide, when I am currently viewing an HD channel (which due to that profile is displayed using XvMC) the guide works fine.

---

### Post by derrick81787 on 2008-05-03
> **uncle hammy said:**
> FWIW, I also have an issue with the slow program guide, with no channel icons.  

I am using the CPU+ display profile, and I realzied that the program guide is only slow when I am viewing a SD channel (which due to the profile is displayed with ffmpeg) and open the guide, when I am currently viewing an HD channel (which due to that profile is displayed using XvMC) the guide works fine.

Yeah, I figured out how to remove the icons, and it didn't really help any.  Here's a link to the discussion on the mythtv-users mailing list, which also has a link to the bug report.

[http://www.mythtv.org/pipermail/mythtv-users/2008-January/207138.html](http://www.mythtv.org/pipermail/mythtv-users/2008-January/207138.html)

From the bug report, it looks like changing the deinterlace settings might help.  I'm not home right now, but I think I'm using the BOB deinterlacing method, which is mentioned in the report.  Whenever I get back, I'll have to change the settings to use some other method and let you all know what happens.

At least it looks like the developers are aware of the situation.

*****Edit:**  You were mentioning that it only happens to you in SD and not in HD.  That further supports the deinterlacing theory because I think that HD content is already deinterlaced.  Therefore, your deinterlacing settings would only have any effect on SD channels.

---

### Post by uncle hammy on 2008-05-08
I don't htink that's true, because if I turn off deinterlacing on my HD setting in the display profile, the picture is badly interlaced with saw tooth edges.  

Someone will probably correct me, but I think it's going to boil down to your display.  I am displaying on a 720p tv, so I need to have it deinterlaced because it's a non interlaced display.  What I don't know is what effect the broadcast itself has, and how it gets encoded.  All the stations in my area broadcast in 720p, I am displaying 720p, yet without deinterlacing, it's bad.  With deinterlacing, it looks great.

---

