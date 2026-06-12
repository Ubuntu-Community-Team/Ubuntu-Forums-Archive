---
title: "Very slow Program Guide while watching Live TV"
date: 2008-12-07
forum: Mythbuntu
---

### Post by Da_Teach on 2008-12-07
I've recently setup a new media pc, pretty good specs, C2D 8400 with 4Gb memory and a P5N7A-VM motherboard which has a Geforce 9300. Its running Mythbuntu 8.10 with all the latest updates and nvidia 177.80 (also tried 173) drivers.

But there's something that I cant figure out. The program guide is unbelievably slow if you open it while watching live tv. Another media pc that doesnt have such high spec's is running it all much smoother (it has a Geforce 6150LE).

Now I've done a google and there was a known problem a while ago but those fixes should be in the MythTV that came with 8.10. So I'm at a loss whats actually causing MythTV to be this slow.

Anyone else having this issue (or had this issue)?

---

### Post by bjorndell on 2008-12-08
Hi!

I have a decent machine and also noticed the lag, the epg took forever to browse.

Made some tests and the only thing that worked was to change from opengl render to qt, for the mythfrontend render.

I worked for me, no the little livetv window i the epg becomes choppy instead when browsin, but thats something i can live with.

.

---

### Post by nrune on 2008-12-08
Have you turned on mysql caching. That's what I use to try and speed things up. Not a perfect option by far but does help a lot once the data is cached. 

YMMV

Mike

---

### Post by Da_Teach on 2008-12-09
MySql caching wont work as another frontend that is using the same backend has no issues at all.

Anyways, after some testing I found that its the same issue that is supposedly fixed. The related bug is this one:

