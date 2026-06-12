---
title: "Video lag and tear after 11.04 upgrade (compiz problem)"
date: 2011-05-20
forum: Multimedia Software
---

### Post by clytn on 2011-05-20
Hi,
as always when it comes to Linux, doing anything at all often renders the whole system unusable and forces you to spend an eon of time fixing it.

Updating from Ubuntu 10.10 to 11.04 was of course no exception of this rule. Appart from messing up my remote control and introducing the Unity interface, i had to see my video performance get dramatically reduced. All this with a simple click of a button in the update manager.

Well.. On to the problem.

System: Asrock ION 330HT, 500Gb disk and 2Gb of RAM
The system was running extremely well on Ubuntu 10.10 and had no problem whatsoever playing 1080p movies on an LCD HDTV using XBMC. I also used it to play SNES games with SNES9x with little or no lag.

I upgraded the system to 11.04, and immediately noticed that there were lag and some tearing when playing SNES games. When I tried to watch an XviD encoded .avi the framerate was extremely low and there were a lot of tearing.

Since then, i've fiddled around with various settings, but I cant figure out what's wrong.

I've tried:
-Switching to "Ubuntu Classic" session, which improved video performance, but still was far from perfect
-Unchecking "Sync to vblank" in CompisConfig Settings Manager, under OpenGL settings
-Switching every possible setting in XBMC between all possible values
-Re-installing Nvidia drivers (apt-get remove nvidia-current and then apt-get install nvidia-current)

I found that:
-The process "compiz" was using 10% CPU, but I think this is normal when running Unity because I checked this with a friend also running 11.04 on Atom 330 and ION (not asrock)
-Killing compiz will immediately, in one millisecond, fix all problems with video lag and any video starts to run smooth. There's no imagination going on, the movie will just in the blink of an eye start running as smooth as it was before 11.04. Of course, killing compiz will also mess up the XBMC window, the movie frame will shift down and to the right on the screen with no more full screen playback. Basically, I have to restart Xorg to fix my GUI if i kill Compiz.


I know for sure that 11.04, with Unity and Compiz, should run fine on an Asrock ION330HT. My friend has the same specs, and it's doing so on his machine. Also, googling it gives nothing about problems running 11.04 on an Asrock ION330HT.

Please help me out! I've reinstalled this system countless times and it's getting harder and harder to explain to my girlfriend and others why Linux is so neat. So far it's done a great job showing that it sucks.

---

