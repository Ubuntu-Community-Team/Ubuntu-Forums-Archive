---
title: "Bad video quality in Linux - horizontal lines"
date: 2008-04-26
forum: Multimedia Software
---

### Post by Artistar on 2008-04-26
Hi, i have a big problem with bad video quality on Linux. First of all, i'm Debian Lenny user, but also use Ubuntu on other machines, and from time to time on my own computer.

Well, i have it for six months now already and was never able to solve it, but i really tried everything i found.... :(

The problem is with videos falling appart - some [**_horizontal lines_**]("http://www.imagesforme.com/show.php/20672_03.png.html") are appearing, especially on faster scenes, so basically videos are unwatchable. That's unacceptable behaviour because i use Linux for both multimedia and work. On Windows, of course, i don't have this problem.

The cause of it is not in fglrx drivers (tried on last five versions), becuase it appears on vesa, mesa, etc. too. The -xv is also not a problem, because it appears on diffenerent extensions too.

So, what i have here is that the problem appears on different installations (Ubuntu 7.04, 7,10, 8.04 - didn't use it before 7.04....), and every single installation of Debian Lenny, using different drivers, different extensions, different video players (totem-xine, totem-gstreamer, xine, vlc, mplayer, etc.) and different codecs.

Maybe the cause of it is in my hardware: C2D E6750, Gigabyte P35C-DS3R, 2x1GB Kingmax DDRII. ATI HD2600XT DDRIII, Samsung SyncMaster 226BW....

I really dont know what else to do or try....

Thanks in advance for any kind of help.

---

### Post by pro003 on 2008-04-26
man I've been having this problem since I bought ati2600pro it seems like ati is not a solution if you want good 3d acceleration or good quality video.. seem like there are some better performances in 8.04 but still my video in full screen in ubuntu just does not work, small windo (totem movie player) works fine though... but hey who wants to watch video that way..

so I would too appreciate any help...

---

### Post by mc4man on 2008-04-26
The video your are watching appears to be interlaced, find the setting to enable deinterlace and enable it. In vlc it's under video tab, try blend or bob, totem has only 1 choice, smplayer has the better quality ones.
In windows players like powerdvd have auto deinterlace - if it's needed than deinterlacing is used, if not than it isn't

---

### Post by pro003 on 2008-04-26
i've tried that too, long time ago... deinterlace i mean...

i will now install vlc and smplayer and see what's the difference...

thanks though

---

### Post by fxandrei on 2008-04-26
I have the same problem . Poor video quality. I installed vlc and it stil kinda sucks.
I tryed to set the output module in vlc to opengl but when i try to open something it exits vlc. Ps: i have ati 2400 pro

---

### Post by xalaros on 2008-04-26
Are you using compiz???
maybe if you install compiz fusion icon and turn off compiz during video playback could work. Also try Smplayer thats what i use most of the time i find VLCs lack of fullscreen video controls annoying.
Also i you don't want to turn compiz on/off all the time what i did was tell compiz through the compizconfig menu that my refresh rate is 60 and my
output is 1680x1050. That seemed to stop the problems off course there is also vsync and sync to black in my nvidia setting that i used, i don't know if there is something similar for ATI. Anyway i think that most of the problem is that gnome thinks that the refresh rate of the screen is 50hz but in truth it is 60hz i don't know why this hasn't been fixed in hardy final i was hoping it was, but on the other hand it might have something to do with the nvidia drivers, so maybe it will be fixed on the next drivers.

---

### Post by pro003 on 2008-04-26
could someone tell how to set refresh rate in compiz config? 

'cause actually everything works well in the beginning but after driver (restricted or not) installation compiz and emerald, video in full screen is no longer an option..

---

### Post by eye208 on 2008-04-26
Video will look best if the media player uses XVideo. XVideo is an interface to control the hardware video overlay provided by modern graphics cards.

If you use an ATI card with ATI's own proprietary Linux driver, XVideo is disabled by default. This is because the driver only supports either OpenGL overlay or XVideo overlay, but not both at once. For some reason ATI chose to ship the driver with XVideo disabled.

You can enable XVideo by running the following command:
```
sudo aticonfig --ovt Xv
```
This will modify the X.org config file. Restart X (or the computer) to apply the changes.

Note that XVideo may not work properly with Compiz desktop effects. If you experience problems (e.g. media players crashing immediately) then turn off desktop effects.

---

### Post by xalaros on 2008-04-26
compizconfig settings manager is the way to change the refresh rate in compiz. If you haven't installed it, install it because it is not done so by default.
The go to system - preferences - advanced desktop effects settings.
Once the compizconfig window comes up, just hit general settings and on the
display settings tab, untick detect refresh rate and change the slider to the refresh rate you want also you may want to tick the vsync to black also.
That fixed a lot of my problems with tearing in videos.

---

### Post by pro003 on 2008-04-26
still doesn't work... Never mind - am buying NVIDIA anyway SOON.

---

### Post by krul on 2008-04-26
I have an NVIDIA (8600), but have also bad quality tv output. Just playing with different settings, but no luck.
Only with Xinerama (instead of twin view) the output is very good, but then Desktop effects won't work anymore and my 2d is not that responsive anymore :(

---

### Post by Artistar on 2008-04-27
@mc4man - i tried everything you said with vlc and it's a lot better. It seems that vlc handles deinterlacing a lot better than totem, but still after turning on deinterlacing (x, mean, blend, bob,....) and trying every extension, i still get one horizontal line traveling from the bottom of the screen to the top (i'll take a screenshot when i come home). i'll also try mplayer later.

@fxandrei - i also have a problem with vlc exiting after setting up opengl....

@xalaros- i'm not using compiz but i heard about those problems with video playback.

@eye208 - "sudo aticonfig --ovt Xv" is sth i always do after installing fglrx, so it doesn't seems to ber the cause....

Btw, thank you all for replying. :)

