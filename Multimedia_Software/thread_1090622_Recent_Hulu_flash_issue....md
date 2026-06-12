---
title: "Recent Hulu flash issue..."
date: 2009-03-08
forum: Multimedia Software
---

### Post by RonPDX on 2009-03-08
[FONT="Tahoma"][SIZE="2"]
Good Morning everyone, 

I recently have come across an interesting issue with Hulu and couple of other flash sites, starting about 2-3 weeks ago (up until then flash worked great) there are certain shows (Terminator, ER, Burn Notice, etc) that stall or are choppy, yet older shows like The Pretender or A Team play perfectly. 

After exhausting all of the Google possibilities I am hoping that someone can help figure out where the problem may be. This problem is only occurring in Ubuntu, if I switch over to Windoze flash again plays perfectly. I have already followed the pinned tutorial relating to flash with no success and I have also eliminated Compiz as being my flash culprit. I primarily run Firefox but I have also tried Opera only to find that the problems are occurring.

Any Ideas?

Thanks, 

Ron 

  
[/SIZE][/FONT]

---

### Post by warp99 on 2009-03-08
I"m sure your talking about flash in fullscreen, correct? If so the reason that the video is choppy on the newer flash video is because it's using an opengl acceleration string embedded in the video and your flash is not using the hardware acceleration, but only the software rendering.

I had a similar problem until I made some changes using the nvidia-settings app included with the restricted drivers. If you're using the open nv drivers then there's a problem. These use the mesa glx extensions which Adobe in their "wisdom" will not allow hardware acceleration if these extensions are loaded. It's explained here at one developers blog site:

[http://blogs.adobe.com/penguin.swf/2008/05/flash_uses_the_gpu.html](http://blogs.adobe.com/penguin.swf/2008/05/flash_uses_the_gpu.html)

So the problem is 100% Adobe's since they can't seem to get their act together.

---

### Post by RonPDX on 2009-03-10
Warp 99, 

Thank you for your advice, while I read the posts on the links you provided I found that most of it was a little over my head. 

I did solve all of my flash problems though my trying a couple different things. 

First I tried downloaded/installing the Nvidia 177 drivers via Synaptic Package Manger only to find out that the drivers do not support the GeForce 5700LE, the only drivers that appear to be supported is the 96 and 173 series drivers.I uninstalled/reinstalled the 173 series drivers and that appeared to do the trick. After restarting, full screen flash is working like it should, no stalling, etc. 

Now I am wondering what had caused the problem with my drivers and how to avoid it in the future. 

Thanks again Warp 99 for your help, it is appreciated. 

Ron

---

### Post by RonPDX on 2009-03-10
Apparetly I spoke too soon --

While some issues were solved with reinstalling the 173 drivers, some of the recent Hulu videos are still almost unwatchable. Since most of these problems are recent I am wondering if would help to downgrade from flash 10 to flash 9? Does anyone have idea if this would help or am I out-of-luck since this an adobe issue.

**Update**

Since this appears to be an issue with OpenGL and Flash, I have reverted back to onboard graphics. 

Thanks everyone for your help.

Ron

---

### Post by warp99 on 2009-03-10
The simple answer is that the newer Hulu videos are authored to take advantage of the graphics processing unit (GPU) on your video card while the older videos use legacy mode instead. Unfornately on you system Adobe Flash is not using the GPU hardware acceleration on the newer videos, but instead is falling back to software mode instead. 

When this happens 100% of your CPU is being used to run Adobe Flash. The skipping is the wait state since Adobe still wants more CPU cycles but only so many are available. Why is Adobe falling back to software mode? It could be one or more of these reasons:

1) Compiz is running at the same time
2) Your GLX rendering vendor is "SGI"
3) Some of the Opengl libraries are missing
4) Nvidia-settings configuration issues

Even with all of these issues in check Adobe Flash is **still** a resource hog. Case in point, I have a mythTV server with a 256MB nVidia 6200 video card, an AMD 3400+ CPU, and the compositing extensions disabled. Even with GPU hardware acceleration Adpbe Flash will consumer **60%-80%** CPU.

