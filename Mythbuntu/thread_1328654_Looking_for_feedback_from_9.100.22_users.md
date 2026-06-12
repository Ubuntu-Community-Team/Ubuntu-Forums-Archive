---
title: "Looking for feedback from 9.10/0.22 users"
date: 2009-11-16
forum: Mythbuntu
---

### Post by laffinet on 2009-11-16
I am contemplating to upgrade (clean install) to 9.10/0.22 and am looking for some feedback from people that are using 9.10/0.22.

I'm currently running mythbuntu 9.04 with the avenard repos (which is obviously using mythtv 0.21), thus already using VDPAU (well, sort of, there are a few problems, but that's a different story).

I've done a fair bit of customisation, so an upgrade is a bit of work for me. 

After reading the release notes and various comments on different forums I am wondering: is it worth it ?

Any major new functionalities ?
Any major improvements that are too good to be missed ?

Thanks for any feedback.

---

### Post by OffAxis on 2009-11-16
What kind of a TV card do you have?

I have IPTV (network recorder) and 9.10 does not work at all.

Both coming off a working 9.04 and from a clean install.

Menus are pretty, though.

---

### Post by laffinet on 2009-11-16
I'm running two Leadtek tuner cards, which I know work fine under 9.10

---

### Post by mookie60 on 2009-11-16
8.10 and 9.04 ran very well on an older Dell Optiplex with 2.2ghz cpu, though not fast enough, as expected, to do HD.   recently picked up a new (used) HP with 3.6 ghz cpu hoping to do HD.   as the new machine's arrival coincided with the release of 9.10, I went ahead and setup the box with 9.10/.22 before pulling the tuners from the old machine.

things installed and ran well. . . . looked beautiful in fact, i was getting psyched to check out the new guis.    but, after swapping in the tuner cards (hauppauge 1600 & 150) i found the channel scanner wouldn't work.   the 1600's analog side scanned to channel 16 and would go no further, the digital tuner would not find any channels, just a bunch of "timed out" msgs.   i don't recall how the 150 scanned.

not sure whether to blame the new hardware, 9.10, or myth .22, i tried installing 9.04 and upgrading myth to .22 - same problem.   then tried 9.10/.22 on the old box - same problem.   

ultimately i just put 9.04/.21 on the new box and it works.   so that's where i'll stay for now.

john

---

### Post by laffinet on 2009-11-16
Interesting.

So far I have to say I haven't found any compelling reasons to upgrade. Maybe I'm missing something, but I haven't heard of any major new functionality or improvement that makes me want to go through the troubles.

---

### Post by rootytooty on 2009-11-16
I just received my CD today.  I was trying to run it on my Windows PC to see what it looked like and then make a memory stick of it to use for my eee pc 900.  I did this with the earlier version 8.10 ??? When  when I tried to run it on my pc it comes up and says something like "no video----).  This is in the demo/install mode.  But it happened in other modes also.

I will try to run the cd on my eee pc with my optical drive and see what happens.

Thanks,
Bobby

---

### Post by mbobak on 2009-11-17
> **laffinet said:**
> Interesting.

So far I have to say I haven't found any compelling reasons to upgrade. Maybe I'm missing something, but I haven't heard of any major new functionality or improvement that makes me want to go through the troubles.

And now, I'll give you a reason *not* to upgrade.

[Bug #453444]("https://bugs.launchpad.net/ubuntu/+source/rsyslog/+bug/453444"):  It's nasty.

Causes your /var/log/kern.log and /var/log messages to get filled w/ messages about CPU normal temp/CPU over temp, over and over again. Filled my 80GB root partition in about a day.

Worse, it'll peg your CPU at or near 100%, and it will suck up your I/O bandwidth, and you won't be able to watch a web video or do any mythtv recording playback w/o lots of choppiness audio dropping, etc.  I've worked up a simple little workaround, but, till this is permanently fixed, I can't, in good conscience, recommend 9.10.

You have been warned. :-)

