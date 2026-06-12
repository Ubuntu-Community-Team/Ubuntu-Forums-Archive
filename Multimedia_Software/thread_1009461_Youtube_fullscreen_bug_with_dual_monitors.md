---
title: "Youtube fullscreen bug with dual monitors"
date: 2008-12-12
forum: Multimedia Software
---

### Post by drelyn86 on 2008-12-12
Kind of a weird bug... :confused:

I have dual monitors (both at 1280 x 1024, 2560 x 1024 total). When I view a youtube video in fullscreen, the video seems like it's changed to the aspect ratio to fit on a 2560 x 1024 screen, and then is shrunk down to just one screen, so it's a lot smaller than it should be (there are white bars above and below the video to fill the extra screen space). Is there any way I can get it to fill the whole screen (and just 1 monitor)?

I only have this problem on Youtube. Fullscreen videos are sized correctly on Hulu, Megavideo, Myspace, Ebaumsworld, por... well, you get the idea. 

any help would be appreciated.

relevant specs:

Ubuntu 8.10 32-bit
2 CRT monitors @ 1280 x 1024, big desktop mode
ATI HD3850 w/ FGLRX driver (the one included in Intrepid)

---

### Post by markbuntu on 2008-12-12
Hmmm, this does not happen to me on my big desktop. I am also using fglrx from the repos with a HD3650 card. I have 2 lcd monitors, one 24 inch and one 19 inch.

---

### Post by cmcginty on 2009-02-14
Interestingly, I have two PCs with dual screen setup. The Nvidia machine (GeForce 6200) has the bug you describe. The Intel GM4500 laptop does not have any problems when outputting dual screen from the docking station.

If anyone has an idea on how to fix the Nvidia drivers I would love to hear it.

---

### Post by drelyn86 on 2009-02-14
I'm also back to using Hardy, and still have the same problems... just with Youtube.

---

### Post by poobslag on 2009-02-26
Yes, youtube fullscreen works horribly for me too with my dual monitors. There appear to be at least 3 bugs upon activating fullscreen mode.

1. The frame rate drops to about 1/3 of normal.

2. The fullscreen video is about half as tall, and half as wide as it's supposed to be.

3. The fullscreen video always appears on my left monitor, instead of taking up whichever monitor I'm currently on.

None of these three issues occur in windows. I'm running Ubuntu 8.04, the 64-bit version, with the 32-bit flash plugin.

---

### Post by drelyn86 on 2009-02-28
UPDATE: I'm still having this problem, HOWEVER, I've found a decent workaround. 

If you have compiz (and the advanced settings manager), you can enable the desktop zoom effect, and use Super + left-click-drag to do a custom-sized zoom on the video.

---

### Post by GeorgeAScott on 2009-04-08
I have the same issue.  there's got to be a better way.  that zoom sidestep is quite annoying.

---

### Post by TheBuzzSaw on 2009-04-08
Yup. Same here. It is clearly an Nvidia/YouTube issue. I'm glad I'm not the only one.

