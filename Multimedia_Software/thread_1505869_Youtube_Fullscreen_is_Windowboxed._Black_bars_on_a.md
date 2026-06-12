---
title: "Youtube Fullscreen is Windowboxed. Black bars on all four sides."
date: 2010-06-09
forum: Multimedia Software
---

### Post by tropicalfish on 2010-06-09
I am running Ubuntu Lucid Lynx 10.04. I am also running Mozilla Firefox 3.6.3. (As far as I know I don't get this on my Windows installation).

This is my problem:
My full screen is being windowboxed. I have black bars on the top, bottom, left and right of the video. This shrinks the video by a large amount.

I have the seekbar shown in the following pictures so you know that it doesn't appear at the very bottom of the screen like it should.
4:3 videos like this: [http://www.youtube.com/watch?v=Mnb23O-I_O4](http://www.youtube.com/watch?v=Mnb23O-I_O4)
[http://i144.photobucket.com/albums/r183/mrairplaneman777/1-7.jpg](http://i144.photobucket.com/albums/r183/mrairplaneman777/1-7.jpg)

16:9 videos like this: [http://www.youtube.com/watch?v=5LPzvVzF1Fo](http://www.youtube.com/watch?v=5LPzvVzF1Fo)
[http://i144.photobucket.com/albums/r183/mrairplaneman777/2.jpg](http://i144.photobucket.com/albums/r183/mrairplaneman777/2.jpg)

---

### Post by WinterRain on 2010-06-09
I have noticed some sites do full screen properly, and some don't. I live with it. Besides, most flash videos look like crap full screen anyway.

Hopefully, someone can give you some answers.

---

### Post by tropicalfish on 2010-06-09
> **WinterRain said:**
> Besides, most flash videos look like crap full screen anyway.

Unless it's HD 720 or above...

Which is sort of disappointing because they appear to be the same size as if the video wasn't fullscreened but in the "larger" viewing mode on the Youtube page.

---

### Post by prince_sabin on 2010-06-09
It seems that the flash video isn't being stretched when you go to full screen.  The 1080p on my computer fills the screen but the 720p is boxed

This may or may not be a good solution for you, but you can always use compiz to zoom in on the video while in full screen.  Use <super>and mouse wheel up.  This is hardware accelerated upconverting(the zoom provides basic pixel interpolation), and is lighter on computer resources than flash.

I was zooming in on flash videos with compiz before there was full screen.

---

### Post by lovinglinux on 2010-06-09
There is definitely something really wrong. The entire player, including controls are not fitting the screen size.

I'm not sure what could be causing this, but I would start checking if you have the latest proprietary driver for your video card installed. Then try to disable Compiz effects. Also check which version of flash you have. [This extension](http://flash-aid-extension.blogspot.com) will help you fix any flash version compatibility issues.

I also recommend creating a new Firefox profile to see if the problem persists. See [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by WinterRain on 2010-06-09
> **lovinglinux said:**
> There is definitely something really wrong. The entire player, including controls are not fitting the screen size.

I'm not sure what could be causing this, but I would start checking if you have the latest proprietary driver for your video card installed. Then try to disable Compiz effects. Also check which version of flash you have. [This extension](http://flash-aid-extension.blogspot.com) will help you fix any flash version compatibility issues.

I also recommend creating a new Firefox profile to see if the problem persists. See [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

Tried all that, does not help. Then again, I can live with the smaller sized flash windows. It's weird that full screen works fine on some sites, (like nfl.com) but not others. But, when I go full screen on youtube, it is not full screen, but twice the size of the normal video which is good enough for me.

---

### Post by lovinglinux on 2010-06-09
> **WinterRain said:**
> Tried all that, does not help. Then again, I can live with the smaller sized flash windows. It's weird that full screen works fine on some sites, (like nfl.com) but not others. But, when I go full screen on youtube, it is not full screen, but twice the size of the normal video which is good enough for me.

I subscribe to a video site that doesn't go full screen as it should, but the problem is that the site platform doesn't support Linux well. Firefox, Chrome and Opera open a new window instead of a real full screen. Anyway, what I do is use Kwin zoom feature instead of the player full screen. 

> **prince_sabin said:**
> It seems that the flash video isn't being stretched when you go to full screen.  The 1080p on my computer fills the screen but the 720p is boxed

This may or may not be a good solution for you, but you can always use compiz to zoom in on the video while in full screen.  Use <super>and mouse wheel up.  This is hardware accelerated upconverting(the zoom provides basic pixel interpolation), and is lighter on computer resources than flash.

I was zooming in on flash videos with compiz before there was full screen.

Compiz also has a nice option that allows you select the area you want to zoom with the mouse. I don't remember how to do it tho, since I'm using KDE with Kwin for a while.

---

### Post by themusicalduck on 2010-06-09
Do you happen to use dual monitors? I have this same problem. I read somewhere it was to do with the fact that Youtube sizes the player as if it were stretched over both monitors.

To zoom into a specific space press the super key and drag with left click.

---

### Post by tropicalfish on 2010-06-10
Yes, I do use dual monitors. Two 17" at 1280x1024.

Oh, and zooming into a specific space is Super/Start + Scroll wheel (click).

---

### Post by tropicalfish on 2010-06-10
Looking at my ATI settings, it says my total desktop area is 2560x1024... which could be causing the issue. Though, full screen is only on one monitor...

...and Xinerama sucks, so I don't want to use that.

---

### Post by tropicalfish on 2010-06-18
Bumpity bump.

---

### Post by AllRadioisDead on 2010-09-30
I'm having the same problem, does anyone have a solution?

---

### Post by sticky_icky on 2010-10-28
**I HAVE THE SOLUTION** for this problem, for everybody that has flash issues, _when all embedded flash goes fullscreen on every site except youtube or googevideos_.  **I HAVE THE SOLUTION** for this problem, for everybody that has flash issues, _when all embedded flash goes fullscreen on every site except youtube or googevideos_.  

      I wish to christ i could have found this years ago...  i have the  same  problem, main monitor is 1440x900, running an xfx geforce 7600gt,  and  everything but youtube works.  flash/youtube/ubuntu=HUGE #$^@##@   headaches for years.  i tried litterally hundreds of workarounds or   fixes, HOURS of time trying to get the stupid flash fixed for more than 2   minutes, and not one single thing worked, ever, until now.t

      ubuntu forums had been completely useless to me, in those  endeavors,  wasted much time for nothing, though, in fairness to the  buntu, i fully  acknowledge the fruitful efforts of the ubuntu team, the  linux world has  made HUGE strides forward since i started with  slackware7.   with  ubuntu, the reality is that aside from arbitrary  reference, i haven't  needed the forums, everything but flash, some  really obscure software,  works like a charm, since the nvidia driver  issues have been  sorted.(btw, for me, the only way to install properly  working nvidia  drivers/nvidia settings/flashplugin is with apt from  terminal after  stopping gnome...**not with synaptic from the desktop**)

     since nothing's ever worked for me, i didn't bother reading the  thread, i'd be shocked if it was mentioned... anyway, after a routine  cleaning/reinstallation of firefox i happened across this:[ http://www.addonfox.com/]("http://www.addonfox.com/"),   which icludes some really good addons for firefox....also some bs, the   converter, swifclick, and windowshopper addons pissed me off...

the real gem of that collection, which i had never found before is:

**[flashvideoreplacer 1.0.5]("https://addons.mozilla.org/en-US/firefox/addon/161869/")**

      it "replaces embedded flash videos with quicktime or windows media   player compatible videos."   WHAT THAT MEANS IS IT COMPLETELY REPLACES   THE WHOLE, STUPID, YOUTUBE/GOOGLEVIDEO GUI AND **EMBEDS IN ITS PLACE MPLAYER**.
(in the preferences,the selection for plugin/mimeType, is "windows media player (application/x-mplayer2)

hall-o-fu#%ing-luja!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

     _**this is the only thing that has ever worked for me**_,   and it seems to be a really solid addon, so far as i can tell, not   buggy, video looks great-not choppy, options exist to automatically   choose the quality of youtube videos, choose cache size(default is   2megs), enable post processing, all the gnome mplayer interface   settings, etc.  _it doesn't seem to change anything on any video sites except youtube/googlevideos, and optionally vimeo and blip.tv etc._  only problem is i haven't been able to get the youtube playlist to autoplay the next vid.

if  you are frustrated wit yt/google, try this.  i can confir, it works   with gnome mplayer on 10.04.1 LTS.  i have every video and audio   application i could find, though, not sure of the impact other packages   have on mplayer/vice-versa.
[B]
hope this works for you, NO need to thank me if it does, but--

         PLEASE[/B] **PLEASE PLEASE help others when you have solutions.**

god bless.

---

### Post by lovinglinux on 2010-10-29
> **sticky_icky said:**
> **I HAVE THE SOLUTION** for this problem, for everybody that has flash issues, _when all embedded flash goes fullscreen on every site except youtube or googevideos_.  **I HAVE THE SOLUTION** for this problem, for everybody that has flash issues, _when all embedded flash goes fullscreen on every site except youtube or googevideos_.  

      I wish to christ i could have found this years ago...  i have the  same  problem, main monitor is 1440x900, running an xfx geforce 7600gt,  and  everything but youtube works.  flash/youtube/ubuntu=HUGE #$^@##@   headaches for years.  i tried litterally hundreds of workarounds or   fixes, HOURS of time trying to get the stupid flash fixed for more than 2   minutes, and not one single thing worked, ever, until now.t

      ubuntu forums had been completely useless to me, in those  endeavors,  wasted much time for nothing, though, in fairness to the  buntu, i fully  acknowledge the fruitful efforts of the ubuntu team, the  linux world has  made HUGE strides forward since i started with  slackware7.   with  ubuntu, the reality is that aside from arbitrary  reference, i haven't  needed the forums, everything but flash, some  really obscure software,  works like a charm, since the nvidia driver  issues have been  sorted.(btw, for me, the only way to install properly  working nvidia  drivers/nvidia settings/flashplugin is with apt from  terminal after  stopping gnome...**not with synaptic from the desktop**)

     since nothing's ever worked for me, i didn't bother reading the  thread, i'd be shocked if it was mentioned... anyway, after a routine  cleaning/reinstallation of firefox i happened across this:[ http://www.addonfox.com/]("http://www.addonfox.com/"),   which icludes some really good addons for firefox....also some bs, the   converter, swifclick, and windowshopper addons pissed me off...

the real gem of that collection, which i had never found before is:

**[flashvideoreplacer 1.0.5]("https://addons.mozilla.org/en-US/firefox/addon/161869/")**

      it "replaces embedded flash videos with quicktime or windows media   player compatible videos."   WHAT THAT MEANS IS IT COMPLETELY REPLACES   THE WHOLE, STUPID, YOUTUBE/GOOGLEVIDEO GUI AND **EMBEDS IN ITS PLACE MPLAYER**.
(in the preferences,the selection for plugin/mimeType, is "windows media player (application/x-mplayer2)

hall-o-fu#%ing-luja!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

     _**this is the only thing that has ever worked for me**_,   and it seems to be a really solid addon, so far as i can tell, not   buggy, video looks great-not choppy, options exist to automatically   choose the quality of youtube videos, choose cache size(default is   2megs), enable post processing, all the gnome mplayer interface   settings, etc.  _it doesn't seem to change anything on any video sites except youtube/googlevideos, and optionally vimeo and blip.tv etc._  only problem is i haven't been able to get the youtube playlist to autoplay the next vid.

if  you are frustrated wit yt/google, try this.  i can confir, it works   with gnome mplayer on 10.04.1 LTS.  i have every video and audio   application i could find, though, not sure of the impact other packages   have on mplayer/vice-versa.
[B]
hope this works for you, NO need to thank me if it does, but--

         PLEASE[/B] **PLEASE PLEASE help others when you have solutions.**

god bless.

Thanks for your comments about FlashVideoReplacer.

---

### Post by snevs on 2011-09-11
Fixed in: 
11.0.1.129-0ubuntu0~sevenmachines1

---

### Post by Rusna on 2011-11-18
I have this issue. Just installed clean 11.10 and Chromium. Yes, it's persistent with Firefox as well.

Any fixes? And no, replacing flash with video converter is not a suitable solution. It's just a workaround.

---