---

### Post by fxandrei on 2008-04-27
Is there nothing we can do to fix the video quality ?! I mean this is a major factor in making people not staying around ubuntu and linux in general. Most of the people want to have a good IM app, a good music player and a good movie player . And since a lot of people watch movies this is a really big letdown. Not to mention that the monitors are getting bigger and bigger and a lot of movies come out in HD quality, and having this interlaced thing with ur video makes me stick with **** like windows :).

---

### Post by Zibex on 2008-04-27
the simplest solution is just to turn off compiz :)

---

### Post by pro003 on 2008-04-27
here you go..

after fresh install of ubuntu 8.04

- create internet connection
- update your sistem i.e sudo apt-get update....
- enable repositories, choose best server if slow...
- open restricted manager 
- enable ati restricted driver
- install kplayer, mplayer & mencoder
- play video in full screen with kplayer 

p.s. kplayer has various video options so investigate little bit and you'll find a best fit...

that's my best... at least till I buy nvidia :guitar:

---

### Post by fxandrei on 2008-04-28
> **Zibex said:**
> the simplest solution is just to turn off compiz :)

Are u trying to say that the bad video quality has something to do with compiz? So if i turn off the effect it will fix the quality issue ?

pro003 i did the following :


> after fresh install of ubuntu 8.04

- create internet connection
- update your sistem i.e sudo apt-get update....
- enable repositories, choose best server if slow...
- open restricted manager
- enable ati restricted driver

i will do the last 2 :

- install kplayer, mplayer & mencoder
- play video in full screen with kplayer 

and return with the result ;)

---

### Post by pro003 on 2008-04-28
no, my video runs with compiz and it's quite good but let's say not 100/100... anyway it's kinda better...

---

### Post by fxandrei on 2008-04-28
I have a problem :). I cant seem to be able to install kplayer . It has dependencies that ubuntu states "are not installable". Does the video quality problem hangs in kplayer ? By the way, kplayer is for kde.

---

### Post by fxandrei on 2008-04-28
Im trying now to install kmplayer and mplayer ..

