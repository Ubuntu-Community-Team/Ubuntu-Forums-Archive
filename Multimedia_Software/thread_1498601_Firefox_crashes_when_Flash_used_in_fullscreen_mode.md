---
title: "Firefox crashes when Flash used in fullscreen mode (after upgrade to Ubuntu 10.04)"
date: 2010-06-01
forum: Multimedia Software
---

### Post by samba on 2010-06-01
Hi all,

I just upgraded to Ubuntu 10.04 from 9.10, and now I can't view any Flash video in fullscreen mode (Youtube, atdhe, etc.). When I click on fullscreen Firefox crashes instantly. Everything was working fine in 9.10.

I looked around on the forums; I tried to install the Flash-Aid extension for Firefox. It says that my architecture is 32bit, then reinstalls the Flash plugin, but that doesn't help; fullscreen still crashes. I also tried to install the 64bit version from Adobe's website, but that doesn't help. 

I had a look at the mozilla website [http://support.mozilla.com/en-US/kb/Cannot+view+full+screen+Flash+videos;](http://support.mozilla.com/en-US/kb/Cannot+view+full+screen+Flash+videos;) I tried to preload the libGL.so.1 library as suggested there, but that doesn't help. I wanted to try to disable hardware acceleration in the Flash player settings, but I can't even change the settings; when I right-click on Settings, the adobe small preferences screen appears but I can't click on anything, nothing works.

That's all on Ubuntu 10.04 with Firefox 3.6.3 and Flash Player 10,0,45,2. I also installed the newer 10.1 Flashplayer plugin from the Adobe website, but Firefox still crashes.

Is that a well known bug? Anyone knows how to solve it?

Thanks a lot! :-)
Vincent

---

### Post by samba on 2010-06-01
I just found a way of getting full screen to work, but I had to install Google Chrome. Basically, the problem was hardware acceleration. But since I could not (and still cannot) access the Flash Player Settings from Firefox, I could not disable hardware acceleration. So I installed Google Chrome, and then magically in Google Chrome I could access the Flash Player settings! So I disabled hardware acceleration in Google Chrome, and then full screen works. Since hardware acceleration is now disabled by default, full screen mode now works in Firefox as well.

Kinda weird though that I had to install Google Chrome to get Flash Player to work in Firefox...

Vincent

---

### Post by lovinglinux on 2010-06-01
If you are using a 64bit version of Firefox, then get the latest [FLASH-AID 1.0.3](http://flash-aid-extension.blogspot.com). It fixes a bug that was causing the extension to detect 64bit browsers as 32bit.

Also check if you have libmoon installed and remove it. This is part of Moonlight (Silverlight) plugin and it is known to cause such crashes when viewing flash content.

If you don't have it, you could try Firefox 3.6.4, which has a feature that isolates the flash process, so if flash crashes the browser doesn't crash. See the [[COLOR="Sienna"]**Installing Other Versions**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/installing-other-versions.html) and  [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by samba on 2010-06-01
Thanks lovinglinux for the advices. I did have Flash-AID 1.0.3 installed, but I'm really using a 32bit version of Firefox (I think). However I did have a "moonlight" folder in ~/.mozilla/plugins (even though I had uninstalled the Moonlight plugin a long time ago). I removed that folder, but it didn't help.

In any case, with hardware acceleration disabled, full screen now works. I could try installing Firefox 3.6.4, but well for now I'll keep with no hardware acceleration (in fact I have to say that I quite like Chromium as well, I'd never tried it... :-)

Cheers,
Vincent

---

### Post by lovinglinux on 2010-06-01
> **samba said:**
> Thanks lovinglinux for the advices. I did have Flash-AID 1.0.3 installed, but I'm really using a 32bit version of Firefox (I think).

But you said you have tried the 64bit flash from Adobe. Anyway, go to Firefox Help menu and click About Firefox. It will show the browser version, architecture and other info.

> **samba said:**
> However I did have a "moonlight" folder in ~/.mozilla/plugins (even though I had uninstalled the Moonlight plugin a long time ago). I removed that folder, but it didn't help.

Try this:

```
sudo apt-get purge libmoon
```

On a second thought, libmoon crashes Firefox even when not in full screen. So I'm not sure this could be the cause of your problem.

> **samba said:**
> In any case, with hardware acceleration disabled, full screen now works. I could try installing Firefox 3.6.4, but well for now I'll keep with no hardware acceleration (in fact I have to say that I quite like Chromium as well, I'd never tried it... :-)

I don't like Chrome/ium. I like some concepts behind the browser like sandboxing and separate process for each tab, but you can't do almost any customization, extensions are limited and awkward, I can't integrate KDE password management with it, there is no sidebar...the list goes on. I can't be productive with it.

