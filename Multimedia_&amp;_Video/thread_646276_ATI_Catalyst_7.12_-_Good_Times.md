---
title: "ATI Catalyst 7.12 - Good Times?"
date: 2007-12-21
forum: Multimedia &amp; Video
---

### Post by Farenheit on 2007-12-21
It looks like ATI Catalyst 7.12 drivers came out.  Has anyone tried them?  Hot or not?

If I install them, would I need to uninstall the old drivers before installing the new ones?

---

### Post by rvf on 2007-12-21
It's a pretty minor release.  The only changes are:
>     
[LIST]
[*] A memory leak is no longer noticed when running OpenGL applications
[*] Running X -configure no longer results in a segmentation fault in the fglrx driver
[*] fglrxinfo no longer reports OpenGL Render string: as Mesa GLX Indirect on systems containing an ATI Rialto AGP series of product 
[/LIST]

I don't see any noticeable difference in compiz performance.  All the previous issues are still there.

If you build debs from the setup program, they should upgrade a previous 7.11 installation seamlessly.  I can't speak for any earlier versions.

EDIT: I should note that I'm using the AIGLX support in the fglrx driver--just to clarify what I meant by "previous issues."

---

### Post by Tarmael on 2007-12-21
Yeah, I'm running them.

They work well.

Compiz is fine.

Gaming is nice.

---

### Post by mmanzato on 2007-12-21
"Official" fglrx packages for gutsy (xorg-driver-fglrx & c.) are still at 8.37.6. 

I understand that 7.11 (and even the previous 8.x.x) weren't packaged for Ubuntu because they were considered unstable even by ATI.

Although I _could_ compile them myself, I'd rather not if I could apt-get them. Is there any chance that 7.12 be packaged in the official repositories so that I can get them with a standard upgrade?

Bye

---

### Post by kthijs on 2007-12-21
quake 4 seems to play better at higher resolutions, but maybe I'm only imagining that :confused:

---

### Post by Onimae on 2007-12-21
I've actually been having a problem with my install. amdcccle states the my max resolution on this monitor is 1440x900, which is true, however I cannot go above 1152x864. Anyone know why this would be happening? (Obviously this is a widescreen, if that helps anything).

**Peter**

---

### Post by Farenheit on 2007-12-21
> **Onimae said:**
> I've actually been having a problem with my install. amdcccle states the my max resolution on this monitor is 1440x900, which is true, however I cannot go above 1152x864. Anyone know why this would be happening? (Obviously this is a widescreen, if that helps anything).

**Peter**

Maybe something in your xorg.conf is messed up.  You might look in there at the supported resolutions.  Under the "Screen" section, there should be a "Display" subsection, with all the supported modes listed.  Add/edit resolutions to taste.

Anyway, I suppose I'll try the drivers tonight (I used the AIGLX install method as well)...backed up my root partition with partimage just in case.

@mmanzato, who knows if they'll package them for Ubuntu.  I suppose the drivers are about "as stable as they'll get" for now.  Might as well bite the bullet and install them...tons of how-to's on here.  It made my Enemy Territory Quake Wars playable when I did.

---

### Post by Onimae on 2007-12-21
> **Farenheit said:**
> Maybe something in your xorg.conf is messed up.  You might look in there at the supported resolutions.  Under the "Screen" section, there should be a "Display" subsection, with all the supported modes listed.  Add/edit resolutions to taste.

Anyway, I suppose I'll try the drivers tonight (I used the AIGLX install method as well)...backed up my root partition with partimage just in case.

@mmanzato, who knows if they'll package them for Ubuntu.  I suppose the drivers are about "as stable as they'll get" for now.  Might as well bite the bullet and install them...tons of how-to's on here.  It made my Enemy Territory Quake Wars playable when I did.

I tried adding those manually and it still didn't seem to want to work...it would seem that widescreen resolutions don't happen with this new driver...is that a misguided belief?

**Peter**

---

### Post by Number_6 on 2007-12-21
Anyone else been getting the Mesa problem from this? I seem to be installing everything correctly by building the packages, but fglrx just won't start. I was able to get it working the same way with 7.11 last week. If I try typing 'sudo modprobe fglrx' it tells me "FATAL: Error running install command for fglrx". I'm back to running 8.37 right now.

I've heard they fixed the suspend bug for this release. Any comments?

---

### Post by cbrigstocke on 2007-12-21
It's supposed to fix the suspend issue as well.  Suspend doesn't really work for me regardless so not a big deal for me.

---