---

### Post by pro003 on 2008-04-28
> **fxandrei said:**
> I have a problem :). I cant seem to be able to install kplayer . It has dependencies that ubuntu states "are not installable". Does the video quality problem hangs in kplayer ? By the way, kplayer is for kde.

Which exactly? I can provide you with those,perhaps...

btw, doesn't really matter if it is for kde.. it works just fine with gnome too.

---

### Post by Zibex on 2008-05-02
> **fxandrei said:**
> Are u trying to say that the bad video quality has something to do with compiz? So if i turn off the effect it will fix the quality issue ?

pro003 i did the following :




i will do the last 2 :

- install kplayer, mplayer & mencoder
- play video in full screen with kplayer 

and return with the result ;)

correct me if im wrong. you get video tearing while watching videos? if so - compiz is at fault. btw... try smplayer not kmplayer

---

### Post by fxandrei on 2008-05-04
Yes, i also get video tearing sometimes.

---

### Post by eeg on 2008-09-25
Hi,

just wanted to confirm this bug and add some derived info. To those who may not
know, there is an official bug entry at launchpad (I've already submitted this
same info there) :

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/151674](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/151674)


IMHO, I think this is a problem affecting only Ubuntu (and/or maybe other Debian
-based distros). I make this (somewhat) bold statement due to one simple reason:
[B]I ran Fedora Core-8 for 6 months prior to installing Ubuntu... and never, ever
had this tearing problem[/B] (or the hue/blueing/greening problem). And to be clear,
I played tons of videos of all types, and at fullscreen, when using Fedora.

My guess is that it has something to do with the drivers provided. The only
difference between Ubuntu and Fedora is in the nVidia driver packages. I recall
that Fedora uses a special repository called Livna to install proprietary
drivers. My understanding is that the Livna guys "cook up" the driver a little
bit before releasing it as an RPM. So that may be the big clue here.


I have tried all the suggested workarounds (disable compiz, output to OpenGL,
use VLC, etc...) and nothing seems to work. This effectively means I am not
able to watch any form of video on my PC (unless I use another distro or go back
to Windows).

The only things I have yet to try is :
-  install a simpler WM (e.g., IceWM) and see if that helps any
-  install Fedora in a VirtualBox VM and run videos from it

Can someone more knowledgable please advise me on these two methods (especially
the IceWm tactic... do you think it will have any effect?) Needless to say, both
those remaining options are really bad.


Thanks.

---

### Post by DrMega on 2008-09-25
> **eeg said:**
> Hi,

just wanted to confirm this bug and add some derived info. To those who may not
know, there is an official bug entry at launchpad (I've already submitted this
same info there) :

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/151674](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/151674)


Thanks for posting this up, it is an issue that I've just gave up on. There are two flaws in the bug report though. Firstly, I have had this problem since Dapper (pre Compiz) and secondly, I have this problem on both machines, one has a nVidia card and the other is ATI.

I'm sure it will get resolved sooner or later.

---

### Post by pro003 on 2008-09-25
> **DrMega said:**
> Thanks for posting this up, it is an issue that I've just gave up on. There are two flaws in the bug report though. Firstly, I have had this problem since Dapper (pre Compiz) and secondly, I have this problem on both machines, one has a nVidia card and the other is ATI.

I'm sure it will get resolved sooner or later.

I agree. I have tried dozens of combination and only few times managed to work right but mostly unsuccessful. Video tearing is one of major problems with ubuntu and developers should give a lot more time to this issue.

Until then, I'm watching movies like dvd-rips through tv-out, but on ms-windows which my wife prefers.

---

### Post by eeg on 2008-09-27
Hi,


So... been grappling with this problem the last couple of days and I may have
found the problem. It seems to be something to do with my dual-monitor setup.
Simply, [B]if I remove my 2nd monitor from the X-server (via the nVidia drivers),
the tearing goes away[/B]. The moment I re-enable it, the tearing comes back. This
is independent of whether I had compiz-effects on or off (i.e., when I disable
compiz but still have two monitors active, videos still screen-tears).