---

### Post by samba on 2010-06-01
> **lovinglinux said:**
> But you said you have tried the 64bit flash from Adobe. Anyway, go to Firefox Help menu and click About Firefox. It will show the browser version, architecture and other info.

To be honest, I know almost nothing about 32bit/64bit. But my architecture is i686, so I guess it's 32bit (which is why the 64bit Adobe version didn't work :-). 

In fact, is it worth installing the 64bit version of Ubuntu on my desktop? (my processor is Core 2 quad -- and Core 2 duo at work -- so they are 64bits I guess) I'm not a gamer, and not very much into video stuff...



> 
Try this:

```
sudo apt-get purge libmoon
```

On a second thought, libmoon crashes Firefox even when not in full screen. So I'm not sure this could be the cause of your problem.


OK I'll try that when I go back home and see what happens.

> 
I don't like Chrome/ium. I like some concepts behind the browser like sandboxing and separate process for each tab, but you can't do almost any customization, extensions are limited and awkward, I can't integrate KDE password management with it, there is no sidebar...the list goes on. I can't be productive with it.

I guess I haven't used Chromium enough by now to see if it really like it... (I only used it for a few hours! :-)

Thanks again,
Vincent

---

### Post by lovinglinux on 2010-06-01
> **samba said:**
> In fact, is it worth installing the 64bit version of Ubuntu on my desktop? (my processor is Core 2 quad -- and Core 2 duo at work -- so they are 64bits I guess) I'm not a gamer, and not very much into video stuff...

They can be 32bit too. Depends if you installed the 64bit version of Ubuntu or the 32bit. You can run the command below to make sure:

```
uname -a
```

The 64bit plugin is better.

---

### Post by gaby-cta-ro on 2010-10-12
> **samba said:**
> Thanks lovinglinux for the advices. I did have Flash-AID 1.0.3 installed, but I'm really using a 32bit version of Firefox (I think). However I did have a "moonlight" folder in ~/.mozilla/plugins (even though I had uninstalled the Moonlight plugin a long time ago). I removed that folder, but it didn't help.

In any case, with hardware acceleration disabled, full screen now works. I could try installing Firefox 3.6.4, but well for now I'll keep with no hardware acceleration (in fact I have to say that I quite like Chromium as well, I'd never tried it... :-)

Cheers,
Vincent


Exactly the same problems happened to me on Ubuntu 10.10, Firefox 3.6.10, adobe flash 10. I tried all of the above, and others, and nothing seemed to work !!!:( Untill i read this topic !!! Thanks very much "samba" !!! The simple fact of unchecking "hardware acceleration" in flash settings did it ! The only difference is that i could make this change from Firefox flash settings.

 Thanks again !
All the best !

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

### Post by Tian102983 on 2010-10-29
Try this.
Open Fire Fox.
Go To A Flash Video.
Right Click On It.
Go To Settings.
Disable or Uncheck Hardware Accelerations.

I found that this worked for me, and now I can view everything in full screen without lag so far. And I didn't have to download anything, or change anything in terminal.

Google Chrome won't allow me to right click flash, but I find that changing the settings in Firefox, will change the settings for Google Chrome.

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

Wow. That really makes me happy. I'm the developer of FlashVideoReplacer. :)

---

### Post by ohurcool73 on 2010-12-08
> **Tian102983 said:**
> Try this.
Open Fire Fox.
Go To A Flash Video.
Right Click On It.
Go To Settings.
Disable or Uncheck Hardware Accelerations.

I found that this worked for me, and now I can view everything in full screen without lag so far. And I didn't have to download anything, or change anything in terminal.

Google Chrome won't allow me to right click flash, but I find that changing the settings in Firefox, will change the settings for Google Chrome.


Thank You for the suggestion this definitely helped me the most on google chrome on 10.10 i've had the problem since i upgraded to 10.04 and i just upgraded to 10.10 and still had the problem after doing this it is now fixed. Thank You so much

---

### Post by HeYzN on 2011-01-10
Disabling hardware acceleration worked - full screen didn't crash my flash - but video was slow and choppy.

I have a solution that worked perfect for me though :)
Changing my nvidia driver.

My spec:
Lenovo T61 with ubuntu 10.04 LTS
nVidia card

How to:
system -> administration -> hardware drivers
this opened for me a window with two options for the nvidia proprietary driver
- NVIDIA accelerated graphics driver (version 173)
- NVIDIA accelerated graphics driver (current version) [Recommended]

I (think) I down graded from the recommended current version to the 173 version by clicking activate button for 173 version. after install was prompted to restart computer.
restarted - flash videos now work in full screen without problems and high quality/speed.
no need to disable hardware acceleration either.

---