-Mark

---

### Post by rootytooty on 2009-11-17
Are you talking about me with my Eee PC or answering someone else??? I am currently using Xandros with the easy desktop.

Are you saying that 9.10 is  no good???

Thanks,
Bobby

---

### Post by mbobak on 2009-11-17
Regarding that bug, here's a very temporary workaround, that should be ok till the proper fix is available in Karmic.

The following is a copy of what I posted in the bug report:
Hi all,

This bug has been a real pain in my backside.  I think I have a reasonable, short-term workaround.  I'm *not* suggesting this is a permanent fix for anyone, nor should this be applied to any source trees anywhere.

This is strictly for someone who, like me, is suffering because of this, and wants a slightly better solution than simply killing off logging systemwide till a proper patch is available.

Here's my hack:
--- /etc/init/rsyslog-kmsg.conf.orig	2009-11-17 01:40:07.000000000 -0500
+++ /etc/init/rsyslog-kmsg.conf	2009-11-17 01:42:36.000000000 -0500
@@ -18,7 +18,7 @@
     chown syslog:syslog /var/run/rsyslog/kmsg
 end script
 
-exec dd bs=1 if=/proc/kmsg of=/var/run/rsyslog/kmsg
+exec dd bs=1 if=`grep -v "CPU[0-7]: Temperature" /proc/kmsg` of=/var/run/rsyslog/kmsg
 
 post-stop script
     rm /var/run/rsyslog/kmsg

Or, for people who don't like dealing w/ patch files, go to /etc/init, make a copy of rsyslog-kmsg.conf.  Then, edit rsyslog-kmsg.conf, find the line near the end of the file that looks like:
dd bs=1 if=/proc/kmsg of=/var/run/rsyslog/kmsg

and replace it with:
exec dd bs=1 if=`grep -v "CPU[0-7]: Temperature" /proc/kmsg` of=/var/run/rsyslog/kmsg

So, all this does is filter out *all* warnings referring to CPU temperature fluctuations (for boxes up to 8 CPUs).  Don't look at me if you don't see the warnings and end up flaming out your CPU. :-)

Hope this helps someone until such time that a proper fix is available.

-Mark

---

### Post by mbobak on 2009-11-17
> **rootytooty said:**
> Are you talking about me with my Eee PC or answering someone else??? I am currently using Xandros with the easy desktop.

Are you saying that 9.10 is  no good???

Thanks,
Bobby

No, actually, I was replying to laffinet.  But, my point is, there is a well-known bug, that can be fairly debilitating.  I'm saying that it's probably a good idea to wait on installing 9.10, till this bug is resolved.  Saying "9.10 is no good" is just a *bit* of an overstatement and oversimplification.

Other than this bug, for which I've now got a temporary workaround in place, 9.10 seems to be a fine distribution.  It's unfortunate that this bug came up in the 9.10 release, but it will get resolved soon, and all will be well.  Till then, don't run 9.10, or implement my workaround.

Hope that helps,

-Mark

---

### Post by rootytooty on 2009-11-17
Thanks Mark.  I don't know my way around Linux that well so maybe my best bet would be to either use 8.10 or just use my Easy Desktop until the fix comes out.  I paid $10 for my CDs.  That is not a big problem as I wouldn't think they would send me out an updated version---or would they???  Or do they notify us when the fix is in and then I just order a new set of CDs???

Thanks,
Bobby

---

### Post by frego on 2009-11-17
I had been running 9.04 Mythbuntu (64bit), about a week ago, I performed a fresh install of 9.10 Mythbuntu 64 bit.  The one major positive I have found is how the mythvideo metatag info is automagically filled in, if your videos have standard file names.  When I first saw a custom background image per each show as I browsed through my video list I was very impressed!  And talk about wife acceptance factor!  The metatag info automatically pulled in show description, episode name, actors, director, etc.  A very nice feature for those of us who rely on mythvideo.  Now I'm trying to go through and get shows named properly so the jamu.py script will fill in more info.  But with thetvdb.com website being down for 5 days, I fear it was too good to be true.  