Think that's bad on my other machine which has **two** 512MB nVidia 9500 GT in SLI mode, an Intel 8200 Quad Core CPU, and running Kubuntu 8.04 64-bit, Adobe Flash will use **30%-50%** CPU. To be fair the 64-bit version of Flash does not use any hardware acceleration and defaults to software mode.

The only one here to blame is Adobe since it's ridiculous that so much CPU processing power is needed to run something as simple as a video. If I downloaded the video and played it in mplayer I use 2-3% CPU at the most. Nice way for Adobe to encourage bittorent, isn't it? :)

---

### Post by RonPDX on 2009-03-10
Warp 99 -- 

I have to agree, Adobe is such a resource hog and hopefully one day they will get things together. While trouble shooting this issue I disabled compiz and was having the same result, unfortunately my onboard graphics is black-listed by compiz for good reason, it crashes :(. 

After looking at the GLX rendering, my vendor is SGI, this is why I finally switched back to onboard even though the performance is not as good. 

With all of these problems, it is only encouraging me to either build or buy a new system and keep this one as a myth-backend. :) 

Now only if Hulu would allow us to download content and use mplayer...

Thanks again for all of your help & Wisdom, 

Ron

---

### Post by RonPDX on 2009-03-26
Well here I am back dealing with the flash saga. 

After switching back to onboard video I was still have flash problems, so I switched back to my graphics card. So the question is what else I can do to try fix this flash issue.

I thought this problem was only related to full screen however I am finding that I am even having problems in a normal window. So the question is, where can start looking or what changes can I make to help with these issues? I really don't want to switch over to Windoze every time I need flash. I did notice that most of these problems happened after one of the repo updates...

Thanks again for all of your help, it is really appreciated. 

Ron

---

### Post by fixitdude on 2009-03-28
It's fixed!

I had the problem that many flash videos, including hulu and nbc, were skipping, always had to download them using a Firefox plugin which doesn't work with hulu, talk about annoying.

I upgraded everything a few days ago using synaptic package manager and it had a new kernel 2.6.22-16-generic, so I rebooted and now it plays great! I'm on Gutsy.

So try to do a update on everything, reboot and see if that works.

---

### Post by RonPDX on 2009-03-28
> **fixitdude said:**
> It's fixed!

I had the problem that many flash videos, including hulu and nbc, were skipping, always had to download them using a Firefox plugin which doesn't work with hulu, talk about annoying.

I upgraded everything a few days ago using synaptic package manager and it had a new kernel 2.6.22-16-generic, so I rebooted and now it plays great! I'm on Gutsy.

So try to do a update on everything, reboot and see if that works.

Thanks -- everything updated and running perfectly including full-screen flash.

---

### Post by B34N on 2009-03-30
> **fixitdude said:**
> It's fixed!

I had the problem that many flash videos, including hulu and nbc, were skipping, always had to download them using a Firefox plugin which doesn't work with hulu, talk about annoying.

I upgraded everything a few days ago using synaptic package manager and it had a new kernel 2.6.22-16-generic, so I rebooted and now it plays great! I'm on Gutsy.

So try to do a update on everything, reboot and see if that works.