### Post by Onimae on 2007-12-21
Suspend does now work (for me at least). Also, Xv started working out of no where (in the previous release, Xv wouldn't load). Pretty much everything is improved, except my resolution has been regressed. I'm keeping 7.12, though, because suspend is more important to me than a wide resolution, though I really hope they release a hot fix for that or something, as it is kind of a problem.

**Peter**

---

### Post by superm1 on 2007-12-21
> **mmanzato said:**
> "Official" fglrx packages for gutsy (xorg-driver-fglrx & c.) are still at 8.37.6. 

I understand that 7.11 (and even the previous 8.x.x) weren't packaged for Ubuntu because they were considered unstable even by ATI.

Although I _could_ compile them myself, I'd rather not if I could apt-get them. Is there any chance that 7.12 be packaged in the official repositories so that I can get them with a standard upgrade?

Bye
They **do** build debs for you.

```
./ati-VERSION.run --buildpkg Ubuntu/gutsy
```

---

### Post by aya_pro on 2007-12-21
> **Onimae said:**
> I've actually been having a problem with my install. amdcccle states the my max resolution on this monitor is 1440x900, which is true, however I cannot go above 1152x864. Anyone know why this would be happening? (Obviously this is a widescreen, if that helps anything).
**Peter**
Exactly my problem. I have the same resolution and it dropped to 1152x864. I have found no solution, so went back to 7.11...

---

### Post by rvf on 2007-12-21
> **superm1 said:**
> They **do** build debs for you.

```
./ati-VERSION.run --buildpkg Ubuntu/gutsy
```

Exactly.  The only thing that needs to compile is the kernel module.  I will say that the packages the 7.12 driver generates actually compile the kernel module (and inform you of it) during installation.  For some reason the 7.11 drivers did not (at least for me).

---

### Post by Farenheit on 2007-12-21
Well, got them loaded for my X1800XL...they seem to be OK for me (I only have a standard 4:3 monitor).  My Enemy Territory Quake Wars didn't freeze up after 1 hour of play, so that is better (maybe something to do with the memory leak fix).  

Compiz still causes flicker in OpenGL and video playback (does anyone else have this?).  Basically any games and videos flicker unless I disable Compiz and enable Metacity.  Then I turn Compiz back on when I'm done.  Compiz seems to respond a bit faster too, but still jerks a bit.

---

### Post by MrKirby on 2007-12-22
Just for reference:

I have an ATI Radeon x1600 Pro AGP 512 (non-mobility) that I was only previously able to get desktop effects to work with XGL until this update.  Using XGL with the previous version STILL had the slow scrolling problem for me, so if you have an x1600 series i would suggest switching, because I actually saw a very slight improvement in the scrolling problem.

I also now have direct rendering, which also didn't seem possible (or easy to accomplish) with this card and desktop effects previously.

Compiz works great, seems just a bit slower, but definitely acceptable as far as all the flashy stuff.

Downside: Problems playing videos.  All flickery and stuff playing with VLC, movieplayer etc. in a window, but the flickering does not happen in fullscreen.  This does not affect flash videos ( l like stumble video), although it does affect their performance in browser windows, so keeping your stumble videos to a small size and just using enhanced desktop zoom to put 'em fullscreen seems to make the framerates watchable.

Overall, I'm *happier* with the new drivers and AIGLX on my radeon X1600 and am looking forward to more improvements.

Now that I think of it, though, I haven't tried XGL with the new drivers, but I think I'm just gonna keep it here for now, as it's useable and will make it easier to upgrade the drivers again later.

[Another thread that shows my config for those who are interested]("http://ubuntuforums.org/showthread.php?p=3991041#post3991041")

---

### Post by bladerunner6 on 2007-12-24
i thought they had fixed the flickering with compiz enabled!

---

### Post by precursor on 2007-12-24
Hey Guys -

I installed the 7.12 last night on my laptop (Asus F7 w/ mobility 2400HD) and here is what I have found:


- Compiz is much smoother for me overall, no where near as jerky as it was.

- World of Warcraft runs very smooth as well

- I also cannot get my full resolution - 1440x900

- Video Playback and Open GL are choppy if compiz is enabled, disabling it does fix the problems

- I still cannot suspend or hibernate with my laptop =/



Hopefully we will see an updater after Christmas is over.

---

### Post by prince_niceguy on 2007-12-24
I am having 1650x1050 display and seems there is a known issue in ati latest drivers.

Connecting a display device that supports 1680x1050 to a system running Linux may result in a maximum display resolution of 1280x1024 only being available

So, I am not upgrading... i have paid for getting a 1650x1050 resolution screen :-) and would like to use it rather than 1280x1024

---

### Post by niallporter on 2007-12-29
I installed using the method on the Unofficial Catalyst Linux Wiki for my Gutsy x86 install ([http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)).  This is the first Catalyst release I've managed to get working at all on my AGP X800XL 256MB.  I followed the "Option 2" bit on that site for gutsy to the letter and it works fine with Compiz on XOrg.  Performance is pretty nice on my 1920x1200 Dell screen.

The only issue I have is that on exiting my Gnome session whether to restart, shutdown or logout the machine seems to hang, either with a black screen or my wallpaper.  Anyone else got this?

EDIT:  Another issue, 3D acceleration seems to work, performance on Google Earth and Second Life (about the only 3D apps I run on linux) seems fine but the 3D display seems to flicker to black quite badly, anyone seen this as well?

---

### Post by niallporter on 2008-01-04
> **prince_niceguy said:**
> I am having 1650x1050 display and seems there is a known issue in ati latest drivers.