### Post by mc4man on 2011-05-20
I started getting some tear here on 2 different machines (one an AGP 7800 desktop, the other a 8400m laptop
(may have absolutely no effect for you...

So along with the usual setting of vsync wherever possible (one place in ccsm, 2 in nvidia-settings), I did the opposite  of in the past and enabled  'Unredirect Fullscreen Windows' in compiz - screen
(also set refresh rate to double the actual
Whether it matters also disabled the 'workarounds' plugin.

Not getting tearing here anymore (or at least not obviously visible

(if you get stuttering with a cpu(s) that scale and use  ondemand i'd lower the up_theshold from the crappy kernel default of 95
Also one can temp move the nvidia powerize setting to max.

---

### Post by allwise on 2011-05-20
clytn: I've got the exact same problem. In Ubuntu 10 everything worked, but now all has screwed up. The only difference between the configurations is that I got a SSD-drive. 

I managed to get the remote working by following this guide: [http://ubuntuforums.org/showpost.php?p=9293063&postcount=12](http://ubuntuforums.org/showpost.php?p=9293063&postcount=12)

Also XBMC is now starting in windowed mode, and I have to mouse click it to enable it. A bit frustrating when I only have the remote connected to the computer.

Anyways, do someone have a solution/suggestion for this compiz problem?

---

### Post by Mr. Shannon on 2011-05-20
In 10.10 I had to disable desktop effects in order to watch HD video without tearing.  In 11.04 there are 2 Ubuntu classic sessions, try the one without effects.  I think this will give you the old interface without Compiz.  If that works and you want Unity then you could try Unity 2D.  See this link for instructions: [http://www.addictivetips.com/ubuntu-linux-tips/how-to-get-ubuntu-2d-unity-desktop/]("http://www.addictivetips.com/ubuntu-linux-tips/how-to-get-ubuntu-2d-unity-desktop/")

---

### Post by clytn on 2011-05-21
> **mc4man said:**
> I started getting some tear here on 2 different machines (one an AGP 7800 desktop, the other a 8400m laptop
(may have absolutely no effect for you...

So along with the usual setting of vsync wherever possible (one place in ccsm, 2 in nvidia-settings), I did the opposite  of in the past and enabled  'Unredirect Fullscreen Windows' in compiz - screen
(also set refresh rate to double the actual
Whether it matters also disabled the 'workarounds' plugin.

Not getting tearing here anymore (or at least not obviously visible

(if you get stuttering with a cpu(s) that scale and use  ondemand i'd lower the up_theshold from the crappy kernel default of 95
Also one can temp move the nvidia powerize setting to max.


Thank you, I will test all of this when my girlfriend is finished watching Desperate Housewives with tearing and lag :P

I don't know about that cpu scaling, as far as I know, it's my GPU that is doing all the scaling and video processing.

//Clayton

---

### Post by clytn on 2011-05-21
> **allwise said:**
> clytn: I've got the exact same problem. In Ubuntu 10 everything worked, but now all has screwed up. The only difference between the configurations is that I got a SSD-drive. 

I managed to get the remote working by following this guide: [http://ubuntuforums.org/showpost.php?p=9293063&postcount=12](http://ubuntuforums.org/showpost.php?p=9293063&postcount=12)

Also XBMC is now starting in windowed mode, and I have to mouse click it to enable it. A bit frustrating when I only have the remote connected to the computer.

Anyways, do someone have a solution/suggestion for this compiz problem?


Hi, nice to hear that i'm not alone. That is, if we have the same cause of our problems. Are you on an Asrock ION330 system? Did you upgrade or fresh install 11.04?

---

### Post by clytn on 2011-05-21
> **Mr. Shannon said:**
> In 10.10 I had to disable desktop effects in order to watch HD video without tearing.  In 11.04 there are 2 Ubuntu classic sessions, try the one without effects.  I think this will give you the old interface without Compiz.  If that works and you want Unity then you could try Unity 2D.  See this link for instructions: [http://www.addictivetips.com/ubuntu-linux-tips/how-to-get-ubuntu-2d-unity-desktop/](http://www.addictivetips.com/ubuntu-linux-tips/how-to-get-ubuntu-2d-unity-desktop/)


Thank you for the suggestion. I tried switching to Ubuntu Classic and Ubuntu Classic without effects, but apart from increasing the video FPS, it didn't fix the problem.

In 10.10, I could run all the desktop effects I wanted and still get smooth video playback. I don't want to disable stuff just because the quality of Ubuntu 11.04 is sub-par. Also, I know that it should be possible to run Unity and Compiz on 11.04 with video playback being smooth.

What I want is a solution to the problem. I have a pretty good suspect in compiz, since my video playback is perfect immediately after killing the compiz process. That should be enough to get some smart guy to say that "well compiz does this and this, if that happens you should do this and this and all will be well".

---

### Post by Nitros on 2011-05-21
Hello clytn,

I think I am having the same problem you have. My computer is an Acer Aspire R3610, with Nvidia ION chipset and Intel Atom 330 CPU.

While I had previous versions of Ubuntu 11.04, I had no problem at all with video playback in any of its forms, I was even able to play fullHD video smoothly. However, since I've installed Ubuntu 11.04 playing video has become a very unpleasant experience, as I suffer from random video lag.

This random lag appears on Totem and GNOME Mplayer, as well as with youtube and other flash browser players. Whilst audio keeps running ok, video gets laggy and it gets solved after a while, then no more lag.

Strangely, with VLC happens exactly the opposite, video playback is always smooth but audio starts doing different noises until it becomes impossible to understand a word, as with the other case, this problems gets solved after I've been playing video for a while.

I've not noticed that any program was fully using my CPU, but I'll try to kill compiz as you suggested when that happens again in order to see if that solves my problem as well.

I've tried everything you mention too with no luck, I've also set GNOME Mplayer video output to vdpau and looks like I get a little improvement (video is only laggy for a minute or so and then it is ok), but still it is unpleasant to watch youtube videos.

Hope we can find a solution for this problem soon.

---

### Post by clytn on 2011-05-21
> **Nitros said:**
> Hello clytn,

I think I am having the same problem you have. My computer is an Acer Aspire R3610, with Nvidia ION chipset and Intel Atom 330 CPU.

While I had previous versions of Ubuntu 11.04, I had no problem at all with video playback in any of its forms, I was even able to play fullHD video smoothly. However, since I've installed Ubuntu 11.04 playing video has become a very unpleasant experience, as I suffer from random video lag.

This random lag appears on Totem and GNOME Mplayer, as well as with youtube and other flash browser players. Whilst audio keeps running ok, video gets laggy and it gets solved after a while, then no more lag.

Strangely, with VLC happens exactly the opposite, video playback is always smooth but audio starts doing different noises until it becomes impossible to understand a word, as with the other case, this problems gets solved after I've been playing video for a while.

I've not noticed that any program was fully using my CPU, but I'll try to kill compiz as you suggested when that happens again in order to see if that solves my problem as well.

I've tried everything you mention too with no luck, I've also set GNOME Mplayer video output to vdpau and looks like I get a little improvement (video is only laggy for a minute or so and then it is ok), but still it is unpleasant to watch youtube videos.

Hope we can find a solution for this problem soon.


Thank you for your comments. It seems as our problems are a little different, because my video never runs smooth.

I also played around with vdpau settings and also notice an improvement of FPS, but it's far from acceptable.

---

### Post by allwise on 2011-05-21
> **clytn said:**
> Hi, nice to hear that i'm not alone. That is, if we have the same cause of our problems. Are you on an Asrock ION330 system? Did you upgrade or fresh install 11.04?

I've got an Asus AT3IONT-I Deluxe Atom 330 and did an upgrade from 10.10.

---

### Post by allwise on 2011-05-21
Whoa!! I got it to work, but unfortunatly I'm not 100% sure what did it. In the settings I went to the Unity plugin settings and chose the dock to auto hide. I also installed Unity 2D from this guide: 

[http://www.addictivetips.com/ubuntu-linux-tips/how-to-get-ubuntu-2d-unity-desktop/](http://www.addictivetips.com/ubuntu-linux-tips/how-to-get-ubuntu-2d-unity-desktop/)


```
sudo add-apt-repository ppa:unity-2d-team/unity-2d-daily
sudo apt-get update

sudo apt-get install unity-2d
```

In the last bit of the guide you're supposed to logout and select Unity 2D and then login again. But I didn't find that setting, so I just logged in as normal. And then both Xbmc started in fullscreen and the lags was gone! 

So try that and see if it help you!

//Allwise

---

### Post by clytn on 2011-05-21
Tried Unity 2D, but it didn't work... thanks for the advice though.

I did find a fix, but not a solution nor the cause of the problem. I am very dissatisfied but still happy to have a working media center again.

This is what i did:
```
sudo apt-get remove compiz
find compiz
rm -rf <path/to/compiz>
```I deleted everything related to compiz. I just thought f**k it!

After that, I rebooted the system and logged in using Ubuntu Classic.

XBMC will show videos smooth again.


Once again, Linux fails to deliver. Time after time it is proven that Windows is far supperior when it comes to "just working". Compatibility, user friendliness, media support, graphics, drivers, everything that the average user wants is a lot better on Windows. Until the Linux community understands that, Linux will NEVER replace windows. Just because you like to spend 16hrs getting video playback to work after upgrading your system it doen't mean that it's the way it should be. ******* crap if you ask me. But still, it rocks on other stuff, and that's why I need it.

If anyone knows of a way to troubleshoot my compiz problem, please let me know. I'd really like to know why it faild so miserably.

---

### Post by clytn on 2011-05-21
****!!!!
Of course that **** didn't work, because compiz is the window manager and now I don't have any windows. **** LINUX!

Please help me out. Is the only fix to re-install the whole ******* system?

---

### Post by clytn on 2011-05-21
Ok, some new details..

If I launch:
```
metacity --replace
```
I will get windows, but then video performance sucks similar to what I had with compiz. I will get extreme tearing in videos, but FPS seems to be ok.

//Clayton

---

### Post by Nitros on 2011-05-22
As far as I know, if you start session as "Ubuntu Classic (Without effects)", the window manager will be metacity and not compiz, so uninstalling compiz shouldn't be necessary.

---

### Post by clytn on 2011-05-22
> **Nitros said:**
> As far as I know, if you start session as "Ubuntu Classic (Without effects)", the window manager will be metacity and not compiz, so uninstalling compiz shouldn't be necessary.


Good point, because I noticed that the tearing was about the same with Ubuntu Classic as it was when I did "metacity --replace", so that seems to be true.

---

### Post by FYFI13 on 2011-05-31
Similar problem here. If i enable Compiz effects (i`m using Ubuntu Classic) i can`t even drag a window to other side of screen. I tried to disable VSYNC in CSSM, set proper screen refresh rate, but nothing helped. After disabling Compiz i have 0 lag, can play Nexuiz and so on, but then i get very bad video tearing... Also i`ve tried all possible video drivers, but problem persisted.
Switched back to Ubuntu 10.10 (64 bit) where everything works just great.
AMD Phenom II 965, Nvidia GTX 560Ti.

---

### Post by clytn on 2011-06-01
> **FYFI13 said:**
> Similar problem here. If i enable Compiz effects (i`m using Ubuntu Classic) i can`t even drag a window to other side of screen. I tried to disable VSYNC in CSSM, set proper screen refresh rate, but nothing helped. After disabling Compiz i have 0 lag, can play Nexuiz and so on, but then i get very bad video tearing... Also i`ve tried all possible video drivers, but problem persisted.
Switched back to Ubuntu 10.10 (64 bit) where everything works just great.
AMD Phenom II 965, Nvidia GTX 560Ti.


Thank you. Not much action in this thread though. I don't think this will ever get fixed, so we're stuck in 10.10.

---

### Post by alexfpms on 2011-06-04
Hi,

I've made a fresh install of ubuntu 11.04 and now i have the laggy compiz. The strange thing is if i turn on compiz Benchmark my cpu goes up to 80%. Everything was perfect with 10.10 and now it goes me crazy :(

[http://imageshack.us/photo/my-images/560/tempsk.jpg/](http://imageshack.us/photo/my-images/560/tempsk.jpg/)

---

### Post by 7wonders on 2011-06-07
I had problems also on ion 330 after downgrading to 11.04 but I have now got it to a bearable tiny bit of tear here and there. First go in and change the software sources to allow proposed packages and the run an apt-get update and apt-get upgrade. This will give you a more recent version of lots of stuff including kernel that works with LG tv's (this is how I ended up here!). You will have to make the usual alsa changes to get sound through hdmi working (install gnome alsa and check the iec98 box, unmute everything through alsamixer etc etc). Turn on gpu scaling in nvidia config settings, go into login screen settings and choose ubuntu classic (without effects). Turn on vdpau in xbmc and you should be good to go :)

---

### Post by fnandocc on 2011-06-11
Remember to turn off composite in X

[http://www.mythtv.org/wiki/VDPAU#Disabling_the_Composite_Extension](http://www.mythtv.org/wiki/VDPAU#Disabling_the_Composite_Extension)

---

### Post by danger89 on 2012-01-22
Xorg and/or Compiz seems to have a CPU bug, causes huge speaks...
Check: [https://bugs.launchpad.net/unity/+bug/803943](https://bugs.launchpad.net/unity/+bug/803943)


However if you use Intel HD & you're using Unity try:
[http://ubuntuforums.org/showpost.php?p=11508824&postcount=36](http://ubuntuforums.org/showpost.php?p=11508824&postcount=36)

---

