---
title: "Flash video cripples CPU"
date: 2010-08-30
forum: Multimedia Software
---

### Post by tripmix on 2010-08-30
Opening any flash video with the flash player plugin cause my CPU to go to 100% (even more but I assume that's just top reporting dual core or something). I've googled around and others seem to have this issue but no fix as far as I can tell. I want to watch youtube and stuff without burning up my CPU so I need to fix this.
A simple "locate -i *flash*.so" gives this:

```
/usr/lib/firefox/plugins/flashplugin-alternative.so
/usr/lib/flashplugin-installer/libflashplayer.so
/usr/lib/iceape/plugins/flashplugin-alternative.so
/usr/lib/iceweasel/plugins/flashplugin-alternative.so
/usr/lib/kde4/kipiplugin_flashexport.so
/usr/lib/libvisual-0.4/morph/morph_flash.so
/usr/lib/midbrowser/plugins/flashplugin-alternative.so
/usr/lib/mozilla/plugins/flashplugin-alternative.so
/usr/lib/openoffice/basis3.2/program/libflashli.so
/usr/lib/xulrunner/plugins/flashplugin-alternative.so
/usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so
/usr/share/ubufox/plugins/libflashplayer.so
```

Although I did install the package flashplugin-nonfree, inn debian that I'm a little more used to flashplugin-nonfree provided libflashplayer.so and not flashplugin-alternative.so which seem to be the one all my browsers are using. However about:plugins in firefox says very little except "application/x-shockwave-flash 	Shockwave Flash"

Can I just replace all the flashplugin-alternative.so with libflashplayer.so and maybe make some links or something or would that be bad?

The process using my CPU is reported as plugin-containe but it only happens with flash video and not any other plugins. If the video is playing, paused or stopped/not started makes no difference.

EDIT: I did replace all the flashplugin-alternative.so with libflashplayer.so, it didn't help. Seems firefox was using that plugin all along, presumably from here "/usr/share/ubufox/plugins/". I can't imagine I'm the only one who wants a fix for this here, there should be hordes. I use the latest kbuntu, flash player, firefox and kernel all from the repo.

---

### Post by snowpine on 2010-08-30
A good first step is to compare your hardware against the Adobe Flash system requirements: 

[http://www.adobe.ca/products/flashplayer/systemreqs/](http://www.adobe.ca/products/flashplayer/systemreqs/)

As you'll see, if you want to play 720 or 1080p, you'll need quite a fast system!

A good workaround is to download the video to your hard drive, rather than watch it streaming from the web. There are numerous Youtube downloaders out there, or you can try an app called Minitube.

---

### Post by tripmix on 2010-08-30
Thats not an issue, I have a very fast system. And if you read my post you would have noticed this happens even when no movie is playing. Starting the plugin is enough. Also I've now tried google chrome from a suggestion in this post   [http://ubuntuforums.org/showthread.php?p=9578244](http://ubuntuforums.org/showthread.php?p=9578244)  with the same results.

EDIT: I'm gonna try and get the plugin from adobe and see if that helps.

---

### Post by snowpine on 2010-08-30
I did read your post :); did you read mine? Does CPU usage improve when you use Minitube or download the video to your hard drive?

The Adobe Flash player is what's called "proprietary" or "non-free" software. It is not distributed as a default part of Ubuntu, and because it is not "open source" there is really nothing Canonical/Ubuntu can do to improve it. :(

---

### Post by wojox on 2010-08-30
Have you had a look at lovinglinux's page [Firefox Tutorials]("http://firefox-tutorials.blogspot.com/") 

If your using Ubuntu & Firefox, this is the place to look.

---

### Post by tripmix on 2010-08-30
Yes the CPU improves, in fact is at less than 10% but then I'm not using the flash player am I so it's besides the point. What you are suggesting implies I have to hunt down the flv url in the html source of every video using flash player and that is not a workaround I can live with. Thanks for trying to help and all but this to much work to be a solution nor is a firefox problem so I doubt that link will help but I'll have a look anyway.

EDIT: And yes, I know it's closed source. You might notice I've been a member on this forum since 2006. Just because ubuntu can't change it don't mean that people can't find a fix, like a downgrade or if it's in conflict with something or whatever. Usually in linux there is always a fix even when dealing with closed source.

EDIT2: Flash plugin from adobe and firefox4.0 tested with same results.

---

### Post by ajgreeny on 2010-08-30
> **tripmix said:**
> Yes the CPU improves, in fact is at less than 10% but then I'm not using the flash player am I so it's besides the point. What you are suggesting implies I have to hunt down the flv url in the html source of every video using flash player and that is not a workaround I can live with. Thanks for trying to help and all but this to much work to be a solution nor is a firefox problem so I doubt that link will help but I'll have a look anyway.
I think it is you who misunderstood the comments about "download the video to your hard drive".  This does not mean you have to have the flash plugin running, because you download the flash as a separate activity, and can even close firefox, but not the firefox download window, once the download has started.

Have a look at the add-on DownloadHelper.  It is so simple to use, you'll wonder why you did not install it before.  There is certainly no need to "hunt down the flv url in the html source of every video" as the add-on finds the flv for you.

The combination of Flashblock and DownloadHelper is brilliant.

---

### Post by tripmix on 2010-08-30
Whats to misunderstand by Download the video? If the flash plugin was running my cpu would be at 100% not 10%, please read before you type. I have used DownloadHelper before, it does not find the flv url for all sites and they are constantly changed in order to prevent such plugins from finding the flv url. Trust me I know, I've written python scrips that does just that myself.

---

### Post by no2498 on 2010-08-30
this may or may not help
i installed grease monkey for fire fox

then i set my plugin 

5.1.&#8195;The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
      This means, that your cpu is doing all the work. Change it to "xvimagesink"
      ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and change the appropriate settings.
    


hope it helps you

---

### Post by tripmix on 2010-08-30
Thanks for the constructive help (at last) :)  Unfortunately that was not it, I kinda suspected as my videos play fine and the issue is really only the players CPU usage. Even when video is not playing or loading for that matter it's 90-100% and the fan starts and everything, I'm really just worried about my CPU burning and the noise is annoying. Otherwise it's perfectly usable, video and sound plays with no issues and no increase in CPU. Opening several pages with players however cause my system to lag but video still plays fine when it eventually starts.

