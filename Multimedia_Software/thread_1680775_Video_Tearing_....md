---
title: "Video Tearing ..."
date: 2011-02-03
forum: Multimedia Software
---

### Post by airbus001 on 2011-02-03
Hello,

I have been using Ubuntu for two weeks already, and absolutely love it. There is one problem that I have searched for a solution for and found many proposed solutions for but none that work on my system. I have somewhat bad video tearing on all video players: Movieplayer, VLC, Miro Internet, MiniTube, etc. and all different codecs from xvideo to h264. In case you do not know video tearing is where the monitor displays a horizontal line where one frame above is a different frame from the one below(exactly like the picture in the wiki article: [http://en.wikipedia.org/wiki/Screen_tearing](http://en.wikipedia.org/wiki/Screen_tearing) )

First I am running 10.04 AMD64 Desktop LTS version of Ubuntu, as 10.10 was unstable on my system. My hardware configuration is: AMD Phenom X4 9550 @ 2.6 GHz, 4GB OCZ Platinum DDR2 @ 1066 MHz, Asus M3N-HT AM2+ Mobo, 1 TB WD Black Caviar. I already installed the Nvidia Accelerated Graphics Driver with the Nvidia X Server Settings, as I have on board graphics via the nForce 780a chipset on the northbridge. I also have dual monitor set up. 

Solutions I have reviewed are: Turning off Compiz(revertiing to Metacity). This has little to no affect on the video tearing. Second proposed solution was turning on Vsync to Vblank on the Nvidia X Server XVideo Settings, OpenGL, and Compiz. This proposed solution made my computer drop frames like crazy(video very choppy). 

Not sure what else I could do? Do you think buying a decent graphics card would help GTX 460 or better? As my onboard graphics is only 512 MB of DDR2 @ 400 MHz, and the GPU clock is at 400 MHz, with a 128 bit memory interface. As a sidenote: all the videos I am trying to play on Ubuntu play with out any problems on Windows 7, however there is no way I can go back to Win 7.

Thanks for the help,
airbus001

---

### Post by cchhrriiss121212 on 2011-02-03
You shouldn't need a new card, try what is mentioned here:
[http://crunchbanglinux.org/forums/topic/10510/fix-lag-with-hd-video-on-vlc/](http://crunchbanglinux.org/forums/topic/10510/fix-lag-with-hd-video-on-vlc/)

---

### Post by airbus001 on 2011-02-03
Thank You Chris I have now tried everything on that page to no avail. Does anyone have any other suggestions? Please?

---

### Post by Hedgehog1 on 2011-02-03
This is not a solution as much as my experience with my AMD x4 system and the faster 'Evga GeForce GT 430 1 GB DDR3 PCI-Express 2.0 Graphics Card'. 
 
I also get tearing when running full screen video (I use a 55" TV as my monitor via an HDMI cable) from Ubuntu & Windows 7.
 
When I dual boot to Windows 7 and run VLC for the same 720p video files, no tearing.
 
So the my hardware can do the job. Because I can dual boot to watch 'Top Gear' and 'Doctor Who' from the UK, I have not tried to figure it out yet.
 
Mostly I wanted you to be aware that a faster Nvidia video card on an AMD system 'tears' video too.
 
Perhaps some folks with ATI cards in AMD boxes can fill us in - you may be forced to adding a faster ATI card (not a bad thing!).

---

### Post by efball3 on 2011-02-03
> **airbus001 said:**
> Hello,

I have somewhat bad video tearing on all video players: Movieplayer, VLC, Miro Internet, MiniTube, etc. and all different codecs from xvideo to h264. 

I already installed the Nvidia Accelerated Graphics Driver with the Nvidia X Server Settings, as I have on board graphics via the nForce 780a chipset on the northbridge. I also have dual monitor set up. 

Solutions I have reviewed are: Turning off Compiz(revertiing to Metacity). This has little to no affect on the video tearing. Second proposed solution was turning on Vsync to Vblank on the Nvidia X Server XVideo Settings, OpenGL, and Compiz. This proposed solution made my computer drop frames like crazy(video very choppy). 



I tried many many things to fix video tearing (nvidia 9400GT, dual monitors with twinview, Ubuntu 10.04).  I switched from compiz to mutter and that fixed it (mutter --replace).  You also must have vsync set in the nvidia settings (two places, and set to the correct display).

---

### Post by Hedgehog1 on 2011-02-04
> **efball3 said:**
> I tried many many things to fix video tearing (nvidia 9400GT, dual monitors with twinview, Ubuntu 10.04).  I switched from compiz to mutter and that fixed it (mutter --replace).  You also must have vsync set in the nvidia settings (two places, and set to the correct display).

efball3,

I clicked the 'Sync to VBlank' in both the 'XServer xVideo Settings' & 'OpenGL Settings' for Xscreen 0.

I then uninstalled compiz and installed mutter.

Finally I did a "sudo mutter --replace" in the terminal window.

Now my video is playing WITHOUT TEARING!!

Thanks very much!

airbus001 - this did the trick.  Of course, I miss my 'wobbly windows'...  :KS

---

### Post by Hedgehog1 on 2011-02-04
I started fooling with this some more.

I left the 'Sync to VBlank' in both the 'XServer xVideo Settings' & 'OpenGL Settings' for Xscreen 0.

I then uninstalled mutter and reinstalled compiz & ccsm.

The options look different in the System >> Appearance Preferences >> visual effects.  There is not a 4th 'ultimate' option.  But the settings in System >> CompizConfig Settings manager all seem to work.

Here is the thing - I have my wobbly windows back, but the video playback is not tearing.

I did skip the install of three 'default' compiz modules in the synaptic package manager:

* Compiz Fusion option code generator
* OpenGL window and compositing manager - development file
* Compiz window decoration library - development files

I don't know if skipping these solved the tearing when using compiz.

---

### Post by boddhisatva on 2011-02-08
I've had the problem with tearing with compiz for a long time, on two different hardware configurations. I usually just turned off Compiz when watching stuff. But today I found one little option in ccsm - in general options > image settings, I ticked 'synchronize with vsync' (I'm translating from Polish, so these might be called a bit differently in English). And it worked like a charm! Of course, vsync is turned on in nvidia settings, both for texture and opengl.

---

### Post by Feelkarma on 2011-03-26
> **efball3 said:**
> I tried many many things to fix video tearing (nvidia 9400GT, dual monitors with twinview, Ubuntu 10.04).  I switched from compiz to mutter and that fixed it (mutter --replace).  You also must have vsync set in the nvidia settings (two places, and set to the correct display).
Thanks efball3, this was driving me nuts!
Everything was working fine until I installed Cairo Dock, then tearing appeared (which I had about one year ago and had then solved itself after upgrading to 10.10). In my case, even uninstalling compiz didn't do the trick, only after actually installing and activating mutter did it work. So thanks again!

---

### Post by jimmybute on 2011-03-30
OMG - Thank You for this infomation, this has been driving me nuts on my HTPC.

Good Fix!

\\:D/:guitar:\\:D/

---