No luck for me.  The CPU usage does spike to 100% when in full-screen.  The problem is the same on two completely different machines.  It seemed to start happening about three weeks ago.  I uninstalled and reinstalled flash as suggested here : [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

What more should I try?
I'm not using ATI video cards.

Thank you!

---

### Post by fixitdude on 2009-04-05
fieroboom made a good suggestion you could try, remove the "flashplugin-nonfree" and install "adobe-flashplugin", that may work.

[http://ubuntuforums.org/showthread.php?t=1092624&p=7003729](http://ubuntuforums.org/showthread.php?t=1092624&p=7003729)


sudo dpkg --purge flashplugin-nonfree

sudo apt-get update

sudo apt-get install adobe-flashplugin

---

### Post by B34N on 2009-04-06
> **fixitdude said:**
> fieroboom made a good suggestion you could try, remove the "flashplugin-nonfree" and install "adobe-flashplugin", that may work.

[http://ubuntuforums.org/showthread.php?t=1092624&p=7003729](http://ubuntuforums.org/showthread.php?t=1092624&p=7003729)


sudo dpkg --purge flashplugin-nonfree

sudo apt-get update

sudo apt-get install adobe-flashplugin

I gave it a shot.  The first two commands execute perfectly and the last ends with "Couldn't find package adobe-flashplugin".  So I went to the Adobe site to D/L and install install_flash_player_10_linux.deb.  I reinstalled it and the problem remains.  The video gets choppy only on full screen.  System resources get pegged.  Works fine in XP so I think it's a config issue on my side.  Any thoughts?

---

### Post by bobbo85 on 2009-04-10
Are there any plans to get this fixed?

I would like to put Ubuntu on my mom's comp, but one of the only things she does with her computer is watch youtube videos and hulu episodes.

I have not seen any easy work arounds yet, but here's what I have seen:
-editing a flash.so file with a hex editor
-disabling compiz (do the new OS's have window managers to fall back on?  i think they come with compiz pre-installed) with that 'replace metacity' command in the terminal

Has anyone found a good *working* work around?  Or is there a fix being made?  

It's a bummer that I'm holding off on spreading the linux love to older windows users, but honestly watching videos online is becoming more and more popular - to the point that nobody would use an OS that could not play them in full screen without the abortion of video quality that currently presents itself.

I mean I hate it too when I have to reboot into windows.  It just seems so ironic that linux is so much more powerful, so limitless, it seems like it can do anything - but it shits its pants at the thought of watching an episode of family guy on hulu.

---

### Post by RonPDX on 2009-04-11
My flash was working for a short time after updating and know I am back to the original problem, even with Epiphany. I am currently using Wubi, as soon as Jaunty is realeased I will be moving to a dedicated partition which I am hoping may solve the problem. 

Until then, does anyone have any other ideas?

Thanks

---

### Post by fixitdude on 2009-04-19
I wonder what would happen if you ran Firefox under Wine and had Flash on that?

---

### Post by moserine on 2009-04-21
I have been having this problem also--after doing a little bit of searching I came across this thread: [http://forums.linuxmint.com/viewtopic.php?f=61&p=142201](http://forums.linuxmint.com/viewtopic.php?f=61&p=142201)

One person mentions that the problem is related to the underlying gnome architecture, so, as a simple (if drastic) solution, I switched to KDE. After watching several videos on Hulu I can say that performance is significantly improved. Though not perfect, it skips WAY less on normal screen size.

Kind of drastic, yes, but, if you're like me you can't live without those episodes. :)

---

### Post by bobbo85 on 2009-04-24
I found a bug report at adobe.com and voted for it to be fixed.  

Please vote for the issue to be addressed here (I did) so we can watch videos in full-screen at last!
[http://bugs.adobe.com/jira/browse/FP-1692](http://bugs.adobe.com/jira/browse/FP-1692)

---

### Post by Quiet_Melvin on 2009-04-29
I've been having this exact same issue, although my experiences are not limited to watching flash in full screen mode.  Running flash through firefox routinely consumes a massive amount of my CPU, usually approaching 70Your password has now been reset and emailed to you. Please check your email to find your new password. To change your password, please use this form 70%, and will continue this consumption so long as flash continues to run.  Immediately after ceasing flash use, the CPU usage quickly abates, however if I continue to let it run my CPU will overheat and eventually cause Ubuntu to shutdown.

I've voted for the fix on the Adobe website, hopefully we can finally get some movement on this issue.

---

### Post by julia.l.acuna on 2009-05-25
I am also having problems watching hulu, or cbs videos.  I tried downloading adobe flash player.  I am new to ubuntu so please be patient with me.  I am not able to see videos at all.  I can watch youtube videos.  When I go to hulu I get a blank screen.  Do you have any suggestions?

---