Curse Nvidia for staying proprietary... :(

---

### Post by redseventyseven on 2009-04-09
Can confirm this, with NVidia FX 5200, using Twinview.

Youtube and MLB.tv don't fill the screen properly, and disply off-centre.

BBC Iplayer works perfectly.

I wonder what the difference is?

---

### Post by Pasdar on 2009-04-12
Same issue here, GeForce 6200, TwinView enabled. I don't have this problem on other video sites.

---

### Post by Neilguy on 2009-04-12
I have the same problem too with GeForce Go 6150. Any resolution to this problem?

---

### Post by TheBuzzSaw on 2009-04-13
> **Neilguy said:**
> I have the same problem too with GeForce Go 6150. Any resolution to this problem?
Buy an ATI card...? :P

---

### Post by Pasdar on 2009-04-14
Today it just worked all of a sudden. I haven't done anything to the system other than using update feature and installed/uninstalling some programs.

Try updating your OS and see what happens.

---

### Post by off1 on 2009-04-28
Same here, using ATI radeon 3450

Pasdar, Can you post your xorg.conf settings?


THANX!!!

---

### Post by EdgarPE on 2009-07-01
Same problem here on Ubuntu 9.04 with nVidia 8600GT and 21" + 15" LCD. NVidia restricted driver and compiz is installed.  I attached my xorg.conf.

---

### Post by scimitar123 on 2009-09-02
I'm having this same problem. Nvidia card and dual 17" monitors. Whats the fix for this? Its only youtube, not other flash based streaming sites!

---

### Post by Lucky75 on 2009-09-02
I'm having problems as well. Youtube has extra probs, but even other sites have problems. since my monitors are of a different size/resolution.

[http://ubuntuforums.org/showthread.php?t=1256206](http://ubuntuforums.org/showthread.php?t=1256206)

---

### Post by Bodsda on 2009-10-29
This does not appear to be a compiz issue nor a dual screen issue. I get the same small 'fullscreened' display when running one monitor without compiz

It is also not specific to Youtube, I have experienced this on more then one site -- next step is to try with vesa drivers

---

### Post by darude on 2010-01-17
Same problem with youtube and GeForce 6800 XT in all distros I've tried: Kubuntu, openSUSE, Mandriva...

---

### Post by EienTatsu on 2010-02-18
anyone developed a fix for this?

---

### Post by Lucky75 on 2010-02-28
Bump. I've had problems since at least 9.04 with this. Any ideas on it? It's not just youtube, and different flash players seem to have different problems with the display, although youtube is generally the worst of them all.

---

### Post by Lucky75 on 2010-03-03
bump

---

### Post by vek on 2010-05-01
I get this too.  I think its youtube's fault.  They're probably evaluating the full desktop size (3000x1024 or whatever) and then rendering to that, then shrinking it or something.  So you end up with a small image in the middle of one monitor.

Youtube doesn't appear to have any way to report a bug, so bleh

---

### Post by Rykes on 2010-05-21
Just giving this thread a bumpty bump since I'm having the very same problem. Nvidia Geforce 9800 GT

---

### Post by TheBuzzSaw on 2010-05-22
I bypass this bug by fetching the fully buffered Flash video file from /tmp/ and just watching it in Totem, which enters fullscreen just fine in dual monitor setups.

---

### Post by wizi on 2010-07-21
Bump!!! I am having the same problem with youtube videos. If anyone know how to fix this, please show us.

---

### Post by TheBuzzSaw on 2010-07-21
> **wizi said:**
> Bump!!! I am having the same problem with youtube videos. If anyone know how to fix this, please show us.

I've given up on YouTube itself, but I have a powerful alternative. I just wait for the video to buffer all the way. Then, I go into the folder /tmp and grab the video file from there. It'll have some title like "Flashx9dhfg9h3". Just copy, paste, and rename it. Play it in your media player, and full screen mode works fine there. Flash is an abomination.

---

### Post by livelite on 2010-10-25
I'm one of those having this issue as well, however, there is a neat workaround you might want to try.

It works by replacing the flash player on YouTube with an embedded Ubuntu movie player.

To do this you'll need FireFox, and the [Greasemonkey]("https://addons.mozilla.org/en-US/firefox/addon/748") extension with the [Youtube without Flash Auto]("http://userscripts.org/scripts/show/50771") script installed.


Once you do this, YouTube videos will play nicely in full screen, and might even handle those HD videos nicely if your pc had trouble viewing them with the flash player.

Enjoy ;)

---

### Post by guntu on 2010-10-26
I have the same issue, I'm running Ubuntu 10.04 on a HP Pavilion dv2000 with NVidia graphic card (can't remember the model) and using Twinview.

It pretty annoying but I thought it was because my second monitor is actually my TV.

---

### Post by livelite on 2010-10-26
I don't think it's an NVidia cards only issue, since I'm using a Dell Vostro 1500 laptop, which has the Intel GM965 integrated graphics controller, and the same problem happens when an external monitor is connected.

This has been happening in Ubuntu 10.10, 10.04, 9.10 and probably earlier.

Try the Greasemonkey script workaround until this is fixed, it works quite nicely.

