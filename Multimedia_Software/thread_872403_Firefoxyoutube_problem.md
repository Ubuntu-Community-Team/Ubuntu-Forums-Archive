---
title: "Firefox/youtube problem"
date: 2008-07-27
forum: Multimedia Software
---

### Post by dondad on 2008-07-27
Running 8.04.1 on Dell xps 410 nvidia 8600 video. Periodically I will be trying to watch either a youtube or embedded video and will get a blank white screen where the video should be. Sometimes it works fine, but after a few videos it sometimes will not play. Reloading or refreshing the page does not help. I can close Firefox and reopen it to the same page and it works fine. Seems to occur more often if I close a video before it is done.

Any idea what could be causing this and how to fix it?

---

### Post by tamoneya on 2008-07-28
what are you using for your flash plugin?  have you tried the new flash 10 beta.

[http://markusthielmann.com/blog/flash_10_beta_ubuntu_hardy](http://markusthielmann.com/blog/flash_10_beta_ubuntu_hardy)

site appears a little messed up but just scroll down to the bottom.

---

### Post by dondad on 2008-07-28
> **tamoneya said:**
> what are you using for your flash plugin?  have you tried the new flash 10 beta.

[http://markusthielmann.com/blog/flash_10_beta_ubuntu_hardy](http://markusthielmann.com/blog/flash_10_beta_ubuntu_hardy)

site appears a little messed up but just scroll down to the bottom.

Thanks. I installed it. Will let you know if it helps.

---

### Post by rawlins02 on 2008-07-29
I'm also trying to set up a video player. Running Ubuntu 7.10. Installed libflash package successfully:

> sudo apt-get install libflash-mozplugin

Setting up libmad0 (0.15.1b-2.1ubuntu1) ...

Setting up libflash0c2 (0.4.13-9ubuntu1) ...

Setting up libflash-mozplugin (0.4.13-9ubuntu1) ...


But when I start firefox and type about:plugins into the address bar I don't see the plugin. At sites with video I'm seeing, "Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. Get the latest Flash player."

EDIT:  I've just deleted libflash-mozplugin...am following instructions on the sticky:
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by dondad on 2008-08-01
> **dondad said:**
> Thanks. I installed it. Will let you know if it helps.

I installed it and things seem to be better than they were, but it still sometimes freezes up partway through a video and the only way that I have found to get it back is to close Firefox and reopen it. Sometimes this will fix it and it plays all the way through.

Any idea what else I can try or any way to try to track down the problem?

---

### Post by henrik_daver on 2008-09-30
I'm having kind of the same problem. I too get the white/grey boxes instead of Flash videos from time to time, but I guess that's a Flash problem that will be resolved in coming releases.

The video freeze problem is something else, though. Every time I try to play a video in Firefox, be it in Mplayer or Flash, it halts after approximately two seconds every time. Anyone has some solution to this?

I'm using Firefox version 3.03. Didn't experience this until some month ago, maybe it is a Firefox issue?

Cheers,
Henrik

---

### Post by Aviendha2008 on 2008-10-23
I have the same problem with youtube freezing up after 2 secs. This has started about a week ago with kernel upgrade to 2.6.24-21.

---

### Post by enque on 2008-12-16
This thread is about the white-box problem, the freezing is something else and have been discussed in other threads, as well as the sound freezing thing.

I also have this problem, and I've had it since about september/october and have awaited a fix to appear but nobody seems to mention it. I'm sick of it so that's why I'm posting in this thread -- to bump the issue.

**Here is my description:**
Occationally YouTube videos fail to appear, only the sound starts to play, and where the player should be visible there is only a white/grey empty box. This happens with all videos, but only occationally. Reloading the page can fix it -- usually it takes reloading the page four times before the video to properly appear.

**-->> Seems to occur more often if there is a video already playing, and I leave that page in favor of another video. Then that another video is likely to have this problem.**

This may be specific for youtube videos -- Google videos (and other flash videos) occationally fail too, but much less often and not in the entirely same way, so the problems may be unrelated.

**Related info:**
[LIST]
[*]Ubuntu Intrepid 64 bit
[*]Firefox 3.0.4
[*]Using standard flash player, not the beta
[*]Nvidia integrated video and sound card
[*]Intel Dualcore 64-bit system
[/LIST]
Maybe somebody knows what causes this problem?
Thankful for help!

---

### Post by gandaran on 2008-12-16
> **enque said:**
> This thread is about the white-box problem, the freezing is something else and have been discussed in other threads, as well as the sound freezing thing.

I also have this problem, and I've had it since about september/october and have awaited a fix to appear but nobody seems to mention it. I'm sick of it so that's why I'm posting in this thread -- to bump the issue.

**Here is my description:**
Occationally YouTube videos fail to appear, only the sound starts to play, and where the player should be visible there is only a white/grey empty box. This happens with all videos, but only occationally. Reloading the page can fix it -- usually it takes reloading the page four times before the video to properly appear.

**-->> Seems to occur more often if there is a video already playing, and I leave that page in favor of another video. Then that another video is likely to have this problem.**

This may be specific for youtube videos -- Google videos (and other flash videos) occationally fail too, but much less often and not in the entirely same way, so the problems may be unrelated.

**Related info:**
[LIST]
[*]Ubuntu Intrepid 64 bit
[*]Firefox 3.0.4
[*]Using standard flash player, not the beta
[*]Nvidia integrated video and sound card
[*]Intel Dualcore 64-bit system
[/LIST]
Maybe somebody knows what causes this problem?
Thankful for help!
are you still using the the standard 32-bits flashplugin-nonfree from the repos for 64-bits system?
well, everybody is saying the new 64-bits beta adobe flash is wonderful!
try it, remove the flashplugin-nonfree and npwraper and get the beta here
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

---

### Post by SeePU on 2008-12-16
gandarin, what is the best way to remove it?  I have the same issue.  I'm using 8.10 Kubuntu Intrepid 64-bit and I have the grey box where the video should be but I get sound each time.  Not all videos in youtube have the grey box but enough do that it's a problem.

So, uninstall the 32-bit Flash 10 and install the 64-bit alpha Flash 10 for Linux?  It's a tar file, a plug-in, correct?

But, how should one uninstall the Flash 10 (32-bit, I assume) that's already there?  I guess I could go to the repository where it's shown?  Also, I need to uninstall the nsplugin?

---

### Post by gandaran on 2008-12-17
> **SeePU said:**
> gandarin, what is the best way to remove it?  I have the same issue.  I'm using 8.10 Kubuntu Intrepid 64-bit and I have the grey box where the video should be but I get sound each time.  Not all videos in youtube have the grey box but enough do that it's a problem.

So, uninstall the 32-bit Flash 10 and install the 64-bit alpha Flash 10 for Linux?  It's a tar file, a plug-in, correct?

But, how should one uninstall the Flash 10 (32-bit, I assume) that's already there?  I guess I could go to the repository where it's shown?  Also, I need to uninstall the nsplugin?
use synaptic to remove **flashplugin-nonfree** (the adobe flash) just find it mark for complete removal and click the apply button
then download the .tar.gz flash package for 64-bits to desktop, extract the package and just drop the libflashplayer.so file in a browser plugins directory, usually /usr/lib/mozilla/plugins or any firefox plugins folder

---

### Post by goggle5 on 2008-12-17
I was having the same problem with Flash and the grey boxes appearing ... I had the latest version of flash.  After some looking around and installing/uninstalling some of the Flash libraries in synaptic, I found that this package was causing the trouble ... swfdec     (or something like that - I can't get onto my Ubuntu desktop to double check the name - but that's another issue)

I uninstalled it and everything seemed to work after that.

---

### Post by SeePU on 2008-12-17
> **gandaran said:**
> use synaptic to remove **flashplugin-nonfree** (the adobe flash) just find it mark for complete removal and click the apply button
then download the .tar.gz flash package for 64-bits to desktop, extract the package and just drop the libflashplayer.so file in a browser plugins directory, usually /usr/lib/mozilla/plugins or any firefox plugins folder
Thanks!  I did just that and youtube videos seem to be working fine now.  I will assume that fix solved the problem.

google5, if I have any future problem and the grey boxes return, I'll be sure to look into your 'fix.'  Thanks for the idea and info.

---

### Post by Morty007 on 2009-01-25
I'm having the same problem, only with a 32bit system. I have to refresh the page several times for it to work. 

Any suggestions?

---

### Post by rath3r on 2009-01-27
> **tubunu said:**
> Here's what I did to solve a similar problem with flash: 

```
sudo apt-get purge flashplugin-nonfree gnash gnash-common swfdec-mozilla && sudo apt-get install flashplugin-nonfree libflashsupport

```

:)



Flash videos had not been working on firefox 3 in Hardy 8.04(32bit) but this was on another forum. It had been bugging me for ages. but all works now.

Thank tubuntu 

hope this helps as well

---