For the time being, I'm just manually changing the settings to switch between
video-mode and dual-screen-mode. (i.e., enable/disable in xorg.conf, logging
out to restart X and logging in again). Its not ideal... you can pretty much
forget about putting desktop-shortcuts and gnome-panels on that 2nd monitor
(cos everything gets dumped on your remaining active screen).

One alternative is to enable "Separate X-Screens" so you get to use both
monitors and still get rid of the tearing. However, in my experience, this is
not useful as (1) you can't drag windows between the two monitors and (2)
enabling compiz-effects makes your menu-interactions really, really slow
(another bug where all your pop-up menus are really slow to appear... though I
know there is a workaround to solve this).


[B]My earlier suggestion about it being something to do with Fedora's special
livna drivers is wrong[/B]. I remembered that I gave up trying to enable Twinview in
Fedora-8 and just used separate x-screens. This is why my Fedora video-playing
experience was not affected by the tearing/hueing/blueing/greening.


Hope this is of some help to others facing this same problem. Don't try to
jiggle with totem/VLC's settings. Don't install latest nVidia/ATI drivers.
Don't try installing IceWM and XCFE. Don't tweak refresh-rates and "sync-to-
vblank" options. Just disable that extra monitor in X11 and see if that helps.
If it doesn't... my thoughts and prayers go out to you and your family.




@ DrMega & pro003


Eyup, your experiences plus my own seems to point the finger away from drivers.
IMO, it seems highly likely that its an X11 thing now. Do you guys have dual-
monitor setups as well?


Anyways, here's hoping it gets fixed. Tho, it doesn't look like it will be
solved anytime soon. The launchpad-bug status is still at "undecided", so I'm
guessing its not a top priority for them.

I can understand this situation... not many people have dual-monitor setups.
Then again, I know quite a few who hook-up their old monitors as a secondary
displays (yours truly being one such example). Plus, don't people
connect their laptops to larger screens at home and work?

Maybe, it should be seriously considered (*at least something higher than "undecided"!*).



---
eeg!

---

### Post by mattlach on 2008-09-29
It seems to be some sort of bandwidth issue,maybe when it comes to DVI bandwidth (Dot clock) to large monitors..

I only have the tearing issue when I fullscreen, it is OK in smaller windows.   This suggests it is a bandwidth problem.

When I set the correct refresh rate, and V-syn it in compiz-config it gets much MUCH better, but instead of tearing, it appears to drop frames every once in a while. This further confirms that it appears to be a bandwidth issue..

Maybe for some reason when enabling OpenGL as the primary interface, it somehow limits bandwidth over DVI?

---

### Post by Svendheim on 2008-10-01
This was actually a very simple matter in my case. The tearing goes away when I turn off Compiz.

That been said, I am very disappointed that the problem is not solved in the new beta of Ubuntu :(

---

### Post by eeg on 2008-10-07
> @ mattlach
It seems to be some sort of bandwidth issue ...

I know nuts about DVI bandwidth requirements :) However, I do know that size of
the window does not matter (at least in my case). The screen-tearing happens
regardless of the window-size I set when playing videos. Maybe its just less
noticeable when the video is small? When they are blown up to full-screen, I
guess the tearing problem is amplified.


> @ Svendheim
This was actually a very simple matter in my case. The tearing goes away when I turn off Compiz

Sadly, this is not the remedy for me. Compiz is not the cause of the
problem in my case.

- turned off compiz via [Visual Effects] in [Appearance Preferences]
- reboot PC (or restart X)
- videos/graphics ***still*** show screen-tearing

The only way I could get rid of the tearing was to disable my 2nd monitor in
[xorg.conf] (see my previous posts). Everyone seems to point the finger at
Compiz... I think its something to do with X. Then again, nobody else has
confirmed or replicated my 2-monitor problem scenario.