---

### Post by ram130 on 2010-10-28
Same issue here on my HP dv7 with ATI graphics and  a dell monitor as my second...also having video tearing issues..will ubuntu ever get better??..these bugs have been around a long time!

The grease monkey script worked great! but still disappointed ..

---

### Post by sticky_icky on 2010-10-28
**I HAVE THE SOLUTION** for this problem, for everybody that has flash issues, _when all embedded flash goes fullscreen on every site except youtube or googevideos_.  **I HAVE THE SOLUTION** for this problem, for everybody that has flash issues, _when all embedded flash goes fullscreen on every site except youtube or googevideos_.  

      I wish to christ i could have found this years ago...  i have the same  problem, main monitor is 1440x900, running an xfx geforce 7600gt, and  everything but youtube works.  flash/youtube/ubuntu=HUGE #$^@##@  headaches for years.  i tried litterally hundreds of workarounds or  fixes, HOURS of time trying to get the stupid flash fixed for more than 2  minutes, and not one single thing worked, ever, until now.t

      ubuntu forums had been completely useless to me, in those endeavors,  wasted much time for nothing, though, in fairness to the buntu, i fully  acknowledge the fruitful efforts of the ubuntu team, the linux world has  made HUGE strides forward since i started with slackware7.   with  ubuntu, the reality is that aside from arbitrary reference, i haven't  needed the forums, everything but flash, some really obscure software,  works like a charm, since the nvidia driver issues have been  sorted.(btw, for me, the only way to install properly working nvidia  drivers/nvidia settings/flashplugin is with apt from terminal after  stopping gnome...**not with synaptic from the desktop**)

     since nothing's ever worked for me, i didn't bother reading the thread, i'd be shocked if it was mentioned... anyway, after a routine cleaning/reinstallation of firefox i happened across this:[ http://www.addonfox.com/]("http://www.addonfox.com/"),  which icludes some really good addons for firefox....also some bs, the  converter, swifclick, and windowshopper addons pissed me off...

the real gem of that collection, which i had never found before is:

**[flashvideoreplacer 1.0.5]("https://addons.mozilla.org/en-US/firefox/addon/161869/")**

      it "replaces embedded flash videos with quicktime or windows media  player compatible videos."   WHAT THAT MEANS IS IT COMPLETELY REPLACES  THE WHOLE, STUPID, YOUTUBE/GOOGLEVIDEO GUI AND **EMBEDS IN ITS PLACE MPLAYER**.