Connecting a display device that supports 1680x1050 to a system running Linux may result in a maximum display resolution of 1280x1024 only being available

So, I am not upgrading... i have paid for getting a 1650x1050 resolution screen :-) and would like to use it rather than 1280x1024

The guide I followed (see my post immediately above this one) tells you how to fix that.  It's easy, just a quick manual change in xorg.conf, I got it working fine in 1650x1080 on my girlfriend's PC.

---

### Post by prince_niceguy on 2008-01-05
Thanks for the tip.. will work out on the same today and see if it resolves.. :-)

Thanks anyway..

---

### Post by dagfinn on 2008-01-11
> **niallporter said:**
> The guide I followed (see my post immediately above this one) tells you how to fix that.  It's easy, just a quick manual change in xorg.conf, I got it working fine in 1650x1080 on my girlfriend's PC.

You mean 1680x1050?

Anyway, it didn't work for me. I couldn't set 1680x1050 no matter what I did. Suspend worked, though.

I reverted to 7.11 ([http://ati.amd.com/support/drivers/linux/previous/linux-r-cat711.html](http://ati.amd.com/support/drivers/linux/previous/linux-r-cat711.html)).

For the record, I have a Dell Vostro 1000 (ATI Radeon Xpress 1100).

---

### Post by prince_niceguy on 2008-01-12
i too tried setting 1650 x 1050. but i was not able to set it any way... :-(... reverted back to the version from the repository...

---

### Post by berman56 on 2008-01-13
Yes, for those of us with wsxga 1680x1050 LCD monitors, you have to revert back to the 7.11 driver unless you can successfully manage to manually edit your xorg.conf file.  I spent some time with my xorg.conf file to no avail.  7.11 it is until 7.13 comes out.

ATI + ubuntu gives me a headache.

---

### Post by perixx on 2008-01-13
Hi guys...

I've had my share of problems while installing both ATI and Nvidia's repository and latest drivers recently (and solved all of my ATI problems during the process). 

If you follow this link, you can see what I've found out - maybe it's also useful to you - note especially post #9 and #12 in the first thread. I'm also addressing to the flickering/tearing Vsync-problem with videos and the 'MESA' troubles:
[http://ubuntuforums.org/showpost.php?p=4054938&postcount=9]("http://ubuntuforums.org/showpost.php?p=4054938&postcount=9")
and here a summary:
[http://ubuntuforums.org/showpost.php?p=4061365&postcount=273]("http://ubuntuforums.org/showpost.php?p=4061365&postcount=273")

MESA trouble solved after changing card and re-installing drivers:
[http://ubuntuforums.org/showthread.php?t=661639]("http://ubuntuforums.org/showthread.php?t=661639")

If you're having trouble during compilation process of the ATI drivers:
[http://ubuntuforums.org/showpost.php?p=4071656&postcount=3]("http://ubuntuforums.org/showpost.php?p=4071656&postcount=3")

Regarding the screen refresh rate/flickering (e.g. for CRT's) and special resolution problems, you may look here, perhaps it helps:
[http://ubuntuforums.org/showthread.php?t=653480]("http://ubuntuforums.org/showthread.php?t=653480")
[http://ubuntuforums.org/showthread.php?t=658068]("http://ubuntuforums.org/showthread.php?t=658068")

I hope you find it useful...

perixx

---

### Post by r!ots on 2008-01-15
Did suspend/hibernate work for anyone after installing the 7.12 drivers?
For me it isn't. During suspending/hibernating the screen flickers badly and then it doesn't wake up anymore. I get a blank screen and that's it. Only thing I can do is a hard reset after suspending/hibernating, but at least everyting else is working properly with those drivers, which is an improvement.

---

### Post by dagfinn on 2008-01-16
> **r!ots said:**
> Did suspend/hibernate work for anyone after installing the 7.12 drivers?

Suspend worked for me, hibernate didn't. But I don't much feel the need for hibernate, especially since I ordered the largest battery for my Dell laptop.

---

### Post by perixx on 2008-01-20
I for myself can definitely say that ATI Catalyst 7.12 - Good Times? 
**[COLOR="Red"]NO![/COLOR]**

- Some Games don't run at all anymore; compatibility decreased
- Save and working Installation way was troublesome to find out
- Video Playback causes utterly awful tearing unless (pseudo?)-Vsync is perma-enabled and 3D-performance (which is yet everything else from satisfying) drops to unacceptable levels
- many advanced features aren't well-supported by the driver, if at all (temporal AA, HDR, AF > 4x,REAL Vsync, decent Video routines....)
- strange unpredictable digital/analog initial output switching at bootup is occuring sometimes 
- 3D-performance is not only far from perfect, but actually unusable for decent fast-paced 3D-games, yet IN LOWEST RESOLUTION and effects modes
- this baby is NO MATCH AT ALL to the Windows-drivers!!

perixx

---

### Post by aya_pro on 2008-01-21
The latest  8.1 driver solved all resolution problems on my notebook that I had with 7.12. I got my 1440x900.

---

