---
title: "Screen Flashes black before video play back with VLC (ATi)"
date: 2010-08-02
forum: Multimedia Software
---

### Post by 0004tom on 2010-08-02
I'm experiencing a sudden black flash before video play back with VLC. The whole 3 screens just flash black and come back, and then the video plays fine in VLC. This doesn't happen with other media players, such as mPlayer and Totem. 

I'm running an XFX Radeon 5450 (ATi) with the propriety 10.7 drivers. Running 3 17" (1280x1024) in "EyeFinity". I've had a look on the unofficial bug thingy for ati drivers for linux, and there is a bug back from 2008.

[http://ati.cchtml.com/show_bug.cgi?id=855](http://ati.cchtml.com/show_bug.cgi?id=855)

Here's a quick video I just made showing what happens. Uploaded to youtube.

[http://www.youtube.com/watch?v=LzDtcJtgeS0](http://www.youtube.com/watch?v=LzDtcJtgeS0)

Just wondering if anyone has any ideas, of tips to start looking to try and solve my little issue, I've spent hours and hours looking though xorg, syslog and other logs in /var/log/ and nothing seems to stand out.

---

### Post by 0004tom on 2010-08-06
Information on how to fix this issue can be found [here]("http://phoronix.com/forums/showthread.php?p=141005")

[QUOTE=Forbidden]I had/have the same issue. One important thing I noticed: It would only occur on DisplayPort connected screens, not DVI connected screens. (I even converted one from DisplayPort to DVI to confirm this)

This was happening to me with Ubuntu 9.10, so I tried upgrading to 10.4, still happened.

However, about an hour ago, I just installed a new set of libraries/binaries of VLC and Gstreamer. It's the "Cutting Edge Multimedia" PPA, which includes v1.2 and hardware acceleration and all that. Oddly enough, it stopped the screen-blanking-when-video-starts when starting both VLC and GStreamer videos, but not when starting up MPlayer or Xine.

[https://edge.launchpad.net/~nvidia-v...dge-multimedia](https://edge.launchpad.net/~nvidia-v...dge-multimedia)

(It mentions nvidia in the url there, but it's also for ATI.)[/QUOTE]

Upgrading the VLC binarys with the ones from this PPA I nolonger get the screen flash before video playback.

---

### Post by kotnik on 2010-08-14
This isn't solved.

I'm having exact same issue (my first ATI card, bummer), and using VLC from some obscure repo is far from solution.

Please, if you find any more info, let us know. I'll do the same.

---

### Post by kotnik on 2010-08-14
Just solved my problem. And the solution was pretty dumb. I opened SMplayer, went to Options->Preferences->Video and selected "xv (0 - ATI Radeon AVIVO Video)" {whatever that means}, and now video plays without blanking.

---

### Post by 0004tom on 2010-08-16
Thanks for the feedback and suggestions kotnik, however your method doesn't work for me, and the VLC binarys in that PPA brake more things then they do fix, so I've unmarked the thread as solved.

---

### Post by kotnik on 2010-08-17
But it should be noted that I use mplayer from that repo you provided, and it does have ATI video output that does not blank screen.

---

### Post by 0004tom on 2010-08-24
I tired the softwares from that PPA again, and they work no flash before playback, however I use VLC for one reason, to play from RARs and with the binarys from this PPA this feature of VLC is broken. 

Thought'd I'd give it a senseless bump and attach my xorg.conf too.

```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "off"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "0-DFP1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1280x1024"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "1280 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "0-CRT1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1280x1024"
	Option	    "TargetRefresh" "75"
	Option	    "Position" "2560 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "0-CRT2"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1280x1024"
	Option	    "TargetRefresh" "75"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "Monitor-DFP1" "0-DFP1"
	Option	    "Monitor-CRT1" "0-CRT1"
	Option	    "Monitor-CRT2" "0-CRT2"
	BusID       "PCI:5:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Virtual   3840 1280
		Depth     24
	EndSubSection
EndSection

```

Perhaps someone will see it, and have some more ideas.. I was under the impression everything you do on a linux system gets logged even things you don't do. However this flash doesn't?

The 10.8 drivers are also out tomorrow, so I'm eager to try them :(

---

### Post by imbjr on 2010-08-24
See if anything here helps:

[http://ubuntuforums.org/showthread.php?t=1470082](http://ubuntuforums.org/showthread.php?t=1470082)

---

### Post by kotnik on 2010-08-25
> **0004tom said:**
> Thanks for the feedback and suggestions kotnik, however your method doesn't work for me, and the VLC binarys in that PPA brake more things then they do fix, so I've unmarked the thread as solved.

Well, it stopped working for me too :(  I didn't touch a thing, and screen started blanking all of a sudden.

Gotta get to the bottom of this...

---

### Post by kotnik on 2010-08-25
0004Tom, did you check that setting our friend imbjr dug up in #8?

---

### Post by 0004tom on 2010-08-27
Yep, but sadly nothing helped. I was excited about the radeon.modest=0 posts thinking this could have solved it. But no joy. 

I tried updating the drivers yesterday to 10.8 just wouldn't update. I'd run the 10.8 installer, and after the reboot i'd check the amdccle and it would say I was running 10.7 still. I'm going to the extreme tonight sometime and installing a fresh lucid and use the 10.8 driver.

Hopefully this will stop this.

---

### Post by no2498 on 2010-08-27
this may help for the ati 

write down your settings first so you can set them back if needed



this comes from the program cheese help file faq's



5.1.&#8195;The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
      This means, that your cpu is doing all the work. Change it to "xvimagesink"
      ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and change the appropriate settings.

---

### Post by 0004tom on 2010-08-28
Thanks for the suggestion no2498, sadly this also didn't help :(

Any more ideas?

So I did a clean install yesterday and test this playback issue before I installed the ATi drivers. Using the "opensource" Radeon driver the flash before playback doesn't exist. Install the proprietary driver and you get your flash back, this was using the 10.8 driver too.

I get the feeling ATi are more bothered introducing new features for the drivers then they are investigating and solving existing problems.

---

### Post by kotnik on 2010-08-28
I'll try 10.8 drivers as well.

---

### Post by kotnik on 2010-08-28
Just installed Catalyst 10.8 and nothing changed regarding screen flashing problem.

Tom, if we are the only ones with ATI having this problem, maybe we've got faulty cards?

---

### Post by 0004tom on 2010-08-29
> **kotnik said:**
> Tom, if we are the only ones with ATI having this problem, maybe we've got faulty cards?

That's an interesting thought. Altho there is an 2 year old bug on the ATi Bug Tracker, which to me seems like more people are being effected by this and just don't really care. 

The open source Radeon drivers are meant to have 2D/3D acceleration for the 5xxx HS series of cards soon, they've already missed the time to be included with Meerkat, but might be included with 11.04. I'd all so guess it won't take long for some kind of guide to install them into Meerkat.

[http://www.phoronix.com/scan.php?page=article&item=amd_evergreen_3d&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_evergreen_3d&num=1)

We have 4 more weeks to the next updates to the ATi drivers. Nothing more we can do I guess :(

---

### Post by kotnik on 2010-08-31
Saga continues.

I just installed Mplayer from SVN repository, hoping that it'd fix things, or at least show where the problem might be, but it did nothing.

---

### Post by andrew.46 on 2010-09-01
Hi tom,

> **0004tom said:**
> I tired the softwares from that PPA again, and they work no flash before playback, however I use VLC for one reason, to play from RARs and with the binarys from this PPA this feature of VLC is broken. 

Not much help for your main question but you might be interested to know that MPlayer can play directly from rar files as well. Something like the following would work:

```

unrar p -inul *my_file.rar* | mplayer -cache 2048 -

```

Probably not from an MPlayer gui though I suspect :(.

Andrew

---

### Post by 0004tom on 2010-09-05
Thanks for the suggestion, it seems to work with that PPA however I'm stilling getting the flash before playback with mplayer now.

---

### Post by kotnik on 2010-09-05
Well, now I'm really puzzled.

Finally got some time to try to get to the bottom of this, and I ended up more confused than ever.

First of, being programmer, I decided to debug mplayer to see where the blanking occurs. I started with SVN checkout I mentioned (r32037), compiled it with debugging information, and started poking it with gdb. And I found out that blank pause is caused by this line in libvo/vo_xv.c:637:

```

if (Success != XvQueryExtension(mDisplay, &ver, &rel, &req, &ev, &err))

```

Than I went around the Internet looking up what does that thing do (just returns version) and checked if any other ATI users complained. Than I tried fixing stuff (hardcoding for my specific system) and when I run mplayer next time - there were no blanking! Just like that, without any reason, it disappeared by it self.

I grabbed fresh copy from svn, compiled it, and again, mplayer didn't blank screen while starting and ending video.

I won't touch anything, but knowing how this thing fixed itself, I am expecting for problem to return pretty soon.

Tom, since I narrowed this down to XV extension, I suggest you compile Mplayer yourself, but with --disable-xv --disable-xvmc parameters. I think it will help.

If you need help doing it, I'll be more than glad to help you.

---

### Post by 0004tom on 2010-09-05
Did you do anything else after compiling mplayer? I've just compiled it now, with your options and sadly it's still killing my screens before playback.

```
23:39:57-tom @ L0CALH0ST :~/mplayer_build/mplayer mplayer --version
Unknown option on the command line: --version
Error parsing option on the command line: --version
MPlayer SVN-r32050-4.4.3 (C) 2000-2010 MPlayer Team

```

I used andrew.46 thread, located [here]("http://ubuntuforums.org/showthread.php?t=1542240") but with compiling mplayer i used this command.

```
cd $HOME/mplayer_build && \
svn checkout svn://svn.mplayerhq.hu/mplayer/trunk mplayer && \
cd mplayer && \
./configure --confdir=/etc/mplayer --disable-mencoder --disable-x264 --disable-xv --disable-xvmc && \
make && \
sudo checkinstall -D --install=yes --fstrans=no --pakdir "$HOME/mplayer_build" \
   --pkgname mplayer --backup=no --deldoc=yes --deldesc=yes --delspec=yes --default \
   --pkgversion "3:1.0~svn-$(grep "#define VERSION" version.h | cut -d"-" -f2)" && \
make distclean
```

Did I compile it incorrectly?

---

### Post by kotnik on 2010-09-18
Yes, you've compiled it correctly.

But, after a while the bug reappeared, and I'll try debugging Mplayer again, to see what changed this time.

Stay tuned...

---

### Post by yuki01 on 2010-09-20
Hi all.

I am new to ubuntu forums.
I have the same issue with mplayer and xine-ui, but on debian 5.0.5.
This issue not exist on Totem player with xine engine.

My card is Ati Radeon HD 5570 and issue exists on all drivers for this card from 10.4 to 10.9.


---------------
My english is not good. :(

---

### Post by Veikk0 on 2010-09-21
I also have this problem with my HD 5450 using the proprietary drivers. The flashing has been present for the whole time I've had this card (got it in April). I kind of got used to it but the flashing is still very annoying.

Flashing occurs with VLC and MPlayer using various output options. Totem doesn't flash the screen, Xine I haven't tried.

It would be interesting to know how hardware-related this is. So far there's two people with HD 5450's and one with a HD 5570. Maybe others are affected by this too but just haven't complained?

Yes, I'm looking at you non-registered user :P If you have this problem, just take the time to register and post. It only takes a minute or two.

Video card details: ATI Sapphire Radeon HD5450 512MB GDDR3 PCIe.

---

### Post by kotnik on 2010-09-22
Thanks guys for showing up, Tom and I were starting to think we're the only ones with this problem.

But, Veikk0, I am also the owner of one HD 5570.

Since there are players that don't have this issue, we're thinking it might be avoidable in mplayer as well. I did some hacking, and thought that the issue was in vo_xv, but Tom proved me wrong.

Still haven't found time to play more with it. If you have any idea - please let us know.

I'm hoping I won't be forced to change my video card, but I can tell right now what I won't purchase in the future.

---

### Post by sqti on 2010-09-25
I have the same problem on my Radeon 5670... catalyst 10.9, ubuntu 10.04.1
This happens only in Gnome, or KDE too?

---

### Post by yuki01 on 2010-09-26
Hi sqti.
I installed KDE, and checked xine and vlc. Problem still exists.
I also checked VLC for Windows under WINE. Problem still exists.
But in KDE i found NOATUN player, in which problem does not exists.
So for now we have two video players (Totem and Noatun), which are not affected by "The Black Screen" problem.

I am wondering about one thing. Why Totem and Noatum works?

---

### Post by kotnik on 2010-09-26
> **yuki01 said:**
> I am wondering about one thing. Why Totem and Noatum works?

Beats me.

At first, I thought that XV video output is to blame, but Tom proved me wrong, as I did myself.

Right now, I'm compiling Mplayer with various switches, to see if something will work out.

Will keep you posted, if I stumble upon a solution.

---

### Post by kotnik on 2010-09-26
So, I've been recompiling Mplayer this morning, as I wrote in previous post.

And I finally stumbled upon winning combination. With this configure parameters, Mplayer doesn't blank screen:

```
./configure --disable-xv --disable-xvmc --disable-x11
```

After that, Mplayer is playing via SDL. This is what is says:

```
[VO_SDL] Using driver: x11.
```

But, what's important, no more black screens! Please, if you're idle, test this and let me know if it works for you as well.

---

### Post by yuki01 on 2010-09-26
hi kotnik.
I was not able to compile mplayer due to many errors during compilation.
I have big mess in my system (did very, very bad, mad things with it :twisted:) and i think about reinstalation.

But, what with other video players (xine, vlc)?

---

### Post by kotnik on 2010-09-27
Yuki01, if you post errors you've encountered with compiling mplayer, I might be able to help you.

As far as other player, I've only tried VLC and I'm using it right now since it doesn't blank screen as mplayer does.

---

### Post by sendblink23 on 2010-09-27
> **kotnik said:**
> Yuki01, if you post errors you've encountered with compiling mplayer, I might be able to help you.

As far as other player, I've only tried VLC and I'm using it right now since it doesn't blank screen as mplayer does.

hmm you have just written VLC does not blank screen for you anymore...  what did you do to fix that?

I'm on Ubuntu 10.04 LTS x64 using crossfireX 5770 latest catalyst 10.9 & latest VLC and I get the blank screen issue

Now regular Movie Player works perfectly fine on any movie video files I've tested... but I want it fixed on VLC since I prefer it more

---

### Post by yuki01 on 2010-09-27
I have finally compile mplayer without errors.
But in my case, i have no working video output at all.
However, mplayer is less important for me.

I prefer xine as my primary video player and vlc as my emergency video player. :)

As for now, i can get rid of "The Black Screen" problem, by repleacing fglrx driver with vesa driver in xorg.conf.

---

### Post by yuki01 on 2010-09-27
I have finally compile mplayer without errors.
But in my case, i have no working video output at all.
However, mplayer is less important for me.

I prefer xine as my primary video player and vlc as my emergency video player. :)

As for now, i can get rid of "The Black Screen" problem, by repleacing fglrx driver with vesa driver in xorg.conf.

---

### Post by 0004tom on 2010-09-30
Well atleast we are not the only ones lol. There as also been a replay to the bug report on the amd bug tracker thing, a link is in the orignal post.

I've just ran update manager and installed kernel 32-25 that broke the driver, ATi have release a hotfix for it, I've installed this, everythings working once again, however the flash still remains. Altho in the change log there is alot of talk about adressing XV overlay issues. People are also saying that XV issues are fix in the 10.10 beta, thats been pushed into meerkats repos. So i'll be doing a fresh install later on tonight with the RC of 10.10 once I've finished my evenings tasks.

edit.. I'm doing a meerkat install as I'm unable to find a link to any 10.10 beta drivers

Edit 2.. the flash still remains. :(

---

### Post by mike_2000_17 on 2010-09-30
Hey all,

Just to add to the list of people with the same problem, I'm also having it. I run Kubuntu 10.04 LTS 2.6.32 with an ATI Radeon HD 5770 card on the Catalyst 10.09 driver. I get a black screen moment before starting any video on VLC, but I don't get any problems with the Dragon Player (the video player given by default with Kubuntu). But that video player sucks compared to VLC, so I would like to find a fix too. But maybe I'll just wait for the 10.10 if it is supposed to be fixed then.

cheers,
mike

---

### Post by 0004tom on 2010-10-01
Hmm.. I tried to compile mplayer on 10.10 got errors, So i decided to install 10.04 again, and I get the same errors.


```
ffmpeg/libavutil/libavutil.a(mathematics.o): In function `av_rescale_rnd':
mathematics.c:(.text+0x56): undefined reference to `assert'
mathematics.c:(.text+0x67): undefined reference to `assert'
mathematics.c:(.text+0x76): undefined reference to `assert'
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1
```

Command I'm using

```
cd $HOME/mplayer_build && \
svn checkout svn://svn.mplayerhq.hu/mplayer/trunk mplayer && \
cd mplayer && \
./configure --confdir=/etc/mplayer --disable-mencoder --disable-x264 --disable-xv --disable-xvmc --disable-x11 && \
make && \
sudo checkinstall -D --install=yes --fstrans=no --pakdir "$HOME/mplayer_build" \
   --pkgname mplayer --backup=no --deldoc=yes --deldesc=yes --delspec=yes --default \
   --pkgversion "3:1.0~svn-$(grep "#define VERSION" version.h | cut -d"-" -f2)" && \
make distclean
```

Think i'll spent an hour or so trying to troubleshot this, if I find a fix, I'll post it here.

Just out of curiosity, what ubuntu builds are people using? i386 or x86_64. I'm on x86_64.

---

### Post by 0004tom on 2010-10-01
> **kotnik said:**
> So, I've been recompiling Mplayer this morning, as I wrote in previous post.

And I finally stumbled upon winning combination. With this configure parameters, Mplayer doesn't blank screen:

```
./configure --disable-xv --disable-xvmc --disable-x11
```

Indeed you have, Finally after giving up with todays svn, I grabbed yesterdays snapshot, compiled first time around. And yes no longer having the "flash of bordem" lol


```
15:31:58-tom @ L0CHALH0ST: ~ mplayer -version
Unknown option on the command line: -version
Error parsing option on the command line: -version
MPlayer SVN-r32415-4.4.3 (C) 2000-2010 MPlayer Team
```

Okay now we seem to be getting somewhere. What switches have you tried when compiling mplayer kotnik?

I've just recompiled mplayer with only --disable-x11 and I don't get a flash before playback, and i'm also usings andrews tip about playing from rars.

I'm asking as I'd really love to keep xvmc as I understand is used to put the video load onto the GPU, and have better playback with x264 HD video.

I also now have to try and compile vlc with these switches.

---

### Post by yuki01 on 2010-10-01
Hi all.

I finally have no "The Black Screen" problem in xine. :mrgreen::mrgreen::mrgreen::mrgreen::mrgreen:
I download sources of xine-lib 1.1.19 and xine-ui 0.99.6, and compile it without switches.

So i do not understand, this bug is video card driver-related or video players-related???

---

### Post by kotnik on 2010-10-02
> **0004tom said:**
> 
Okay now we seem to be getting somewhere. What switches have you tried when compiling mplayer kotnik?

I've just recompiled mplayer with only --disable-x11 and I don't get a flash before playback, and i'm also usings andrews tip about playing from rars.


Tom, I tried almost all combinations of video outputs, and when I first hit the combination I wrote above, that's when I stopped.

If disabling X11 is enough, that's what I'll do as well. Also, my wife is complaining that SSA/*** subtitles are not rendering, so I've got some dependencies to hunt.

Edit. I find it funny that AdvancedSubStation gets filtered as profanity :)

---

### Post by kotnik on 2010-10-02
> **yuki01 said:**
> 
So i do not understand, this bug is video card driver-related or video players-related???

Yuki, it's driver related, at least I think so. If you dual-boot with that other OS (as I don't), you can try video overlay in it, and if blanks - then it's hardware related.

---

### Post by kotnik on 2010-10-02
Funny times, I can only say that.

I tried git branch of Mplayer (Uoti Urpala's, he's on of core mplayer developers), compiled it with X11 and it doesn't blank screen. Who'd knew that?!

Beside working mplayer, I got other goodies such as multithreading mplayer (I have dual-core CPU) and other stuff.

I compiled from commit 7a669a. It works fine.

If you want to try, install git-core and fire up these commands:

```
git clone git://repo.or.cz/mplayer-build.git
cd mplayer-build/
./enable-mt
./init -s
make -j4 # I have dual-core, hence 4
```

Afterwards, in mplayer subdirectory, you'll have working mplayer. I made a package with checkinstall, so I don't have to compile smplayer as well.

---

### Post by 0004tom on 2010-10-02
> **kotnik said:**
> Funny times, I can only say that.

I tried git branch of Mplayer (Uoti Urpala's, he's on of core mplayer developers), compiled it with X11 and it doesn't blank screen. Who'd knew that?!

Beside working mplayer, I got other goodies such as multithreading mplayer (I have dual-core CPU) and other stuff.

I compiled from commit 7a669a. It works fine.

If you want to try, install git-core and fire up these commands:

```
git clone git://repo.or.cz/mplayer-build.git
cd mplayer-build/
./enable-mt
./init -s
make -j4 # I have dual-core, hence 4
```

Afterwards, in mplayer subdirectory, you'll have working mplayer. I made a package with checkinstall, so I don't have to compile smplayer as well.

Right okay, so now i'm confused. Your saying you have mplayer with x11 enabled?

I've just managed to compile VLC with x11 disable and it's work same as mplayer. (no flash before playback)

He's the commands I used to compile it.

```
sudo apt-get build-dep vlc
sudo apt-get install lua5.1 libxcb-shm0-dev libxcb-shm0-dev libxcb-xv0-dev libxcb-keysyms1-dev libx11-xcb-dev
./configure --disable-xvideo --disable-xcb
```

If you want test it yourself. I just decided to disable every call to x11, so now I just need to try and different combinations.

---

### Post by 0004tom on 2010-10-03
> **kotnik said:**
> Funny times, I can only say that.

I tried git branch of Mplayer (Uoti Urpala's, he's on of core mplayer developers), compiled it with X11 and it doesn't blank screen. Who'd knew that?!

Beside working mplayer, I got other goodies such as multithreading mplayer (I have dual-core CPU) and other stuff.

I compiled from commit 7a669a. It works fine.

If you want to try, install git-core and fire up these commands:

```
git clone git://repo.or.cz/mplayer-build.git
cd mplayer-build/
./enable-mt
./init -s
make -j4 # I have dual-core, hence 4
```

Afterwards, in mplayer subdirectory, you'll have working mplayer. I made a package with checkinstall, so I don't have to compile smplayer as well.

Sorry to be the bearer of bad news yet again lol

I just followed your instructions and compiled mplayer from git. I get the flash before playback and after stopping the video.

---

### Post by sendblink23 on 2010-10-16
> **0004tom said:**
> Right okay, so now i'm confused. Your saying you have mplayer with x11 enabled?

I've just managed to compile VLC with x11 disable and it's work same as mplayer. (no flash before playback)

He's the commands I used to compile it.

```
sudo apt-get build-dep vlc
sudo apt-get install lua5.1 libxcb-shm0-dev libxcb-shm0-dev libxcb-xv0-dev libxcb-keysyms1-dev libx11-xcb-dev
./configure --disable-xvideo --disable-xcb
```

If you want test it yourself. I just decided to disable every call to x11, so now I just need to try and different combinations.

Random question is that still working for VLC?
And if so.. should I uninstall my VLC and just use those commands to make your version?

*Incase I'm asking for 10.10

---

### Post by sqti on 2010-10-16
And what about new Ubuntu 10.10 guys? There's still the same problem?

---

### Post by 0004tom on 2010-10-16
> **sendblink23 said:**
> Random question is that still working for VLC?
And if so.. should I uninstall my VLC and just use those commands to make your version?

*Incase I'm asking for 10.10

It should work for 10.10 I've not upgraded to 10.10 due to some kernal bugs that affect me. If your not having a flash before playback, then you shouldn't worry about this.

> **sqti said:**
> And what about new Ubuntu 10.10 guys? There's still the same problem?

sadly yeah, this stilll happens with the 10.10 (ATi) drivers that are in mavericks repos. You'll have to compile either vlc or mplayer, as suggested in this thread.

Well saying that, the drivers are on beta, officially the drivers should be released sometime in the next 2 weeks. We can only hope that ATi have been reading the bug reports, and have looked into this.

---

### Post by kotnik on 2010-10-16
> **0004tom said:**
> Right okay, so now i'm confused. Your saying you have mplayer with x11 enabled?


I am saying exactly that.

See screenshot in attachment. I just had to recompile Mplayer (from git branch I mentioned above) since I upgraded to 10.10. And Mplayer works without any problem.

---

### Post by SeePU on 2010-10-21
> **0004tom said:**
> It should work for 10.10 I've not upgraded to 10.10 due to some kernal bugs that affect me. If your not having a flash before playback, then you shouldn't worry about this.



sadly yeah, this stilll happens with the 10.10 (ATi) drivers that are in mavericks repos. You'll have to compile either vlc or mplayer, as suggested in this thread.

Well saying that, the drivers are on beta, officially the drivers should be released sometime in the next 2 weeks. We can only hope that ATi have been reading the bug reports, and have looked into this.Hope springs eternal.   Why would ATI do something crazy and actually support their latest cards in Linux?!?

---

### Post by kotnik on 2010-10-21
> **0004tom said:**
> Sorry to be the bearer of bad news yet again lol

I just followed your instructions and compiled mplayer from git. I get the flash before playback and after stopping the video.

Here's the [deb file]("http://aaa.etondigital.com/user_files/mplayer_2.0-3_amd64.deb") I'm using. After installing it, add this to /etc/apt/preferences.d/mplayer:

```
Package: mplayer
Pin: release a=now
Pin-Priority: 1001
```

To prevent apt from upgrading it.

---

### Post by 0004tom on 2010-10-22
> **kotnik said:**
> Here's the [deb file]("http://aaa.etondigital.com/user_files/mplayer_2.0-3_amd64.deb") I'm using. After installing it, add this to /etc/apt/preferences.d/mplayer:

Hmm, yeah your right, no flash with the mplayer you provided. So I must have done something wrong when I compiled mplayer from git.

---

### Post by 0004tom on 2010-10-22
The 10.10 drivers were released a few hours ago, I've just tested them on a new maverick install, flash still remains with VLC nd mplayer from the repos.

:(

---

### Post by kotnik on 2010-10-23
> **0004tom said:**
> The 10.10 drivers were released a few hours ago, I've just tested them on a new maverick install, flash still remains with VLC nd mplayer from the repos.

:(

I guess we'll have to live with this, ah, feature.

---

### Post by ostaja on 2010-12-15
If you enable example Caffeine (Program which prevent screensaver activation), VLC does not flash screen after that.
Also VLC prevent screensaver activation, which activate automatically when video is started.

Programs which prevent screensavers, flashes screen. I think those programs disable **dpms** activation, **which cause flash**.

So if you do not need dpms, you can let caffeine always be activated, when VLC videos do not make screen flash. **With this you can work around VLC problem.**

---

### Post by imbjr on 2010-12-15
> **ostaja said:**
> If you enable example Caffeine (Program which prevent screensaver activation), VLC does not flash screen after that.
Also VLC prevent screensaver activation, which activate automatically when video is started.

Programs which prevent screensavers, flashes screen. I think those programs disable **dpms** activation, **which cause flash**.

So if you do not need dpms, you can let caffeine always be activated, when VLC videos do not make screen flash. **With this you can work around VLC problem.**

What if I were to disable dpms? Would those apps be no longer able to cause the black-out?

---

### Post by 0004tom on 2010-12-15
Thanks for the suggestion ostaja, however following what instructions you have given, I still get the flash before playback, using yesterdays 10.12 driver. 

Perhaps I'm doing something wrong, would care to give some detailed instructions?

edit... oh

I manually disabled srceensaver in VLC that delayed the flash for like 20 seconds. 
But then I tried it again, and it seemed to no flash.

Tools > preferences > click on all at the bottom and the video towards the bottom of the window will be a tick box with Disable screensaver, I just unticked this.

---

### Post by ostaja on 2010-12-16
> **0004tom said:**
> Thanks for the suggestion ostaja, however following what instructions you have given, I still get the flash before playback, using yesterdays 10.12 driver. 

Perhaps I'm doing something wrong, would care to give some detailed instructions?

edit... oh

I manually disabled srceensaver in VLC that delayed the flash for like 20 seconds. 
But then I tried it again, and it seemed to no flash.

Tools > preferences > click on all at the bottom and the video towards the bottom of the window will be a tick box with Disable screensaver, I just unticked this.

Right, VLC -> tools -> preferences -> "Show Settings to All" -> video -> and there is "Disable screensaver".

Seems that we found a **easy** solution to this problem.

---

### Post by 0004tom on 2010-12-16
It also works with out the need of caffeine. But I wouldn't go as far as call it a solution, as it's taking away some kind of functionality, if you choose not to use an "outside" app, in this case Caffeine to disable the screensaver. As you said "A work around".

But yes, it's alot easier then having to compile vlc without xvideo.

---

### Post by erethil on 2010-12-30
hi guys

as you i have and ati card and haved problems with the videos, i usually use mplayer ...

and im quite proud to say i have found a solution.

just need to shutdown de dpms

in a console type

$ xset -q 

to see your config

$ xset s off

to shut down screensaver

# deactivate
$ xset -dpms

# activate ( i don't want !! xd )
$ xset +dpms

hope works for everyone!!

my fount is in this page [http://nomikos.info/2010/12/12/como-activar-y-desactivar-salvapantallasscreensaver-y-el-ahorro-de-energiapower-saving-del-monitor-en-linux-usando-xset.html](http://nomikos.info/2010/12/12/como-activar-y-desactivar-salvapantallasscreensaver-y-el-ahorro-de-energiapower-saving-del-monitor-en-linux-usando-xset.html)

---

### Post by imbjr on 2011-01-03
> **erethil said:**
> hi guys

as you i have and ati card and haved problems with the videos, i usually use mplayer ...

and im quite proud to say i have found a solution.

just need to shutdown de dpms

in a console type

$ xset -q 

to see your config

$ xset s off

to shut down screensaver

# deactivate
$ xset -dpms

# activate ( i don't want !! xd )
$ xset +dpms

hope works for everyone!!

my fount is in this page [http://nomikos.info/2010/12/12/como-activar-y-desactivar-salvapantallasscreensaver-y-el-ahorro-de-energiapower-saving-del-monitor-en-linux-usando-xset.html](http://nomikos.info/2010/12/12/como-activar-y-desactivar-salvapantallasscreensaver-y-el-ahorro-de-energiapower-saving-del-monitor-en-linux-usando-xset.html)

Unfortunately, this did not work. Or was there something else I had to do?

---

### Post by 0004tom on 2011-01-03
So setting DPMS to disabled, also doesn't work, mine is already disable.

After some investigation, I found that if i retick the disable screensaver option in VLC it automaticly disables DPMS, once I enable it to test. But still without the disable screensaver option in VLC I do'nt get the flash.

Edit, I'm now using the 10.12 driver on 2.6.37-RC7 kernal

edit 2 lol, okay after more playing about, I finally got it to work. With me playing about with the settings in VLC that was changing the DPMS settings also when it was on. I enable the disable screensaver option in vlc, closed vlc, then set xset -dpms to disable it, that option then stuck. Played a video in VLC and got no flash.

---

### Post by erethil on 2011-01-12
i have disabled the screensaver and and make a command line for the init of the pc for execute xset auto

---

### Post by 0004tom on 2011-05-22
Just thought I'd bumb this thread, with some information.

I'm not sure from which catalyst this issue has been fixed, but i'm running 11.05 now, and I don't have to use any of the methods discussed in this thread anymore, to stop the flash before video play back.

I've only just found out, in the last few days I reinstall my Arch linux system, and it seems to be working fine with vlc, mplayer both with vaapi enabled.

Has anyone else notice this?

---

### Post by johncoss on 2011-06-29
Hi to all.

I had exactly the same issue with flash screen in VLC (and in SMPlayer). I use Ubuntu 10.10, Graphics card RADEON HD2600 PRO and Catalyst driver 11.6. Flash screen only happens with ATI drivers. Ubuntu's open-source drivers didn't flashed.

Funny that ATI still didn't fixed this issue. 

> edit 2 lol, okay after more playing about, I finally got it to work. With me playing about with the settings in VLC that was changing the DPMS settings also when it was on. I enable the disable screensaver option in vlc, closed vlc, then set xset -dpms to disable it, that option then stuck. Played a video in VLC and got no flash.

Tom's solution worked for me... So I just wanted to say thanks and to leave info about my configuration :)

---

### Post by ek747 on 2011-10-10
I had the same issue with 10.04 64bit, however changing from vga to hdmi seem's to have fixed the issue.

---

### Post by djvujke on 2012-04-04
hi guys
i have integrated intel hd 2000 and it also flashes while starting mplayer/vlc.
although xset -q  showed as dmps disable i did enable and disable it and after that i have no flashing.
i do need to know how to do it permanently.


i have linux mint 12 KDE

memphisto@HP8200 ~ $ uname -a
Linux HP8200 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 20:45:39 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

---