[http://svn.mythtv.org/trac/ticket/3986](http://svn.mythtv.org/trac/ticket/3986)

However I'm not using the Bob deinterlacer but the Yadif (2x), that said the problem still happens with the Bob 2x deinterlacer as well.

Has this fix been 'unfixed' in 8.10 ?

---

### Post by Da_Teach on 2009-01-02
*bump*

The problem still persists and at this moment it seems its the only issue I have with my MythTV setup.

---

### Post by uncle hammy on 2009-01-02
This has been a nagging issue with a lot of people for a long time now.  The original thought seemed to have been that it had something to do with Bob deinterlacing causing the slow down, and a fix was supposedly introduced to fix it.

I still experience the problem, using the most current version from the weekly builds, so I have a feeling that the "Bob deinterlacing fix" didn't actually fix anything.  Mine is a little stranger though, because the slowdown is entirely depenendant on what channel I am watching when I open the guide.  I have 3 channels that if I am watching them, I know 100% for sure I cannot open the guide, or I'll be stuck for a while.  On any other channel, I have no guide issues.

I have tried every deinterlacer, renderer, etc that I have seen suggested, and nothing has ever fixed it.  I have kind of given up on it, and just don't use the guide when on certain channels.  When I'm on those channels, I just use the up/down keys to scroll through the channels to see what's on.  Annoying as all get out, but like I said, I've given up on that issue.

For what it's worth to anyone who may be able to fix it, all my channels that cause my guide to be slow are broadcast in 720p.  All my other stations, which cause no problems with the guide, are broadcast in an interlaced format (1080i or lower).

---

### Post by fenian on 2009-01-02
Have you tried changin the Video playback profile?
In the frontend go to Utilities/Setup>Setup>TV Settings>Playback
On the third page try setting the Current Video Playback to  Slim.

---

### Post by uncle hammy on 2009-01-02
If I change my profile to any profile that uses XvMC then I have no issues with my guide.  To me, there are 2 issues with this "solution"...

1.  XvMC has it's own drawbacks like greyscale OSD, when the OSD is open/scrolling the guide/jumping forward or back the audio stutters something fierce, etc

2. My machines are easily capable of doing their thing without XvMC,  this is the only issue I have. Due to the issues above, I'd rather not turn it on, just to "fix" the guide being intolerably slow while it's open when I'm tuned to 3 different channels.

---

### Post by uncle hammy on 2009-01-02
If I change my profile to any profile that uses XvMC then I have no issues with my guide.  To me, there are 2 issues with this "solution"...

1.  XvMC has it's own drawbacks like greyscale OSD, when the OSD is open/scrolling the guide/jumping forward or back the audio stutters something fierce, etc

2. My machines are easily capable of doing their thing without XvMC,  this is the only issue I have. Due to the issues above, I'd rather not turn it on, just to "fix" the guide being intolerably slow while it's open when I'm tuned to 3 different channels.

---

### Post by crez79 on 2009-01-02
This plagues me too, but not all the time. I find that the High Quality settings work the most. I still have problems sometimes, and I don't know what exactly is causing it. The only sure fire way to make the guide work for me is to pause the live tv before entering the guide. I am too new to try too much troubleshooting, and am apprehensive trying too much because I always end up breaking something else.

---

### Post by uncle hammy on 2009-01-03
> **fenian said:**
> Have you tried changin the Video playback profile?
In the frontend go to Utilities/Setup>Setup>TV Settings>Playback
On the third page try setting the Current Video Playback to  Slim.
fenian, my apologies, I just took a little closer look at the slim profile, and realized it didn't use XvMC at all.

Anyways, I gave it a try, and it has no effect on my guide issue.  However, that does help rule out Bob as the culprit of the problem.

---

### Post by Da_Teach on 2009-01-10
> **uncle hammy said:**
> However, that does help rule out Bob as the culprit of the problem.

I was running a video playback profile which was using the Yadif deinterlacer.

Somehow I feel this might be a (display?) driver issue, the whole mythtv installation feels more sluggish. 

The PC in question is a C2D 8400 with Geforce 9300 and my other MythTV installation is an X2 6000+ with a Geforce 6150LE. 

The C2D setup should outperform the AMD by far, but mythtv's menu's seem to build up slower on the C2D setup. And the EPG is unusable. Also the pre-scaling startup of mythtv seems to take longer on the C2D setup, as I can actually read what its doing on that PC, but on the AMD it finishes so fast I can hardly read what its doing.

As I have no way of actually measuring performance, is nothing more then a feeling.

---

### Post by uncle hammy on 2009-01-11
I have been using the CPU++ profile for some time now, which uses Bob.  Aside from the EPG issue while on a couple channels, I am quite happy with the performance.  My machines are all AMDs... 3800+ / NVidia 7600GS (FE only), 4600+ x2 / NVidia 7600GS (BE/FE), 5000+ x2 / ATI 1300X.

Now, interestingly, I rarely use the last machine for MythTV.  It's our main family computer and dual boots windows Vista.  I installed Mythbuntu on it mostly for when I work out or am in a bind for a free tv.  The ATI driver is useless, so it uses the standard driver.  I have never actually checked the guide performance on this machine.  When I get a chance, I will...it could help determine if it's an NVidia driver issue.

---

### Post by hitthenorth on 2009-01-12
Does your program guide only go slow when launched from live tv, or when scheduling as well?

Mine is slow in both but seems to be driver related.  I have an M3N78-EM motherboard with on-board 8300 graphics and an AMD 4850e.

With the 177 driver the program guide is horrendously slow and xorg uses around 100% of one core.  With 173 I can zip around the guide (although still using a fair bit of CPU), but I lose the capability of having sound over HDMI.

---

### Post by netslacker on 2009-01-12
try this:

edit xorg.conf and under the device section add:

Option "UseEvents" "true"

save, restart.

---

### Post by hitthenorth on 2009-01-12
Thanks for that suggestion, but I had already tried that along with the other recommended nvidia settings such as PixmapCacheSize etc.

I'm going to have to do some more digging as something is definitely wrong because xorg can use 30% or more CPU just displaying the gnome system monitor graph.

There do seem to be plenty of others having issues with 177 and on-board 8200 and 8300 chipsets though, e.g.

[http://www.nvnews.net/vbulletin/showthread.php?t=125206](http://www.nvnews.net/vbulletin/showthread.php?t=125206)
[http://www.nvnews.net/vbulletin/showthread.php?t=125471](http://www.nvnews.net/vbulletin/showthread.php?t=125471)
[http://www.nvnews.net/vbulletin/showthread.php?t=125442](http://www.nvnews.net/vbulletin/showthread.php?t=125442)

and this monster thread

[http://www.nvnews.net/vbulletin/showthread.php?t=115916](http://www.nvnews.net/vbulletin/showthread.php?t=115916)

---

### Post by Da_Teach on 2009-01-15
> **netslacker said:**
> try this:

edit xorg.conf and under the device section add:

Option "UseEvents" "true"

save, restart.

That option seems to be enabled by default in 8.10. At least its in the xorg.conf on both my Mythbuntu machines and I sure as hell didnt add it :)

---

### Post by Da_Teach on 2009-01-17
I just installed NVidia drivers v180.22 on the system with the slow EPG and it seemed to have solved it for 90%, only starting up the EPG the first time can take up to 20 seconds (after a cold reboot) but after that its instant.

Thus confirming it was/is a nvidia driver issue for me.

Edit: It seemed this was only the case with a reasonably empty EPG, now that the EPG actually has data its slowish again (though the 180.22 drive did improve performance considerably!) (EPG didnt have a lot of data as the IETScanner crashed in the backend)

---

### Post by nrune on 2009-01-17
I did run into a story on slashdot about a longstanding i/o bug in the current linux kernel that occurs when you have to transfer data between two processes or threads.  Not sure if this is related.

[http://it.slashdot.org/article.pl?sid=09/01/15/049201](http://it.slashdot.org/article.pl?sid=09/01/15/049201)

Mike

---

### Post by uncle hammy on 2009-01-17
I just tested it out on my "rarely used" machine, which is just using the open source driver.  I have no issues with the program guide on the same channels that lock up on me with the nvidia drivers on my other machines.

---

### Post by GuiGuy on 2009-01-17
> **Da_Teach said:**
> 
Now I've done a google and there was a known problem a while ago but those fixes should be in the MythTV that came with 8.10. So I'm at a loss whats actually causing MythTV to be this slow.


I had a slow guide issue some time ago. The cause was definitely a mismatch on video resolution/ refresh settings. Once I worked out how to configure the video output correctly to my 1080p LCD at 50hz, all has been well. 

I raised & discussed the matter in [another forum here]("http://www.xpmediacentre.com.au/community/mythtv-general-discussion/31754-weird.html"). A respondent steered me in the right direction. 


Cheers

---

### Post by Da_Teach on 2009-01-23
> **GuiGuy said:**
> I had a slow guide issue some time ago. The cause was definitely a mismatch on video resolution/ refresh settings. Once I worked out how to configure the video output correctly to my 1080p LCD at 50hz, all has been well. 

I raised & discussed the matter in [another forum here]("http://www.xpmediacentre.com.au/community/mythtv-general-discussion/31754-weird.html"). A respondent steered me in the right direction. 


Cheers

Interesting, I just tried switching refresh rate on my media center thats connected to my panasonic plasma. And I didnt see a difference. 

However, disabling XVideo vsync in the nvidia config screen did solve the high (40-50%) cpu usage on some of the channels. The intresting part is that this did not solve the slow EPG on that same channel :(

---

### Post by GuiGuy on 2009-01-25
> **Da_Teach said:**
> 
However, disabling XVideo vsync in the nvidia config screen did solve the high (40-50%) cpu usage on some of the channels. The intresting part is that this did not solve the slow EPG on that same channel :(

Are you using envyng to install the video drivers?

I usually find that with the monitor (lcd screen etc) plugged in and re-installing the video drivers with envy fixes a multitude of sins. I know it's not the purists' way and it often doesn't explain what's gone wrong, but it does seem to fix things.

NB: removing the drivers first might be an idea?

Also, maybe try rescaling the front end in mythtv once you're confident screen resolutions are correct.

---

### Post by Da_Teach on 2009-01-28
> **GuiGuy said:**
> Are you using envyng to install the video drivers?

I manually installed 180.22, I'm pretty sure envyng doesnt support the latest nvidia driver. I'm not sure I want to go through 'that' again (it was a real pain in the buttocks).

Going back to an older driver version isnt an option as that was really really slow compared to what its now.

---

### Post by jdeslip on 2009-01-28
I have the exact same problem, and also have an M3N78 motherboard with onboard nvidia video.   I have tried the 'solutions' like changing to slim profile, changing QT style etc... but nothing has worked.  I'd love to know a solution.

---

### Post by jdeslip on 2009-01-28
I thought maybe that GuiGuy's solution would work for me as well.  But, this problems exists for me on both vga and hdmi for me and at various resolutions.

---

### Post by Da_Teach on 2009-01-30
> **jdeslip said:**
> I thought maybe that GuiGuy's solution would work for me as well.  But, this problems exists for me on both vga and hdmi for me and at various resolutions.

His solution didnt work for me, while it did lower the cpu usage of x11 it did not fix the slow EPG. Even though there seems to be a vsync issue, disabling vsync in the nvidia config setting should have the same effect as getting a 'perfect' sync.

If you didnt give it a try yet, see if it gets better by installing the 180.22 drivers. While it didnt solve the issue for me completely, it did make it better on several channels.

---

### Post by Da_Teach on 2009-01-31
While I'm still not convinced the refresh rate is the problem, I did try 1080p with 24Hz, 50Hz and 60Hz, none of which lowered the CPU usage of XOrg, only disabling xv-vsync made the high cpu usage go away.

I was doing a google on this issue and it seems I'm not the only one:
[http://www.nvnews.net/vbulletin/showthread.php?t=120324](http://www.nvnews.net/vbulletin/showthread.php?t=120324)

The 'funny' thing is that XOrg is only using a lot of CPU on some SD-channels, not on all. Which probably has something to do with that channels refresh-rate. (dont have any real HD channels to check)

Keeping vsync disabled is not an option, it creates a lot of tearing.

---

### Post by jdeslip on 2009-01-31
Yes, I noticed that the cpu usage goes down dramatically when I remove sync to vblank, and this seems to remove the problem with unresponsive programm guide.  But yes, I get some tearing, so I put it back on.  *Befudled

---

### Post by korgman on 2009-01-31
I've just upgraded nvidia driver to 180.22 and I am still having EPG problems.  I've tried every deinterlacer option, doesn't matter. Sometimes I cannot even exit the guide.  I'll have to send a barrage of ESC keystrokes until something hits and it takes me back out.

But, as always, if I pause live TV before entering the guide everything is AOK.  Did a mythbuntu update last week as well.

---

### Post by korgman on 2009-02-05
I think I fixed it on my system.  Its been perfect since I made these two changes:

Set the appearance renderer to OpenGL (instead of Qt)
Turned off Channel Icons.

---

### Post by korgman on 2009-02-06
Nope, not fixed.  But I'm seeing improvements since I've update to 180.22.  I'm getting that thing where once it finally gets into the guide it is fine for the rest of the time.  Still have to experiment if its once after every boot, or once every time I watch TV.

---

### Post by tradewinds on 2009-05-04
I am having this same issue. Has there been any sure way to resolve it. I am on 9.04. M3N78-EM, 4805e, SLIM profile, QT renderer.

---

### Post by Flecko on 2009-05-04
I think that this one is just going to go down as one of those legendary bugs in free software. I had the problem under 8.10, and upgraded my DVR to 9.04. The guide seems to be more responsive, but still not as good as it was on my older crappier DVR system.

Its reminiscent of the kernel IO wait bug that has been around for years. Someday, it will be found, but for now....nothing seems to be a silver bullet for everyone.

I'm doing a fresh reinstall of 9.04 right now to fix another issue I was having, but I'm keeping my fingers crossed that the guide issues won't come back in the meantime.

---

### Post by Brasil on 2009-05-05
Fairly sure the only wway to "fix" this at the moment is to pause before going into the guide. Yeah, not great.

---

### Post by tradewinds on 2009-05-05
I am planning to program my JP1 remote to do the pause and unpause when going in/out of Guide.

However, I think that the icons could be causing it. Seems I am able to navigate around the guide when I turned that selection off in Setup.

---

### Post by ml98133 on 2009-11-04
I doubt this is the problem most of you have had...but I was having an awful time with live tv, where it barely worked at all.

It turned out I had Live TV set to use the TS (transport stream) rather than PS (program stream).  After fixing that, everything worked much better.:D

---

### Post by bruk on 2009-11-06
I too had this a fair while ago (moving through channels criminally slow, moving back/forth on timeline was normal), reported it, heard nothing back that helped (turn on vdpau, different renderer, sql caching, etc.) and chalked it up to one of those random things that I'd just have to live with.

In the UK we had a channel reshuffle a while ago, and after I fixed my myth box up to reflect the change, the slowness in the epg had disappeared. I hadn't the faintest idea what had changed, but I was glad it was working and forgot about it.

I saw a post from someone having slowness in their epg, and the thread had been solved, so out of curiosity I had a look. Turns out using the epg with icon display turned on whilst having no icons causes massive slowdown problems. And I hadn't scanned for the icons since doing a clean 9.10 install, therefore slowdown. It's a pretty shoddy bug, but there ya go.

Rescan for all channel icons, and just generally jump through the setup hoops and make sure everything is there, and maybe, just maybe the epg will start working properly.

---