(in the preferences,the selection for plugin/mimeType, is "windows media player (application/x-mplayer2)

hall-o-fu#%ing-luja!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

     _**this is the only thing that has ever worked for me**_,  and it seems to be a really solid addon, so far as i can tell, not  buggy, video looks great-not choppy, options exist to automatically  choose the quality of youtube videos, choose cache size(default is  2megs), enable post processing, all the gnome mplayer interface  settings, etc.  _it doesn't seem to change anything on any video sites except youtube/googlevideos, and optionally vimeo and blip.tv etc._  only problem is i haven't been able to get the youtube playlist to autoplay the next vid.

if  you are frustrated wit yt/google, try this.  i can confir, it works  with gnome mplayer on 10.04.1 LTS.  i have every video and audio  application i could find, though, not sure of the impact other packages  have on mplayer/vice-versa.
[B]
hope this works for you, NO need to thank me if it does, but--

         PLEASE[/B] **PLEASE PLEASE help others when you have solutions.**

god bless.

---

### Post by ram130 on 2010-10-28
> **sticky_icky said:**
> **I HAVE THE SOLUTION** for this problem, for everybody that has flash issues, _when all embedded flash goes fullscreen on every site except youtube or googevideos_.  **I HAVE THE SOLUTION** for this problem, for everybody that has flash issues, _when all embedded flash goes fullscreen on every site except youtube or googevideos_.  

      I wish to christ i could have found this years ago...  i have the same  problem, main monitor is 1440x900, running an xfx geforce 7600gt, and  everything but youtube works.  flash/youtube/ubuntu=HUGE #$^@##@  headaches for years.  i tried litterally hundreds of workarounds or  fixes, HOURS of time trying to get the stupid flash fixed for more than 2  minutes, and not one single thing worked, ever, until now.t

      ubuntu forums had been completely useless to me, in those endeavors,  wasted much time for nothing, though, in fairness to the buntu, i fully  acknowledge the fruitful efforts of the ubuntu team, the linux world has  made HUGE strides forward since i started with slackware7.   with  ubuntu, the reality is that aside from arbitrary reference, i haven't  needed the forums, everything but flash, some really obscure software,  works like a charm, since the nvidia driver issues have been  sorted.(btw, for me, the only way to install properly working nvidia  drivers/nvidia settings/flashplugin is with apt from terminal after  stopping gnome...**not with synaptic from the desktop**)

     since nothing's ever worked for me, i didn't bother reading the thread, i'd be shocked if it was mentioned... anyway, after a routine cleaning/reinstallation of firefox i happened across this:[ http://www.addonfox.com/]("http://www.addonfox.com/"),  which icludes some really good addons for firefox....also some bs, the  converter, swifclick, and windowshopper addons pissed me off...

the real gem of that collection, which i had never found before is:

**[flashvideoreplacer 1.0.5]("https://addons.mozilla.org/en-US/firefox/addon/161869/")**

      it "replaces embedded flash videos with quicktime or windows media  player compatible videos."   WHAT THAT MEANS IS IT COMPLETELY REPLACES  THE WHOLE, STUPID, YOUTUBE/GOOGLEVIDEO GUI AND **EMBEDS IN ITS PLACE MPLAYER**.
(in the preferences,the selection for plugin/mimeType, is "windows media player (application/x-mplayer2)

hall-o-fu#%ing-luja!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

     _**this is the only thing that has ever worked for me**_,  and it seems to be a really solid addon, so far as i can tell, not  buggy, video looks great-not choppy, options exist to automatically  choose the quality of youtube videos, choose cache size(default is  2megs), enable post processing, all the gnome mplayer interface  settings, etc.  _it doesn't seem to change anything on any video sites except youtube/googlevideos, and optionally vimeo and blip.tv etc._  only problem is i haven't been able to get the youtube playlist to autoplay the next vid.

if  you are frustrated wit yt/google, try this.  i can confir, it works  with gnome mplayer on 10.04.1 LTS.  i have every video and audio  application i could find, though, not sure of the impact other packages  have on mplayer/vice-versa.
[B]
hope this works for you, NO need to thank me if it does, but--

         PLEASE[/B] **PLEASE PLEASE help others when you have solutions.**

god bless.

thanks but how is your solution any different, better than this:

> **livelite said:**
> I'm one of those having this issue as well, however, there is a neat workaround you might want to try.

It works by replacing the flash player on YouTube with an embedded Ubuntu movie player.

To do this you'll need FireFox, and the [Greasemonkey]("https://addons.mozilla.org/en-US/firefox/addon/748") extension with the [Youtube without Flash Auto]("http://userscripts.org/scripts/show/50771") script installed.


Once you do this, YouTube videos will play nicely in full screen, and might even handle those HD videos nicely if your pc had trouble viewing them with the flash player.

Enjoy ;)

---

### Post by Isti115 on 2010-11-13
> **drelyn86 said:**
> Kind of a weird bug... :confused:

I have dual monitors (both at 1280 x 1024, 2560 x 1024 total). When I view a youtube video in fullscreen, the video seems like it's changed to the aspect ratio to fit on a 2560 x 1024 screen, and then is shrunk down to just one screen, so it's a lot smaller than it should be (there are white bars above and below the video to fill the extra screen space). Is there any way I can get it to fill the whole screen (and just 1 monitor)?

I only have this problem on Youtube. Fullscreen videos are sized correctly on Hulu, Megavideo, Myspace, Ebaumsworld, por... well, you get the idea. 



Same for me, with ati radeon gfx card. 
Please help!

Thanks 
Isti115

---

### Post by zepolen on 2010-12-05
My workaround is to start the video in youtube, press pause, then go to /tmp where flash stores the flv filenames like FlashXXO4jkEi. Double clicking them opens them in your favorite player which can remain fullscreen.

---

### Post by Kangarooo on 2010-12-11
> **zepolen said:**
> My workaround is to start the video in youtube, press pause, then go to /tmp where flash stores the flv filenames like FlashXXO4jkEi. Double clicking them opens them in your favorite player which can remain fullscreen.

ROFL :D omg good one joke :D tv then is faster

great previous bugs are fixedd but now i have also this new bug-
Fullscreen is in correct one but not filled/streched.
[http://kangarooo.times.lv/dualflashfull.png](http://kangarooo.times.lv/dualflashfull.png)

---

### Post by Meneltaur on 2011-02-13
I run Ubuntu 10.10, and I found a simpler solution (see thread [http://ubuntuforums.org/showthread.php?t=973631&page=3):](http://ubuntuforums.org/showthread.php?t=973631&page=3):) simply goto System -> Appearance -> Visual Effects and select NONE.  Then the Youtube flash video in fullscreen will appear in the correct monitor.

I am new to Ubuntu, but if this is going to succeed for a more general audience someone has really got to make viewing Flash videos on Linux desktop a lot easier than this, it takes a lot of detective work.

---

### Post by Sylchat on 2011-02-21
You can try HTML5 video on youtube: [http://www.youtube.com/html5](http://www.youtube.com/html5)
then try this video [http://www.youtube.com/watch?v=siOHh0uzcuY](http://www.youtube.com/watch?v=siOHh0uzcuY) (on firefox 4 or latest Chrome, not Firefox 3.x)

The fullscreen is restricted to the window only but at least the video is bigger than with fullscreen flash (firefox 3, 64-bit flash 10.2)

---

### Post by felipemartim on 2011-02-28
sticky_icky's solution worked fine for me

---

### Post by kmolnar on 2011-04-18
While not perfect, Chrome users can install [this plugin]("https://chrome.google.com/webstore/detail/lljjmflmcnaigbhnheldbdbplkbhngnl#") to resize YouTube (and other Flash player-based) videos to fill the browser window.

Hit F11, and you have fullscreen.

I imagine there is something like this for Firefox, but I'm not sure. Not ideal, but a passable workaround for me.

---

### Post by livelite on 2011-04-18
A similar solution is to join the experimental youtube html5 player @ [youtube.com/html5]("http://youtube.com/html5") by going here and clicking join.  You can leave at anytime if a video won't work, or open that video in incagnito, so it will use the default flash player.

::: edit :::

Just noticed this was mentioned.  Well I used this for quite some time, and it's pretty reliable now, although work is still progressing, but this is the future :)

---

### Post by ram130 on 2011-05-04
So, any progress on the issue yet?

---

### Post by Vortex777 on 2011-05-04
I've tried the Flash Video Replacer and that works well for me. If you don't want to do that, the earlier suggestion of going to System -> Appearance -> Visual Effects and selecting *none* fixes it. If you have Ubuntu 11.04, changing the mode to Ubuntu Classic (No Effects) instead of Unity on the login screen will fix this issue as well.

---

### Post by ram130 on 2011-05-04
> **Vortex777 said:**
> I've tried the FlashVideoReplacer and that works well for me. If you don't want to do that, the earlier suggestion of going to System -> Appearance -> Visual Effects and selecting *none* fixes it. If you have Ubuntu 11.04, changing the mode to Ubuntu Classic (No Effects) instead of Unity on the login screen will fix this issue as well.

yeah but FlashVideoReplacer don't work with chrome and I love unity so don't want to disable it since it's so new and interesting to me.

---

### Post by Ziykuna on 2011-05-10
an easy fix for me was to enable the HTML5 Beta.

[http://www.youtube.com/html5](http://www.youtube.com/html5)

---

### Post by cmcginty on 2011-05-10
With HTML5 turned on, the full screen mode stays inside of the browser window. Is that what you get? Thanks for the tip.

---

### Post by aaron777 on 2011-05-11
when I use html5, yes it is in the browser window, which is how its meant to work I think. you can just hit F11 and wait a moment, then when the browser bars disappear (can be slow while video is playing), its basically the same as fullscreen flash.

none of the other fixes worked for me, but I just discovered youtube XL, for which the fullscreen flash works for me with dual monitors! (its a different flash player)
try it at [www.youtube.com/xl]("http://ubuntuforums.org/youtube.com/xl") the controls are massive, but they disappear after a few moments anyways :)
im interested to see if the player works for other people with dual monitors

so my solution to this problem: 
1. enable html5, which will work for a lot of youtube videos
2. for any that still load with flash, copy the video title, open youtube xl (ie via keyword / bookmark) and paste the title in its search box. voila!
...or you could just use youtube xl if that works for you :)

this fix would be perfect if anyone could figure out a search string to use with youtube xl
(ie the equivalent of [http://www.youtube.com/results?search_query=%s](http://www.youtube.com/results?search_query=%s))

-Aaron

---

### Post by Lord_JABA on 2011-05-14
Link to bug on lauchpad: [https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/376815](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/376815)
If we all click "[Does this bug affect you?"]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/376815/+affectsmetoo") maybe someone will fix it.

---

### Post by geokker on 2011-05-15
Thanks kmolnar, that Chrome plugin works well enough for me. For some reason, F11 doesn't work though, so if I menu-select fullscreen, I can't get back and have to kill the process.

Previously, I was using the YouTube plugin for the Totem movie player to fullscreen YouTube content.

---

### Post by DrVal on 2011-08-30
I found a slight work-around...

Lets say you want to watch:
[http://www.youtube.com/watch?v=mhSbi_o5AVQ](http://www.youtube.com/watch?v=mhSbi_o5AVQ)

Just change that URL a bit to:
[http://www.youtube.com/v/mhSbi_o5AVQ](http://www.youtube.com/v/mhSbi_o5AVQ)

it will come up in the imbedded version, and will scale to the size of the screen... you can then go to fullscreen.

---

### Post by carolinason on 2011-09-06
i'm using minitube a "desktop youtube client" to work around flash problems. it plays any youtube video full screen quite well. also running dual monitors made it hard to use a browser on each screen, since clicking in one would disable the fulls screen in the other. this is a work around, but it has turned out to be one with added features.

---

### Post by andrewthemerry on 2012-02-19
> **DrVal said:**
> I found a slight work-around...

Lets say you want to watch:
[http://www.youtube.com/watch?v=mhSbi_o5AVQ](http://www.youtube.com/watch?v=mhSbi_o5AVQ)

Just change that URL a bit to:
[http://www.youtube.com/v/mhSbi_o5AVQ](http://www.youtube.com/v/mhSbi_o5AVQ)

it will come up in the imbedded version, and will scale to the size of the screen... you can then go to fullscreen.
Thank you ::)

---

### Post by ram130 on 2012-02-19
any update? and any new fixes?

---

### Post by Garrettishere on 2012-08-16
If anyone is still having issues with this (and uses chrome/chromium), head to the web store and grab Popout for Youtube [(web store page)]("https://chrome.google.com/webstore/detail/pofekaindcmmojfnfgbpklepkjfilcep"). 

It's an extension which allows you to launch any Youtube video in a separate, resizable window. Thus, giving you full screen capability. The nice thing about it is that the launcher sits in the top right of the video so it's really easy to use.

Anyways, that's what I've come up with and it's worked great so far.

---

### Post by Viniciuswl on 2012-08-28
Problem solved for my firefox! 

Edit the flashplayer binary in a hex editor. To get hex editor:
```
*sudo apt-get install ghex*
```then
```
*sudo ghex /usr/lib/flashplugin-installer/libflashplayer.so*
```Search for _NET_ACTIVE_WINDOW and replace it with some other string of the same length, e.g. __ET_ACTIVE_WINDOW

Restart FF.

Source: [http://www.ubunturoot.com/2011/07/fullscreen-flash-video-with-dual.html](http://www.ubunturoot.com/2011/07/fullscreen-flash-video-with-dual.html)

---