EDIT: I know this might be a bit extreme but I'm gonna try and make a debian chroot and install firefox and flash there, if that don't help it might be a kernel conflict in which case I'll downgrade the kernel or build a new one from the latest source.

---

### Post by no2498 on 2010-08-30
install opera
fire fox uses its files for flash

jump back an forth between the 2 a few times

im down to like 12 % cpu with flash running 1 core

---

### Post by snowpine on 2010-08-30
> **tripmix said:**
> Yes the CPU improves, in fact is at less than 10% but then I'm not using the flash player am I so it's besides the point. What you are suggesting implies I have to hunt down the flv url in the html source of every video using flash player and that is not a workaround I can live with.

Actually it is impossible to watch a video without downloading it to your computer; check your /tmp folder! All I am suggesting is watching that file using your favorite media player (totem, vlc, etc) or Minitube, instead of streaming through Firefox. 

It sounds like my suggestion improved your CPU use from 100% to 10%; sorry if those are not numbers you can live with, but there are some other good  suggestions you can try from the other posters. :)

---

### Post by Yellow Pasque on 2010-08-30
> Even when video is not playing or loading for that matter it's 90-100% and the fan starts and everything
Then you have more issues than Flash. Run htop to find out what's consuming the CPU.

---

### Post by tripmix on 2010-08-31
No offense, but what is you peoples problem? I know what the issue is. Stop talking unless you got something to useful to say, explaining things to you guys is like talking to a rock or worse a windows user. No, I do not have other problems than flash flv player, you seriously think I haven't traced the proses? I've already tried other browsers like I stated before. And stop being all persistent about that useless "download to hard drive" tip, like I don't know how to scrape a site and download whatever I want. Your acting like you have to explain what the word "download" means which means you are a noob, so don't get all pissy about me not taking your advice.

Problem in words you might understand: If I open a page with a flash flv player (not shockwave flash swf player) and forget to close my browser before I leave my computer will catch fire. Therefore the playing of the video is irrelevant to my issue.

What libflashplayer.so is doing when opening a flash flv player is anyones guess but since nobody else here seem to be having this issue it's probably conflicting with something else on my box like a hardware module. Or something else in ubuntu might be acting strange on my setup conflicting with what libflashplayer.so is trying to do causing the issue.

I'm gonna stop following this post now before I get angry and just debug this myself, I'll post the solution when I figure it out just in case someone comes looking in the future but that will be the end of this useless thread.

---

### Post by snowpine on 2010-08-31
> **tripmix said:**
> No offense, but what is you peoples problem? I know what the issue is. Stop talking unless you got something to useful to say, explaining things to you guys is like talking to a rock or worse a windows user.

I suggest redirecting your frustration towards Adobe for shipping a [buggy]("http://www.pcworld.com/businesscenter/article/198095/protect_your_pcs_against_adobe_security_flaws.html"), closed-source codec, not the friendly volunteers of Ubuntu Forums. We have a nice friendly community here, and we do our best to help... I think you got some good answers, but if you are not satisfied with the level of tech support you're getting here **for free** then Canonical has paid support options available. :)

[http://www.ubuntu.com/support/services](http://www.ubuntu.com/support/services)

---

### Post by Yellow Pasque on 2010-08-31
> If I open a page with a flash flv player (not shockwave flash swf player) and forget to close my browser before I leave my computer will catch fire. Therefore the playing of the video is irrelevant to my issue.

Oh. That's a significantly different situation than, "My computer uses 90-100% CPU even when there's no Flash video." Articulate better next time or don't get frustrated when asked for clarification by people trying to assist you.

---

### Post by no2498 on 2010-08-31
i did have the same issue
but im over it now

---

### Post by tripmix on 2010-08-31
It appears the conflict is somewhere between flash, nvidia and the kernel. Downgrading to kernel 2.6.31 from 2.6.32 fixes the problem but is not a good solution. Upgrading to the latest drivers from nvidia (not the ubuntu repo) is a better solution, although the problem doesn't completely go away it's a considerable improvement. With the new module I can now run 5 players simultaneously with about 85% cpu usage. I'll try building a 2.6.36 kernel later and post the results. For now I'll consider this solved, at least for me. I use GeForce 9600M GT on a HP HDX 16.

Sorry if I was a little harsh on you guys earlier, I know you where just trying to help.

---

