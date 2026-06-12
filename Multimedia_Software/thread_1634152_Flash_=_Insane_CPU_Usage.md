---
title: "Flash = Insane CPU Usage"
date: 2010-11-30
forum: Multimedia Software
---

### Post by Alexskot on 2010-11-30
Hi all!

[COLOR=#000000]I have a problem with my computer. Ubuntu 10.10 64 bit is installed on the pc. Although my system has an AMD Phenom II X4 965 Processor and an ati 4850 hd graphics card, it is very unresponsible in everyday tasks. [/COLOR]I know that both open-source and [COLOR=#000000]proprietary drivers suck on linux. [/COLOR][COLOR=#000000]I have installed fglrx but it didn't get any better, far from that. Due to the known incompatibilities of the fglrx driver with the new xorg version, now resolution of plymouth is very low. I knew that if I installed fglrx, plymouth wouldn't work but I was hoping that system will be more responsive. Well, when I watch hd videos on youtube, the process plugin-container uses 100% of my monster cpu. I can't believe how it uses all the processing power of a phenom II x4 and videos are usually played at 15 fps. I understand that sytem isn't able to utilize the graphics card but is it normal such a high processor usage?
[/COLOR]

---

### Post by runeh76 on 2010-11-30
Yeah ATI sucks in ubuntu.. Nvidia works like a charm. Try lowest settings on ur graphic card when u try videos next time. U find earlier threads about flash problems.

---

### Post by Grenage on 2010-11-30
> **Alexskot said:**
> Hi all!

[COLOR=#000000]I have a problem with my computer. Ubuntu 10.10 64 bit is installed on the pc. Although my system has an AMD Phenom II X4 965 Processor and an ati 4850 hd graphics card, it is very unresponsible in everyday tasks. [/COLOR]I know that both open-source and [COLOR=#000000]proprietary drivers suck on linux. [/COLOR][COLOR=#000000]I have installed fglrx but it didn't get any better, far from that. Due to the known incompatibilities of the fglrx driver with the new xorg version, now resolution of plymouth is very low. I knew that if I installed fglrx, plymouth wouldn't work but I was hoping that system will be more responsive. Well, when I watch hd videos on youtube, the process plugin-container uses 100% of my monster cpu. I can't believe how it uses all the processing power of a phenom II x4 and videos are usually played at 15 fps. I understand that sytem isn't able to utilize the graphics card but is it normal such a high processor usage?
[/COLOR]

Flash is a a horrible CPU hog, and the problem is compounded by ATI/AMD graphical drivers.  I got much better performance from on-board Intel or Nvidia drivers, but I've not seen it perform as poorly as you describe.

If you can get a cheap second-hand Nvidia card, you'll likely save yourself a lot of hassle.

---

### Post by Adune on 2010-11-30
> **Grenage said:**
> Flash is a a horrible CPU hog, and the problem is compounded by ATI/AMD graphical drivers.  I got much better performance from on-board Intel or Nvidia drivers, but I've not seen it perform as poorly as you describe.

If you can get a cheap second-hand Nvidia card, you'll likely save yourself a lot of hassle.

Indeed.. Also there is no hardware acceleration supported in Flash on Linux yet. I use nVidia and I can't even watch some Flash videos in fullscreen without dropping frames, Youtube and Hulu work fine though. Just a minor setback that we just have to deal with for now. Hopefully Adobe decides to add hardware acceleration support for Flash on Linux sometime in the near future.

---

### Post by Alexskot on 2010-12-01
I unistalled the alpha version of flash player 64 and now I use the 32 bit version of flash player with nsplugginwrapper. To my complete surprise process npviewer.bin uses "only" 72% of cpu processing power. If I buy an nvidia card and install the nvidia proprietary drivers, can I expect an 8% cpu load as it was in windows 7? I'm thinking of going back to windows but I'll miss many things such as bash, emacs, metasploit, ffmpeg and the list goes on. It's just feel right to run emacs and apache on linux. But it's a shame that I can't do simple tasks such as watching a video on youtube. But it's not only browsing that is sluggish. I feel that the whole system is sluggish mailny beacause of the problems with the graphics card driver. Has amd any plan to actually support linux in the near future?

---

### Post by cchhrriiss121212 on 2010-12-01
If your whole system is sluggish it might be more than your graphics driver causing the problem. On that cpu flash should not take up so much %.
> If I buy an nvidia card and install the nvidia proprietary drivers, can I expect an 8% cpu load as it was in windows 7?
Maybe, but it will likely be a bit higher than that. To compare, I have an Athlon II 245, and a 9600GT, regular flash will take up around 10% of both cores, 1080p flash will be around 80% (it does play perfectly though). This is on a 64bit OS with a 64bit plugin, which is much better than the 32 on my system.

Before swapping hardware, you should look at this for flash on youtube and a few other sites, it will greatly improve your performance:
[https://addons.mozilla.org/en-US/firefox/addon/161869/](https://addons.mozilla.org/en-US/firefox/addon/161869/)

---

### Post by Grenage on 2010-12-01
> **Alexskot said:**
> If I buy an nvidia card and install the nvidia proprietary drivers, can I expect an 8% cpu load as it was in windows 7?

No, because Adobe don't support hardware acceleration on Linux; in this instance, Adobe flash player is your main problem.

---

### Post by soldier1st on 2010-12-01
flash is horrible even on ubuntu 10.04 but it's not linux's fault but adobes inconpetence and unwillingness to fix the issue drives alot of linux users away.

---

### Post by cchhrriiss121212 on 2010-12-01
> **Grenage said:**
> No, because Adobe don't support hardware acceleration on Linux
Flash does have hardware acceleration, it's just that other factors make it ineffective. Someone posted an article about it a while back but I can't seem to find it.

---

### Post by Grenage on 2010-12-01
> **cchhrriiss121212 said:**
> Flash does have hardware acceleration, it's just that other factors make it ineffective. Someone posted an article about it a while back but I can't seem to find it.

You would appear to be correct:
```

As reported on Adobe's Linux blog in May 2008, Flash 10 has native 3D hardware acceleration,
   except due to driver bugs they blacklisted anything with a client glx vendor string of SGI.  Unfortunately, Intel
   seems to report "SGI" here.  I was told that mms.cfg option "OverrideGPUValidation = 1" will override their blacklist.
   Adobe wrote this new blog entry about this.
   See the Adobe Flash Player Administration Guide to learn how to use /etc/adobe/mms.cfg.
```

---

### Post by Yellow Pasque on 2010-12-01
You can workaround the Flash issue on popular sites like youtube using FlashAid to replace the Flash player with a native Linux plugin. It's the best way to deal with Flash IMO. I think Adobe has effectively abandoned Linux GPU acceleration: [http://blogs.adobe.com/penguinswf/2010/01/solving_different_problems.html](http://blogs.adobe.com/penguinswf/2010/01/solving_different_problems.html).

---

### Post by Grenage on 2010-12-01
> However, the internet at large has unanimously declared that it appreciates the Flash Player&#8217;s solution to the video problem.

Lol.

---

### Post by a-user on 2010-12-01
flash for linux currently still sucks. it consumes far more cpu usage than the windows version uner same cirumstances. but at least it is working. luckaly i don't use it too much. for the one or other youtube video it is enough.

edit: i doubt adobe will get things done in near future.

---

### Post by TBABill on 2010-12-01
+1 for installing Flash-Aid. It'll swap out 32 bit Adobe Flash for 64 bit and keep you running the most up to date version at all times. In addition, right click a video while playing and uncheck "enable hardware acceleration" and see if that helps. Doing both should make a difference.

---

### Post by beew on 2010-12-01
> **Temüjin said:**
> You can workaround the Flash issue on popular sites like youtube using FlashAid to replace the Flash player with a native Linux plugin. It's the best way to deal with Flash IMO. I think Adobe has effectively abandoned Linux GPU acceleration: [http://blogs.adobe.com/penguinswf/2010/01/solving_different_problems.html](http://blogs.adobe.com/penguinswf/2010/01/solving_different_problems.html).

You mean the flashvideoreplacer. :) Works like a charm for my 32bit computers but I am not sure if it works for 64 bits though, probably does too.

---

### Post by mc4man on 2010-12-01
You can also, if inclined, enter any youtube url, sd or hd into vlc and it'll playback fine with reduced cpu usage. (about 20 -25% w/ fullscreen 720p here
 - you cannot use vlc's record button on hd vid's (well you can but you'll only get the audio.

---

### Post by hawthornso23 on 2010-12-01
Flash is hopefully soon to die. The future is HTML5.

You can try out the future now. Install chrome or another browser that supports HTML5 (like firefox 4.0 beta), go to [http://www.youtube.com/html5](http://www.youtube.com/html5)
and sign up up for their HTML5 trial.

---