The only major thing I've run into thus far which would be described as negative, is in mythmusic when we edit a playlist the frontend crashes.  I haven't had a chance to dig into log files and find out whats going on yet.  I do enjoy being on the cutting edge, but there is always a trade off with stability to be on that bleeding edge.

---

### Post by hackmeister on 2009-11-17
Besides hitting that nasty installer bug I've been happily running Mythbuntu for a couple weeks now. To me the biggest pluses are support for the PVR-1212 and VDPAU out of the box. I talk about my experiences and thoughts here:
[http://pdavila.homelinux.org:8080/blog/?p=361](http://pdavila.homelinux.org:8080/blog/?p=361)
[http://tlltsarchive.org/archives/MythTVCast_Episode12.ogg](http://tlltsarchive.org/archives/MythTVCast_Episode12.ogg)

I need to play around with the storage groups and a couple other items as well.

---

### Post by Dewey_Oxberger on 2009-11-17
I'm 9.10 from the day the RC came out.  No real downside for me except my wife and kids are having trouble with the new default theme (scrolling menus is looking like a bad idea, also, item priority in the menus is whacky).

There has been a massive improvement in the DVD playback with regards to not crashing during dvd menu navigation.  Loads of Disney dvd's won't play in the internal player on earlier versions.  They all play now.

The VDPAU stuff works (if you keep your cpuspeed high enough) and I expect it'll get better and better.

---

### Post by SiHa on 2009-11-17
My experience with 9.10 has, on the whole, been extremely good.

I did have a few issues getting the RC to install, but the final release has been fine. VDPAU works out of the box, HDMI audio works out of the box (nearly). I've not seen any of the CPU scaling issues (which my Athlon II X2 should support), or the logging bug mentioned in this thread. The new default Mythbuntu theme looks very swish, and the way the fanart for recordings is downloaded automagically is extremely cool.

To be honest, though, the only reason I went to 9.10 was for VDPAU, as I just couldn't be arsed to figure out how to enable JYA's repositories for the 0.21 backports. Also I was running 8.04, and it's stated that there will not be 0.22 packages for 8.04.

If you are running 9.04 with the VDPAU backports successfully, then there probably isn't any compelling reason to upgrade. Maybe it's worth waiting for 0.23 when storage groups should be fully implemented, and there are more themes available which make full use of fanart and banners etc.

---

### Post by blackoper on 2009-11-17
wow did not know about the logging bug. I'll have to check it out when I get home

---

### Post by rootytooty on 2009-11-17
Thank you.  It sounds like you are pretty happy with it over all.  Sounds different then some earlier emails.
 
I just have to figure out why my Windows PC tells me no video as I am trying to install it or at least look at the demo.
 
Thanks,
Bobby

---

### Post by laffinet on 2009-11-17
Thanks everyone for the feedback (keep it coming).

Interesting points (and warnings!). I'm still looking for that "must have" new feature or improvement to push me towards upgrading.

The new UI sounds nice, and automatic artwork/fanart download is a great feature. Then again, I'm running mythtv and xbmc side by side, which means I already have that for my videos, just not in one application.

---

### Post by rootytooty on 2009-11-17
I am still getting used to Linux.  Like I said I have Xandros on my eee pc.  Its works fine but I am looking for something I can upgrade as needed like Openoffice and those kinds of things that get updated from time to time.
 
Thanks,
Bobby

---

### Post by blackoper on 2009-11-17
> **laffinet said:**
> Thanks everyone for the feedback (keep it coming).

Interesting points (and warnings!). I'm still looking for that "must have" new feature or improvement to push me towards upgrading.

The new UI sounds nice, and automatic artwork/fanart download is a great feature. Then again, I'm running mythtv and xbmc side by side, which means I already have that for my videos, just not in one application.

main reason for me was hdpvr support out of the box. The driver in mythbuntu 9.10 for the hdpvr works great and the thing is finally stable. New ui's are nice but like you I also use boxee and xbmc a lot. I only use myth for tv recordings

---

### Post by tgm4883 on 2009-11-18
> **hackmeister said:**
> 
Shutdown choice from the main menu. This is a such simple thing but makes a huge difference in user experience. Being able to cleanly shutdown your system via a tv remote is a must for any serious HTPC solution. Oddly it appears only on my frontend system. What gives? It should be on all MythTV systems.


This has been, and still is configurable from the frontend menu. It's set to automatically configure itself as most users don't want to shut down their backend.

> **hackmeister said:**
> 
# The installer. As previously discussed in my last post the Mythbuntu installer has some serious issues that need to be addressed. Nothing ruins a person’s first experience than a bad installation process.


Whats wrong with the installer besides you can't go through it with a remote?

> **hackmeister said:**
> 
# Mythbuntu has a great centralized configuration application called MCC (Myth Control Center). One of the cool things you could do with MCC was setup diskless frontends from your main MythTV system. The diskless management tools seem to have disappeared. What gives?

Yea the developer of the diskless part left the team as he was too busy with school. MCC was rewritten and he never got around to rewriting the plugin for MCC before he stepped down. This is something we are working on though. (And you can still configure it via the command line)

---

### Post by t3chn0b0y on 2009-11-18
After the update I found quit a few problems that are still to be fixed.
If you use the video instead of snaps in the corner for your recordings,
it has been removed, when it will be added back unknown... For me the snaps that do end up in the corner end up 1x1 pixel in size and in a variety of different shades of brown... TheTVDB.com used to get fanart,snaps etc for videos is constantly down, and when i do an update to my videos information etc, it wipes out what is already there for data when it can't make a connection.. meaning all my work is wiped out, and has to redone once the server is available for connection, meaning it has to do it over and over again for all of my videos, a waste of resources and a burden on their server, explains to me why there is such a load on it already.. Editing recordings by hand before encoding into another format, the frames stick at one point and flicker the other scenes making it hard to remove commericals, and bad for those that might experience cessors. All the themes are pretty much wide screen so if you have 3:4 monitor then you out of luck. There is good bit of bugs to still be worked out before the 0.23 release and I believe this release should of waited until then.. oh another thing, there was no time to get the mythmusic changed over to the mythgui. leaving it looking out of place.. The future looks great for mythtv. but there is much to be done to get there.

---

### Post by hackmeister on 2009-11-18
> **tgm4883 said:**
> This has been, and still is configurable from the frontend menu. It's set to automatically configure itself as most users don't want to shut down their backend.
I discussed all my issues in the podcast. Yeah my guess was that it's assumed that a backend system is on all the time. I'll try to swith this in the frontend menu. Thanks

> **tgm4883 said:**
> 
Whats wrong with the installer besides you can't go through it with a remote?
Again I discussed this in the podcast. I hit a nasty bug both in 64 and 32 bit installs. Installers hangs towards the end and no indication that it finished. Subsequent bootup gets the dreaded flashing terminal login. Others have reported this. Perhaps related to selecting the nvidia driver during the install? 

> **tgm4883 said:**
> 
Yea the developer of the diskless part left the team as he was too busy with school. MCC was rewritten and he never got around to rewriting the plugin for MCC before he stepped down. This is something we are working on though. (And you can still configure it via the command line)
Thanks for the clarifications. I appreciate everything the devs do. Overall I'm very happy with Mythbuntu 9.10. 

Any idea if the Nvidia 190 driver will make it into the repos anytime soon? How about updated Myth 0.22 packages now that it's officially out?

---

### Post by utar on 2009-11-18
Just thought I would post my 2 cents worth on 9.10.

I've had it installed for a couple of weeks now and with a couple of minor issues everything works great.  I was expecting to have more problems, particularly with my Nova T-500 card, since 0.22 is so new.

It took a bit of getting use to the changes from 0.21 but that is to be expected.

My only remaining issue is that my LCD won't work.  Lcdproc 0.5.3 seems to be broken for my display, however this is more of a ubuntu issue and nothing really to do with Myth.  I'm looking at installing an older version when I get chance as the display worked fine on 8.10.



Utar

---

### Post by tgm4883 on 2009-11-18
> **hackmeister said:**
> I discussed all my issues in the podcast. Yeah my guess was that it's assumed that a backend system is on all the time. I'll try to swith this in the frontend menu. Thanks


Again I discussed this in the podcast. I hit a nasty bug both in 64 and 32 bit installs. Installers hangs towards the end and no indication that it finished. Subsequent bootup gets the dreaded flashing terminal login. Others have reported this. Perhaps related to selecting the nvidia driver during the install? 


Thanks for the clarifications. I appreciate everything the devs do. Overall I'm very happy with Mythbuntu 9.10. 

Any idea if the Nvidia 190 driver will make it into the repos anytime soon? How about updated Myth 0.22 packages now that it's officially out?

I believe we are working on an SRU for MythTV 0.22. In any case, you can always use the [auto-builds]("http://www.mythbuntu.org/auto-builds") PPA which contains updated versions of MythTV (as well as the NVidia 190 driver).

---

### Post by laffinet on 2009-11-19
Some very interesting comments here, thanks everyone. Still undecided about upgrading.

In the meantime I installed 9.10 on a USB HDD I had lying around to see things for myself. Not as easy as I thought ! Tried to install via USB stick, but that didn't work (didn't even get to the selection menu). Had to burn a CD, install went fine with that.

Will play around a bit with 9.10, especially trying to upgrade and importing my existing database.

---

### Post by rootytooty on 2009-11-19
Having Xandros on my eee pc does anyone think Ubuntu is a better system than Xandros???   And, easyer to updgrade????
 
Thanks,
Bobby

---

### Post by NautiusMaximus on 2009-11-21
I've just read this thread with great interest, as I'm currently considering upgrading from 8.10 to 9.10 (well, probably a clean install rather than an upgrade, based on advice I got in an earlier thread).

But I'm a bit confused about this logging bug. Some people seem to say it's a real pain, and others say they've been using 9.10 without any problems. Is that because the bug only materialises under some circumstances? If so, does anyone have any idea what they are?

And any news on when it's likely to be fixed?

Many thanks for any answers to those questions and anything else that might help me to decide whether to upgrade. BTW, one of my reasons for upgrading is that I've never managed to get the remote to work (Silverstone GD02 case, iMon remote), and I was hoping that lirc might work better in the new version. Any idea whether it does?

Thanks
NM

---

### Post by williammanda on 2009-11-21
There also are the problems with Jamu.
1. After a video is setup with metadata and then Jamu runs, the video is no longer accessible. Here is the details of the problems and the temporary fix.

[http://ubuntuforums.org/showthread.php?t=1318635]("http://ubuntuforums.org/showthread.php?t=1318635")

2. Jamu deletes coverart for existing videos. Here is the details for this problem without any temporary fix.

[http://ubuntuforums.org/showthread.php?t=1327370]("http://ubuntuforums.org/showthread.php?t=1327370")

---

### Post by jensk on 2009-11-21
I have tried to upgrade my backend from 9.04 to 9.10

My hvr-4000 card didn't run at first. I had to apply v4l-dvb-fixes to get the hvr-4000 to find channels. 

There is another problem with finding channels that i have tried to solve.

The problem is that if there is a MPEG4 HD channel in a mux the other channels can't be found when i'm de a channels scan. So i'm missing three other channels in the mux. Until further i'm back to 9.04.

I have though about entering the the channels manually but i haven't found any methods for entering DVB-T channels manually.

Any good information will be appreciated.

My frontend is running 8.10 with a homemade lirc reciever. Does anybody know if it will work in 9.10.

/jens

---