Also, this screen-tearing is not limited to just videos. It happens in graphics
applications as well. I do a lot of OpenGL programming for my assignments, and
anything drawn in the GL-context window screen-tears as well. Even when I'm
rendering some simple triangles and with [Sync to vblank] turned on.


- eeg

---

### Post by Phases on 2008-10-29
I have been struggling with this problem two different computers. One ATI and one nvidia. 

With or without compiz.

Both dual monitor setups. ATI uses bigdesktop with both monitors on a Y cable to one card.

My nvidia system is on two cards, one for each monitor.

All DVI.

I've tried everything I can find anywhere and can't fix it. All I can figure out is that it has nothing to do with compiz, compiz can't fix it in the settings, and driver versions/types are irrelevant. I get the same problem in every scenario. 

I have not tested eeg's suggestion, I will when I get home - but I suspect he's either right, or closer than anyone else. 

See my post history if you're curious about other stuff I've said or symptoms I've mentioned elsewhere, in case I'm missing stuff here. But the bottom line is, in my case: 

-nvidia and ATI, tried several versions of drivers for each
-compiz on, compiz off, whatever.. problem still there
-both dual monitor setups. Have not tried single. I realize I should for troubleshooting purposes.
-added tons of load modules, and options, in xorg.conf. 
-Tried DVI-D Dual cables just in case, nope.
 
Basically, find any thread around here talking about this problem and if something said seemed like it could help, I've tried it. 

Any thoughts appreciated. Thanks.

---

### Post by eeg on 2008-11-04
Hi Phases,


We're both on the same boat. I went crazy for a week trying to solve this issue.
Tried everything suggested, to no avail.

Anyways, in the latest info at the related bug-entry in LaunchPad :
*[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/151674](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/151674)*
another guy mentioned about having 2 different monitors with 2 different
refresh rates, which is the same setup I've got. I've got a sneaky feeling that
this is the true cause.

To those who are dealing with this problem, and may not know about refresh
rates/syncing : Tearing happens when your card updates the image faster than
what your monitor can show. Thats why the screen "tears". The "Sync to vblank"
option that people have been saying sort of locks the card output to match your
monitor. This gets rid of the tearing.

So, maybe the driver *is* doing the syncing, just not at the right monitor! :D
It makes sense, the drivers are "syncing to VBlank" but [B][I]only at the refresh
rate of your (primary?) monitor[/I][/B]. So, the stuff on the other monitor still tears.
This would be consistent with Xinerama, since I think the nVidia drivers treat
the video outputs as one single screen, not two different monitors with 2
refresh rates.

I've tried this. Played videos on my smaller, older monitor and there seems no
tearing. Still a bummer... I want to see vids on my larger, nicer monitor! :P
So Phases, maybe this could be a big clue in your troubleshooting? Hope this
helps.

-=-
eeg

---

### Post by luminos77 on 2011-01-30
> **xalaros said:**
> compizconfig settings manager is the way to change the refresh rate in compiz. If you haven't installed it, install it because it is not done so by default.
The go to system - preferences - advanced desktop effects settings.
Once the compizconfig window comes up, just hit general settings and on the
display settings tab, untick detect refresh rate and change the slider to the refresh rate you want also you may want to tick the vsync to black also.
That fixed a lot of my problems with tearing in videos.

> **pro003 said:**
> still doesn't work... Never mind - am buying NVIDIA anyway SOON.

I followed xalaros's refresh rate post above and the horizontal lines disappear completely.  Make sure you uncheck the "detect refresh rate".  I did not at first and the lines remained, so make sure you do that.  Also make sure to manually set the refresh rate to the actual refresh rate of your monitor/TV, which can be googled.  I also enabled vsync in my graphics card settings manager.

If you have other issues with nvidia be sure to not use the proprietary drivers: use the real driver.  Follow this thread to install the real nvidia driver: _**[COLOR="Blue"][http://ubuntuforums.org/showthread.php?t=1467074]("http://ubuntuforums.org/showthread.php?t=1467074")[/COLOR]**_

---

