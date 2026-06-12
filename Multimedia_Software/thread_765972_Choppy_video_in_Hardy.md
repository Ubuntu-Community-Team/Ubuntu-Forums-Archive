---
title: "Choppy video in Hardy"
date: 2008-04-24
forum: Multimedia Software
---

### Post by gfahey on 2008-04-24
Used restricted driver for my ATI Xpress 1150/Dell Vostro 1000. Games ran OK with desktop effects turned off. However, video playback is a bit pixelated, choppy and just lousy looking. With Gutsy the video ran superb (fullscreen looking fine). 

It's annoying and I'd love to get it working OK. Are the restricted drivers somehow different for Hardy? Man, if I could just get it looking like I did on Gutsy.

Any help/suggestions appreciated.

---

### Post by Tomatosoup on 2008-04-25
Hello,

I also have a problem with choppy video in Hardy. And I've also installed Beryl or something. I have a Dell Inspiron 1501 with an Ati Radeon 1150 Xpress videocard. I'm using the restricted video driver. Installed via the Hardware Drivers menu.

The problem I guess is when I enter "glxinfo" I see Direct Rendering is not enabled...

So how do I enable this direct rendering mode should be the question I guess. I've searched the internet but found only confusing options.

Does anybody know what we should do?

---

### Post by SpaceTeddy on 2008-04-25
yep. same problem here. Just upgraded, and how videos do not run smooth anymore (although compiz-fusion IS running normal).
Also, gstreamer does not give me GL support anymore, and glxinfo says direct rendering is disabled.

Running Samsung X60 with ATI X1600 Graphics card.
Used to work just fine in Gutsy. Can anybody please help ?

[UPDATE]
just uninstalled the xserver-xgl package, and restarted the xserver. Without compiz fusion, glxinfo says direct rendering is enabled. Also videos run smoothly. But i cannot afford to loose compiz since i desperatly need the widget layer :(

---

### Post by Tomatosoup on 2008-04-25
> **SpaceTeddy said:**
> yep. same problem here. Just upgraded, and how videos do not run smooth anymore (although compiz-fusion IS running normal).
Also, gstreamer does not give me GL support anymore, and glxinfo says direct rendering is disabled.

Running Samsung X60 with ATI X1600 Graphics card.
Used to work just fine in Gutsy. Can anybody please help ?

[UPDATE]
just uninstalled the xserver-xgl package, and restarted the xserver. Without compiz fusion, glxinfo says direct rendering is enabled. Also videos run smoothly. But i cannot afford to loose compiz since i desperatly need the widget layer :(

Thanks. I also uninstalled that package now and everything seems to go a bit more smooth. And my videos are running normally smooth again.

Maybe if someone comes up with a solution for the XGL problem I'll reinstall it again though. But I don't really need it.

---

### Post by SpaceTeddy on 2008-04-25
As i am dependant on compiz (or rather, the widget layer) i've been testing some more. 

my ATI driver load, and compiz seems to be using them, since compiz does run smoothyl. **When the xgl server in not installed**, i get the following output from fglrxinfo 
```
 fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600
OpenGL version string: 2.1.7412 Release

```

which means, afaik, that the drivers where loaded successfully. Also, running glxgears give me *very* smooth performance. 

As soon as i install the xgl server, compiz seems to grab it, and then not share it with anything else. fglrxinfo show then only the MESA driver to be supported and glxgears run choppy at best. 

So the question is - why is the gl support not passed through compiz anymore (which it used to be in gutsy - i know, i USED it) ?

is there really nobody out there that has an idea on how to fix this ?

---

### Post by jwyseu on 2008-04-25
If it is only the video playback being choppy, check what output you are using to playback (xv, gl, x11, ...).

You can change this in gstreamer-properties (if you are using totem with gstreamer). When using mplayer, you could test it using mplayer -vo xv test.avi

The new radeon driver makes it possible to use xv for compiz and still be able to play video's.

---

### Post by SpaceTeddy on 2008-04-25
i've already tried all settings available on gstreamer - they all produce the same output. What makes me wonder is that the gl-option form gestreamer has disappeared.

as for mplayer - i don't have it, but i can try to install it. Although i would more like to use totem, since that can use the gvfs to stream movies over ssh/sftp.

thanks for the tip :)

---

### Post by gfahey on 2008-04-25
I followed [this]("http://ubuntuforums.org/showthread.php?p=4790960&posted=1#post4790960") and voila! Now videos look fine again! Did the trick for me.

***Update:***I had forgotten that I disabled the ATI driver under "Hardware Drivers" prior to this. I have desktop effects "off" as well. So, it looks like this:

Disable the driver and get smooth video playback. But, you can't play games, and Google Earth will cause a crash upon opening (at least for me). Compiz? Forget it.

Enable the driver and you get choppy, horrible video playback. You can play games and Google Earth works fine. Of course, I still have desktop effects "off". 

Enable desktop settings (visual effects) under "normal" and you can't play games and of course, video playback is still horrible. Google Earth won't function with them enabled either. 

I guess you have your choices but, seems a fix is in order for sure. While it's certainly possible to switch settings according to what you want to do, it's unrealistic. 

So.....I wait. (sigh)

---

### Post by szako on 2008-04-26
I experienced exactly the same. Disabled restricted driver for now to watch xvids ...

xserver-xgl + restricted ati driver:
- window loading was damn slow, using firefox was a pain the in ***
- allowed me to use mplayer with xv/gl but video was lagging both in mini and fs mode

xorg with restricted ati driver
- compiz was cool, fast
- mplayer -vo xv didnt start
- with mplayer -vo gl video was blinking
- tomato video was pixeled, choppy when went to fullscreen

---

### Post by mineval on 2008-04-26
Am experiencing the same. I'm running X1950 XT (2 of them, linked for CrossFire which works OK in Windows. In Ubuntu I'm just trying to do basic things like watching a movie)

ATI Catalyst 8.4 driver (supports Hardy, allegedly) + xserver-xgl:
-fglrxinfo shows MESA
-Everything is slow.
-Video in fullscreen mode not pixelated but slow.

ATI Catalyst 8.4 driver without xserver-xgl:
-fglrxinfo shows ATI
-Everything is smoother
-Video in fullscreen mode smooth but pixelated. Played with Anti-asliasing options in Catalyst Control Centre but found no obvious effects.

Had no problem at all in Gutsy. Hope someone'll come up with a solution soon. Thanks

---

### Post by mineval on 2008-04-26
I dont think I'm getting any hardware acceleration at all from the Catalyst 8.4 driver. 

/$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1950 Series
OpenGL version string: 2.1.7415 Release

but:

/$ glxgears
305 frames in 5.0 seconds = 60.959 FPS

Very low frame rate. I read it should be in the thousands if working properly.

---

### Post by SpaceTeddy on 2008-04-27
by now, i would say it's a bug in the xserver-xgl package or in compiz 

> laptop:~$ fglrxinfo 
display: :1.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.3)

laptop:~$ glxgears 
198 frames in 5.1 seconds = 38.953 FPS
489 frames in 5.3 seconds = 91.841 FPS
320 frames in 5.5 seconds = 58.649 FPS
300 frames in 5.4 seconds = 55.321 FPS
360 frames in 5.1 seconds = 70.864 FPS
340 frames in 5.1 seconds = 66.257 FPS

laptop:~$ sudo apt-get remove --purge xserver-xgl
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Reading state information... Fertig
Die folgenden Pakete werden ENTFERNT:
  xserver-xgl*
0 aktualisiert, 0 neu installiert, 1 zu entfernen und 0 nicht aktualisiert.
After this operation, 4682kB disk space will be freed.
Möchten Sie fortfahren [J/n]? 
(Lese Datenbank ... 159082 Dateien und Verzeichnisse sind derzeit installiert.)
Entferne xserver-xgl ...
Lösche Konfigurationsdateien von xserver-xgl ...
laptop:~$ 

then i restarted the xserver via ctrl+alt+baclspace and ran the tests again
> laptop:~$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600
OpenGL version string: 2.1.7412 Release

laptop:~$ glxgears 
24263 frames in 5.0 seconds = 4852.593 FPS
27258 frames in 5.0 seconds = 5451.474 FPS
27227 frames in 5.0 seconds = 5445.239 FPS
27230 frames in 5.0 seconds = 5445.982 FPS
27226 frames in 5.0 seconds = 5445.063 FPS
laptop:~$ 


so what does this tell me ? i don't know ! what i do know is the gl support for applications gets not handed down from the grahpics driver through the xgl-server to the application. Funny enough compiz seems to work with this - just everything else does not !

common guys, this is really annoying !

---

### Post by SpaceTeddy on 2008-04-27
right-o,

on the off chance that this might be an upgrade problem, i reinstalled gutsy on my computer (kept my home dir). But, after the new install, i still run into the same problem. As soon as xserver-xgl is installed, i loose all video performance and the grapics drivers go from ATI to Mesa.

so - i'd say the xserver-xgl package is broken ! 

Or does anybody have any better ideas ?

[EDIT]
i just started compiz (out of desperation) without having the xserver-xgl running. In pervious tests, this always failed. But Now it seemed to have worked - what means compiz can now be run without the xserver-xgl package ? also, on the updated system (from gutsy) this did NOT work. It only started working after a reinstall... 
this is getting really weird.

How can i start compiz at login time so every OTHER application started after it has been loaded ?

---

### Post by szako on 2008-04-27
Yeah, you don't need xserver-xgl to run compiz (anymore :)), that's confirmed already :-)

Seems like xserver-xgl just slows down things...

---

### Post by SpaceTeddy on 2008-04-27
anymore - in gutsy you still needed it to run compiz on a ATI card. Or i have never figured out how to do it without. 

However, running without xgl i now have the problem that i cannot put movies on the GL layer, as they flicker like crazy. Putting them on a "normal" layer kind of works, but then they suck huge amount of CPU, making high quality vids choppy again...

---

### Post by mineval on 2008-04-27
yep, compiz works fine in Hardy without xserver-xgl but fullscreen video gets pixelated, annoys the hell out of me.

---

### Post by szako on 2008-04-27
Hi

Any bugs reported yet related to this issue ?

---

### Post by SpaceTeddy on 2008-04-28
as far as i could test it, it is not compiz. If i turn compiz off i still get the pixeled videos... so i'd say it is not related to it. What is related to compiz is the fact that any openGL programm running when compiz is enabled flickers like crazy - makeing it impossible to render movies on the graphics cards (well you can, i you don't mind the flickering)...

as for the bug report... i don't know of any, but i did not really search for it. I just find it very strange that something like video support does not work properly on a LTS version. Maybe it's the graphics drivers ?

---

### Post by Pdennis on 2008-04-28
Hi,

Same problem here, I haven't really gotten a chance to play around with it yet, but disabling the proprietary ATI driver fixes the choppy video. 

I'll check back after I've had a chance to check it out some more.

---

### Post by szako on 2008-04-28
So it's a general problem! It's a good thing :)

---

### Post by legalizemeth on 2008-04-29
I got video working smooth again on my girlfriend's machine (Dell Inspiron e1505, mobility radeon X1400) by installing the restricted driver and removing xserver-xgl.  Thanks everyone!

---

### Post by herting on 2008-04-29
I will add my name to the list of those who are struggling to get this to work.  I am a bit of a Ubuntu newb so I am sure that there is something that I am missing.  I have a Dell Inspiron E1505 with the ATI X1400.

According to *System>Administration>Hardware Drivers* I am running the ATI drivers.  Also when I type fglrxinfo I get:
> display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.1.7412 Release


I am able to watch videos they are just very poor quality and I am often having to deal with significant lag if I watch in full-screen mode.  LegalizeMeth has the same situation it sounds like but when I attempt their solution of removing xserver-xgl I am told by apt-get that it isn't installed.  

I have been trolling through these forums for the past few days looking for the solution but coming up with nill.  Any help that won't break my computer would be much appreciated.

---

### Post by SpaceTeddy on 2008-04-29
i've been doing some testing myself... try to install mplayer, go into prefenrences->video and select gl (OpenGL) as output. 
This also imporved video quality for me (i already got rid of the lagging with uninstalling the xgl server). Maybe this can enhance your video output. I know this is not a desired option as totem would be the player to tweak, but this is the only player i know (so far) that is able to use the gl layer to render videos... 

> sudo apt-get install mplayer
to get mplayer installed

hope it helps

---

### Post by Anxiety35 on 2008-04-29
I've got an Nvidia card in my Dell Inspiron and have been having the same problems since the update.

I was going to try removing "xserver-xgl" like some suggested, only to find that it wasn't installed. So, I installed it instead. I just watched a 45 minute tv show fullscreen without a single bit of lag. I hope it lasts.

---

### Post by szako on 2008-04-29
> **SpaceTeddy said:**
> i've been doing some testing myself... try to install mplayer, go into prefenrences->video and select gl (OpenGL) as output. 


When I use gl in mplayer
1) normal screen mode video is flashing
2) fullscreen mode is okay ( :)

BUT both uses 100% CPU, so it's not good solution

I have to disable the restricted ATI driver, after that i can watch movies with -vo x11.

---

### Post by abds on 2008-04-29
Hey, I am having the same problems. Output of fglrxinfo 

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.1.7412 Release

```

xserver-xgl is not installed. The only problem is that when I play videos the cpu usage goes up to 100%. Everything else woks fine, even the desktop effects. 

Any ideas?

---

### Post by mineval on 2008-04-29
[http://en.wikipedia.org/wiki/Fglrx](http://en.wikipedia.org/wiki/Fglrx)

hopefully the next Catalyst driver next month will fix it. Otherwise I'm getting myself an Nvidia card.

---

### Post by rossmoore on 2008-04-29
I just wanted to back up what you guys are finding. I have an ATI X300 card, and fglrxinfo show the Mesa Indirect drivers with xserver-xgl, but the ATI drivers without xserver-xgl. And I can only get good video/compiz performance without xserver-xgl.

I have found things using a lot of CPU, although it's been smooth so far - I haven't tried high-res video though, only DVDs.

It does seem like something is a bit broken, but I don't know what. Is there someone with experience on this thread who knows how can we get this looked into by someone who can help, or raise a bug with xserver-xgl? All was fine in Gutsy, as many of you have mentioned.

---

### Post by Kirkaiya on 2008-04-29
For what it's worth - 

I have a Thinkpad T60 (Core2Duo, 2GHz) with the ATI Radeon X1400 video card, and a clean 8.04 Hardy Heron install.

I don't have the xserver-xlg package installed. I originally used Synaptics package manager to install it after reading that somebody else did that, but it gave no improvement on video-playback and made "Alien Arena", the 3D FPS game, completely unplayable, so I removed it.

I was having the same issues with the default movie player while playing back .avi files, so I installed VLC Media Player (a favorite of mine from Windows) using the Applications -> Add/Remove.. package manager.

The same videos play with VLC smoothly, even in full-screen, and the picture-quality is noticeably better.  I installed MPlayer at the same time (which made itself the default for .avi), and while the lag and picture quality are better, there is a pretty bad flicker effect.  Therefore, I set VLC to be the default player for .avi files.

So for me, at least, VLC seems to have fixed the video-playback problem.  I still have the flicker-problem when playing Alien Arena, though, so hoping that the next version of ATI's driver will resolve that.  Oh - the output from fglrxinfo:

kirkaiya@ITDAPAC:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.1.7412 Release

---

### Post by herting on 2008-04-29
For my pc I have not yet fixed the problem.  I tried VLC and it is perhaps marginally better playback than Totem but still not anywhere near average performance.  I also attempted Mplayer gl in both full screen and normal but it flickers so badly that viewing my movies isn't really possible.  I really want to be done with Windows but all I use my laptop for is watching movies and internet browsing so this really is a stubborn issue for me.

Update: I was able to kill the Mplayer with gl flicker by turning off all desktop effects but the video playback is still bad.  Very pixelated when watching videos in full screen and extraordinarily CPU intensive as well.

---

### Post by cyberdemon on 2008-04-29
I to am having this problem after the Hardy upgrade. I thought that this may have something to do with the gstreamer codecs but playback with vlc is the same so that ruled that out. it certainly has something to do with video rendering. I noticed poor video before installing the restricted drivers. So I installed them in hopes that it would get better. They did not. I then increased my visual effects and it got worse. So now I am back to normal visual effects no restricted driver watching video that is barely watchable. I have not checked if the xgl server is installed but will tonight. 

By the way I am using the 64bit version of hardy on an Ati chipset

Acer Aspire 5100

---

### Post by darkwoofe on 2008-04-29
Having the same issue here, too. It also effects some of the screensavers. I've always used VLC for video and so I didn't notice the problem until I saw my screensavers flickering. A little testing later and here I am. It's nothing major for me, but it is annoying.

---

### Post by rossmoore on 2008-04-30
Darkwoofe - I've seen you reply in another thread, where you said this:
[I]Thanks to a helpful member of the forum here, I discovered that a section of my Xorg was set to off or in my case "0". I just changed the zero to enable and the problem was solved. So find this section and make sure that it's enabled:

Before

Quote:
Section "Extensions"
Option "Composite" "0"
EndSection  

Now

Quote:
Section "Extensions"
Option "Composite" "Enable"
EndSection  

If you don't have that section, add it. Or if you have that section and it's set to "0", Enable it. I hope that this helps you with whatever issues you're having...[/I]

Is it worth anyone else on this thread trying this out to see if it fixes their problems? I'll try it out tonight, but I'm not on my Ubuntu box at the moment.

---

### Post by darkwoofe on 2008-04-30
No, I don't think that'll help anyone here unless they're having problems getting Compiz to run after removing xserver-xgl. If that's the case, the post being reffered to is posted here: [http://ubuntuforums.org/showpost.php?p=4837695&postcount=16](http://ubuntuforums.org/showpost.php?p=4837695&postcount=16)

I'm still having the issues with the flickering video and screensavers...Sorry I can't be more help.

---

### Post by Neutrino on 2008-05-01
I have the problem and when i run 'fglrxinfo' i see that ATI drivers are running the 
command 'glxinfo | grep render' says that direct rendering is on.

I think i found the problem when i run this command (to get xorg log when the system boots):

sudo cat /var/log/Xorg.0.log | grep fglrx

I get this interesting line:

Video Overlay not supported on AVIVO based graphics cards. For XVideo support use Option "TexturedVideo".

I googled it and found this post:
[http://www.phoronix.com/forums/archive/index.php/t-1426.html]("http://www.phoronix.com/forums/archive/index.php/t-1426.html")

Actually it may be a kernel driver compatibility problem.

---

### Post by rossmoore on 2008-05-01
> **Neutrino said:**
> I
I googled it and found this post:
[http://www.phoronix.com/forums/archive/index.php/t-1426.html]("http://www.phoronix.com/forums/archive/index.php/t-1426.html")

Actually it may be a kernel driver compatibility problem.

I upgraded from Gutsy using the update manager. When I boot up I get a Grub menu which shows that I can boot in to two different kernel versions. I wasn't sure what this meant (I have an idea what the kernel is, but not of the implications of picking the wrong one to boot up with), so I just picked the top one which was already set as default.

I'm not at my Ubuntu box right now, but this implies it might be worth booting in to the older kernel version that is present in the Grub menu.

Does anyone else get presented with that option at boot time, and does anyone with more experience than me think it's worth trying that to see if it fixes the problem? (Temporarily at least, until the driver compatability issue is sorted).

By the way, I'm not sure if the problem I'm having is the same as people here, so I've posted my particular problem on another thread with details from glxinfo, fglrxinfo and my xorg.conf.

Oh, and I have the fglrx driver installed and recognised by fglrxinfo, but glxinfo shows direct rendering is set to No.

---

### Post by legocorp on 2008-05-07
i have the same problem with the video pixel quality. happier to see that it's not only me. :P

---

### Post by Pépou on 2008-05-07
Same problem.. (ugly videos...) I hope a quick fix !

---

### Post by funnypanks on 2008-05-07
to make videos smoother i added this to my xorg.conf. the texturedvideo is for people with ati cards which are r500 and newer. still doesnt work with compiz. had to patch mplayer so i could use it with compiz... and ati was right they did get rid of the pixelating problem since it was completely gone once i added the texturedvideo thing. and its very reasonable with cpu usage. like 2% usage

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option		"VideoOverlay"		"on"
	Option		"OpenGLOverlay"		"off"
        Option 		"TexturedVideo"         "on"
EndSection

---

### Post by elustran on 2008-05-08
I'll have to look into the textured video mode thing to see if I can get antialiasing to work with xvideo rendering just so things work a little more cleanly.  I basically have everything working now.

In order to eliminate pixilation I'm rendering video with openGL, but that seems to interfere with compiz.  In windowed mode using mplayer video flickers, but everything looks good in fullscreen mode.  Everything else is nice and smooth - compiz works too.  As an additional note, VLC seems to have problems supporting GL in Hardy (someone already reported it as a bug), so I'm stuck using mplayer.  If you don't need to fullscreen or zoom things, just render with a different protocol, and that should work fine because then you won't be competing with compiz for gl resources.

to get things working, I've done the following:
CLEAN INSTALL (not upgrade!)
not installed xserver-xgl
updated everything
play using mplayer
select gl rendering

Earlier, before doing a clean install, I tried using xgl to see if that would help, but it borked my screen resolution settings because of some problem with xrandr.  I've tried messing around with other things like Envy, followed various install guides, mucked around with xorg.conf, etc, but the thing that finally helped was a plain old clean install.  The various tweaks required by a clean install were menial.

---

### Post by lifve on 2008-05-08
same here, Acer 5030 AMD64, ATI Radeon Xpress 200M, hardy AMD64.
I choose not to use restricted driver so the video plays well.
but it will be great if this ~bug~ fixed.

btw anyone have tried driver from ATI web? I already get one, but I don't know how to install it.

---

### Post by funnypanks on 2008-05-20
anyone try radeonhd 1.2.1 with xgl? i think im gonna try it and ill post back

---

### Post by maiden30403 on 2008-05-21
Having the same type problems with an nVidia 4400ti using restricted drivers. This may not be just an ATI problem.

---

### Post by bluemax on 2008-05-28
I have an nVidia 6600 with choppy full-screen video. Definitely not an ATI-only problem.

---

### Post by elustran on 2008-05-28
has nobody arrived at a solution without disabling compiz?

---

### Post by szako on 2008-05-30
Not yet, the gl <> compiz conflict is already bugreported i think.

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/179042](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/179042)

---

### Post by revolutio on 2008-05-30
> **szako said:**
> Not yet, the gl <> compiz conflict is already bugreported i think.

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/179042](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/179042)

The bug hasn't had any activity on it in nearly two months and is only listen as medium importance.  :confused:

This problem prohibits me from using Compiz entirely (I am rather fond of being able to watch movies on my computer) and I'd really enjoy a fix or at least an explanation why.  I'm putting off hardware upgrades on my computer until this gets explained or resolved.

Tried just about every modification to xorg.conf that has been suggested and none have cleared the problem up.

---

### Post by timcredible on 2008-05-30
here's the [thread]("http://ubuntuforums.org/showthread.php?p=5081127#post5081127") that fixed this for me.

---

### Post by revolutio on 2008-05-31
> **timcredible said:**
> here's the [thread]("http://ubuntuforums.org/showthread.php?p=5081127#post5081127") that fixed this for me.
The X11 output trick is a really just a half-measure.  Using X11 there is pretty severe quality loss and slow-down when you expand the video at all.  The difference compared to gl2 is hardly noticeable when the video is at its usual 100% windowed size.  But I kind of like watching movies with a full screen.

---

### Post by szako on 2008-06-01
I'm using Xv output, but when compiz is enabled, video gets flashing. This also goes to gl, gl2 when compiz is enabled. With X11 I can't watch fullscreen. Damn. :/

---

### Post by elustran on 2008-06-02
> **revolutio said:**
> The X11 output trick is a really just a half-measure.  Using X11 there is pretty severe quality loss and slow-down when you expand the video at all.  The difference compared to gl2 is hardly noticeable when the video is at its usual 100% windowed size.  But I kind of like watching movies with a full screen.
Why does X11 quality suck anyway, and why does it seem to be the default?

A little while ago, I was able to get gl video working in fullscreen mode (but not windowed) with compiz working too, but for some reason that stopped working - I think it must have been after a restart.

---

### Post by JarrettV on 2008-06-03
I also have the same problems with radeon 3650 card.  I also get tearing and video quality is horrible.  Should it be possible to have good video quality and desktop effects?

---

### Post by revolutio on 2008-06-04
> **JarrettV said:**
> I also have the same problems with radeon 3650 card.  I also get tearing and video quality is horrible.  Should it be possible to have good video quality and desktop effects?
I've been reading about this pretty intensely over the past few days and apparently the answer is no.  It has something to do with an inherent limitation of the DRI which will allegedly be fixed with the release of DRI2, but that is scheduled to be released right after the next Duke Nukem game.

Star-crossed lovers ATI and Linux are not.  They are more like drunken college students who bumped into each other and after waking up the next morning are wondering about how to deal with the intense hangover and profound awkwardness of their embarrassing hook-up.

---

### Post by szako on 2008-06-05
Then no workaround? :/ arrrgh

---

### Post by muteXe on 2008-06-05
Nvidia 7800GTX here, and i got the same problem. Sucks :(

---

### Post by JarrettV on 2008-06-05
I've also been researching this.  It appears that Intel will be the first to support quality video in Linux as they are working on DRI2.  Anyway, the best [explanation on poor video quality in linux]("http://lwn.net/Articles/277136/") that I have found is here:> the thing about Linux and 3D drivers is that the driver model is f*ked. It's a huge mess. And
it's not even Linux developer's fault.. it's all those years that Xfree stagnated.. Windows
left Linux in the dust when it came to video drivers. 

Right now 2D and 3D are totally different code bases, totally different APIs. But yet they
have to do very similar tasks on the same exact hardware at the same exact time. Not good. 

As far as 2D performance goes.. No video card maker has put any effort in improving it in
years.  In very modern cards there is _no_ 2D-only hardware. It will either done by internal
emulation or simply lack any support for 2D acceleration at all.

So a unified driver based on the GPU is going to be needed going forward. One that supports
multiple APIs. 

To bad we don't have one yet. Except in very early development. (Gallium3D)


Until we are able to get rid of the schism of 2D vs 3D in Linux/X.org (at the driver level..)
it will not have the stability and performance that you get from Windows or OS X. Not so much
in terms of crashing.. but just in terms of general ugliness, lack of performance, and
difficulty (on the part of driver developers and end users). 

One example is during video playback many people will notice that if they use Linux for HD
video there will be occasional tearing and lines across the middle of the screen were you have
overlapping frames and such. This is because there is no way to sync video up with your
refresh rate so that you get a nice solid frame of video ready for each screen refresh.

Why? I donno. The design of Linux drivers simply won't allow it without exceptional difficulty
I guess.

And, here are some potential solutions I have yet to try.

> Posted Apr 10, 2008 14:23 UTC (Thu) by dlarrick (subscriber, #5532) [Link]

There are actually two mechanisms to sync to VBlank under XOrg.  OpenGL has the

GLX_SGI_video_sync extension, and DRM has DRM_IOCTL_WAIT_VBLANK .  One or both of these works

on most modern hardware.  Both of these are useable for video output -- MythTV, for example,

will select whichever is available.

> **JohnLM_the_Ghost said:**
> Yeah well there are two methods.

I dont know the actual names, but it should give the idea...

1. Frame Limiter (Sometimes falsely referred as Vsync)

It really does (or tries to) synchronize the screen and monitor frame rates, but generally dont take into account the actual time when monitor refreshes. Used on software level, and the effect is strongly application and system dependent. Usually doesnt prevent tearing, but may reduce it considerably.

2. True Vsync (wait for Vretrace)

This is hardware/driver level approach. It does full frame rate and time sychronization, but all screen updating must be given to driver. While it is by far more better than former method, it is a bit harder to code (tending to do more bugs) and may cause all kinds of weird things if driver is not good. (And unfortunately Linux is quite short on good drivers, especiallly ATI's)

as for me, I'm not really intensively searching for a solution for vsync, cause I still use Windows for most part, but would be good to know how to achieve it though.

And Yeah ATI really rules lately, they're faster and cheaper. But then again - already mentioned lack of drivers.

> **MichaelZ said:**
> Mplayer is very powerful and there are some options you can add to make audio stay in sync. In mplayer.conf or config (these are found in the ~/.mplayer folder and on my system with newest svn it use config but older software uses mplayer.conf) you can add the different run time options (a sample file):

vo=gl:rectangle=1:swapinterval=1:slice-height=0 # yuv=3 introduces tearing
**double=true    # double buffering, set to false for 1080p x264 videos as CPU isn't fast enough to decode**
lavdopts=fast=1:skiploopfilter=all:threads=2 # for multi core processors x.264
cache=8128 # you should always have some cache setting in KB.
**vsync=true # sync on vertical**
autosync=30 # checks every 30 secs to make sure audio is in sync (adjust as needed)
framedrop=true # drop a frame to sync audio if behind
brightness=1 # adjust brightness
afm=hwac3 # output to spdif if ac3 or DTS
ao=alsa # sound driver to use
stop-xscreensaver=true # don't have screensaver pop up during movie

Also, you can stack these when running different types of media,

vo=xvmc,xv,gl # try XvMC first, then xv, etc.
ac=hwac3,hwdts,pcm,a52 # try ac3 to spdif, dts to spdif, raw pcm, lastly software mpeg decoding

Here is docs that explains these options in detail:
[http://www.mplayerhq.hu/DOCS/HTML/en/index.html](http://www.mplayerhq.hu/DOCS/HTML/en/index.html)

---

### Post by elustran on 2008-06-05
> **JarrettV said:**
> I've also been researching this.  It appears that Intel will be the first to support quality video in Linux as they are working on DRI2.  Anyway, the best [explanation on poor video quality in linux]("http://lwn.net/Articles/277136/") that I have found is here:

And, here are some potential solutions I have yet to try.
I'll have to try some of those when I'm feeling more enterprising... If you get to any of them first, could you post your results?

Also, has anybody figured out why the problems cropped up in Hardy?  Is it because there's something implemented differently between compiz and beryl? I understand you could have video and effects before - I never tried to get beryl working, so I have any experience with the matter.

---

### Post by JarrettV on 2008-06-09
I tried the mplayer settings and they did not seem to work.  I also tried a bunch of different settings in the xorg.conf file that I found in the [compiz thread]("http://forum.compiz-fusion.org/showthread.php?t=6794")(see page 45).  Nothing I try will get rid of the tearing video.  The best I can get is one single but constant tear about 8% down from the top.  This tear is not visible when watching 2.35:1 aspect movies.

Note I am trying with latest ati drivers 8.5 (8.49.7).  Also I am not using compiz.

At this point I am debating whether to try a geforce 8600GTS that I have or go back to vista. :roll: Damn you linux video quality. ](*,)

---

### Post by revolutio on 2008-06-13
I'm really curious now as to whether there are any hardware combinations that don't have this issue.  I can't think that if this was a chronic and universal problem there would be so little talk about it.

Is there anyone who has no issues with video playback while using Compiz?  If so, what hardware and drivers are you running?

---

### Post by executive on 2008-06-14
same problem here with choppy video in full screen on a Dell E1505/X1400. in regular window mode it plays great, but once in full screen, pixelated and laggy.. :(

---

### Post by JarrettV on 2008-06-17
Found an existing bug for the video tearing with ATI here:
[URL="http://ati.cchtml.com/show_bug.cgi?id=1085"]
Unofficial ATI Linux Driver Bugzilla Bug 1085[/URL]

---

### Post by johnlvs2run on 2008-06-17
> **muteXe said:**
> Nvidia 7800GTX here, and i got the same problem. Sucks :(

Same issue here.

---

### Post by Victormd on 2008-06-17
Started reading through the thread ans noticed a bunch of ATI users with issues but I've been having really crappy playback on nvidia and apparently, no fix?!

---

### Post by JarrettV on 2008-06-20
Found another great explination about the poor video quality and video tearing situation on linux using ATI:
[AMD Catalyst 8.6 Linux Driver Tearing Flickering Video]("http://www.phoronix.com/forums/showpost.php?p=35872&postcount=63")
> [Quote]
Originally Posted by Dandel View Post
The flickering video bug occurs when one has compiz fusion enabled the screen area where the video/3d parts are supposed to be rendered flickers between the image to be rendered and some other color, which is usually black. it looks somewhat like one has a old style TV set with bad reception.
Let's set the record slightly straighter about this bug.

Compiz is a compositor, it tells applications to render offscreen and then composites (blends, combines, whatever) into an image and presents it to the screen. The application is still told where it is on the screen, it is just that most 2D clients render to the offscreen pixmap.

The direct clients of the current driver (OpenGL and Video) render directly to the framebuffer (the screen). Compiz (as an OpenGL application) renders to the framebuffer. The "flickering" that people are talking about is actually two openGL clients rendering to the same part of the screen.

The COMPOSITE extension is an all or nothing option, the compositor assumes that all windows are compositable, and there is no way for the driver to say that the window shouldn't be composited. I am hoping that COMPOSITE can be extended to provide hints to the compositor that for whatever reason (overlay, etc), an application can't render offscreen and so the compositor should provide all the details needed for the rendering to occur properly. Currently we can't do that.

To solve this completely, *ALL* clients must support the COMPOSITE extension fully. The NVidia drivers support this currently, some xV clients support this as well. None of the DRI based 3D drivers support this. DRI2 is adding infrastructure to support COMPOSITE fully (through the so-called Redirected Direct Rendering), but that is at least 6-9 months away from the next XOrg release.

I am not providing a timeline as to when full COMPOSITE support will be added to the driver, but I wanted to allow people to understand what is happening rather than making unfounded comments.

Other compositors (like metacity) do not try to re-render the whole screen with OpenGL, and so the behaviour is a lot less noticable - but you can still see that the OpenGL applications are not given clipping information, so will overwrite windows that pass infront of the application.

Regards,Matthew[/Quote]

---

### Post by shrndegruv on 2008-06-25
I have the same problem.  a lot of posts say there is nothing that can be done about it.  why did compiz + video playback work in gutsy then?

---

### Post by lifve on 2008-06-25
same problem here, someone fix this please !!!

---

### Post by nandotron on 2008-06-28
Hi,

not sure what this means, but the only success i've had with playing video properly in ubuntu hardy is to switch off desktop effects and run the video in elisa media centre.  Video quality is as it should be, with the exception of some tearing.

even when i turn off effects, video quality is very poor in vlc, totem and kaffeine, albeit different in each (vlc is very pixelated, while totem has horizontal lines).

I would love to be able to improve the quality in any of these players as elisa is not very convenient to use, and, given that i know for sure now that good video playback is possible in ubuntu hardy with an ati radeon x1400, is it possible that i need to alter the codecs or codec settings to achieve this?  Also gusty had good quality video even with desktop effects turned on, so i'm curious as to what changed in hardy.

if anyone has any advice, it would be very appreciated!

---

### Post by beckettwarren on 2008-07-02
I had the exact same problem with the terrible video playback in Hardy after being fine in Gutsy. 
Tried almost everything that was suggested, but was still running into the same problems as a lot of other folks.
Finally followed the steps in this guide: [http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)

And everything is finally cleared up. It's just installing the newest drivers from ATI and a few xorg.conf settings, but it was the one thing that finally got my video looking good.

---

### Post by markbuntu on 2008-07-02
If you followed the suggestions in the link beckettwarren give above and you have a newer card and a fairly fast cpu you can try the TexturedVideo "off" option and still run compiz and have non-flickering windowed video playback, except with xine. xine still flickers in windowed mode but plays Ok in full screen. gstreamer apps play fine in both windowed mode and full screen. 

I have tried this out with totem, mplayer, vlc, and miro (no xine windowed playback but gstreamer works great) with my Radeon HD3650 and AMD3800+ single core cpu.

---

### Post by lifve on 2008-07-04
> **beckettwarren said:**
> I had the exact same problem with the terrible video playback in Hardy after being fine in Gutsy. 
Tried almost everything that was suggested, but was still running into the same problems as a lot of other folks.
Finally followed the steps in this guide: [http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)

And everything is finally cleared up. It's just installing the newest drivers from ATI and a few xorg.conf settings, but it was the one thing that finally got my video looking good.

T_T looks difficult, and i'm not sure the result is good. i use radeon xpress200m on amd turion64. i ever try changing some option for aticonfig, but the result not good, my cpu always getting higher works, and the video still bad. in the end i choose stop the compiz and not using ati driver, and everything works well.

---

### Post by ds3 on 2008-07-08
I'm having a similar problem, only I get the choppy, pixelated full-screen video in VLC and Totem but not MPlayer (which plays in fullscreen beautifully). The CPU usage doesn't seem excessive in any of the cases. 
I have a Dell Latitude D531 with an ATI Radeon X1270 display using the fglrx proprietary driver (listed as the X1200 series). I'm using 64bit Hardy upgraded from Gutsy, but I don't know if this problem existed in Gutsy because I only had it a few weeks before Hardy came out. The machine is dual boot with Windows XP and I have no problems with the video in Windows. Xserver-xgl is not installed (although I tried installing it and uninstalling it based on some of the posts here, but it didn't change anything). 
MPlayer (both the plug-in and standalone) did not show any video until I changed the settings (separately in the two cases) to opengl, but when I set VLC to opengl it crashes when it tries to open any video.
I have tried a number of the solutions suggested, including editing xorg.conf and every option for a video device in VLC and haven't had any luck. I also shut off the "drop frames" setting but it didn't help either. This is particularly frustrating because I use VLC for DVD playback since MPlayer does not provide access to the DVD menus and sometimes will launch with commentaries running.
Any suggestions are welcome!

---

### Post by elustran on 2008-07-08
> **lifve said:**
> T_T looks difficult, and i'm not sure the result is good. i use radeon xpress200m on amd turion64. i ever try changing some option for aticonfig, but the result not good, my cpu always getting higher works, and the video still bad. in the end i choose stop the compiz and not using ati driver, and everything works well.
I'm happy enough with Compiz not working, but I like being able to use the desktop wall because some windows are too big for my low resolution.  I've been too busy to want to mess with it yet, but if it's going to cause other video problems, I don't think I'll bother that fix that's on the Compiz site.

---

### Post by ds3 on 2008-07-08
Okay, now everything is working for me, but I have no idea why. After trying pretty much every recommendation without any luck, today, after the system has restarted both Totem and VLC are working perfectly fine in fullscreen mode just like MPlayer already was. The odd thing is that I removed every change I'd made since they didn't seem to help. My only (not very good) guess is that when I went through the xorg.conf changes and then followed the suggestion here: 
[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794) 
to implement them using 
aticonfig --input=/etc/X11/xorg.conf --tls=1 
that something reset on reboot, but I have no idea what or why or how, especially since I restored xorg.conf to it's original state before shutting down since nothing seemed to have helped.

---

### Post by NotTheMessiah on 2008-07-09
wow! Video + ATI + Compiz is an intense mission! 

Like others i've tried various things with settings(xorg, gstreamer etc)
but i couldn't see any significant improvement. So I've decided to shut down compiz since i don't think that us users can do anything more then bump from one thing to another in a dark room.

So now i have no compiz and video and D-TV playback working with the occasional tear here and there(this i can live with).

We just have to wait i guess.Oh and i have the ATI driver 8.50.3 and a Sapphire HD 4850 on hardy.

---

### Post by johnlvs2run on 2008-08-03
Be sure you're using the latest driver from Nvidia
[http://www.nvidia.com/object/linux_display_ia32_177.13.html](http://www.nvidia.com/object/linux_display_ia32_177.13.html)

Thanks to Jualin for the part in bold, the resolution is finally staying put.

sudo apt-get install build-essential libxft-dev
alt-cntr-F1
sudo /etc/init.d/gdm/ stop
cd /home/loginname/Desktop/downloads/
sudo sh NVIDIA-Linux-x86-177.13-pkg1.run
yes, ok, yes, ok
cd ... (optional)
cntr-alt-del ... (or sudo /etc/init.d/gdm restart)

> applications > accessories > terminal
**sudo nvidia-settings**
This didn't work from the command prompt previously.

back to the desktop 
> applications > system tools > nvidia X server settings
> X server display configuration 
> "tab" to resolution
> "space bar" to open
> "arrow" to 1280x800 or whatever you want 
> apply > save to X > quit.

---

### Post by rdfi on 2008-08-21
I also have the choppy, very low quality video playback problems everyone is talking about.

I have a ATI Radeon 9600XT.

When I have the "ATI accelarated graphics driver" enabled (System->Administration->Hardware drivers), the desktop effects from compiz work really well, everything is fast. 

Even flash movies look better. I use Flash v10 beta. I tried flash v9 plugin in firefox without the ATI driver, and it was really bad, so I tried the v10 beta plugin and it got decent. And pretty good with the ati driver enabled (I don't know how flash v9 plugin works with the ati driver enabled, never tried it...).

Video playback on the other hand is very bad. Full of aliasing and very choppy. In full screen though, it is just the aliasing, it stops being choppy.

When I disable the ATI driver from System->Administration->Hardware drivers, I get good video playback and I can still use compiz pretty well.

The thing that annoys me most about not being able to use the ATI driver is the flash video quality, especially in web pages that have several flash movies showing.

I can live without compiz, but without flash movies and video quality no way...

---

### Post by ubuntubrian on 2008-08-25
Uninstalled Xserver-xgl and video, scrolling, everything that sucked is better!
Don't need no stinking desktop effects!:guitar:

---

### Post by jmitnik on 2008-08-29
> **rdfi said:**
> I also have the choppy, very low quality video playback problems everyone is talking about.

I have a ATI Radeon 9600XT.

When I have the "ATI accelarated graphics driver" enabled (System->Administration->Hardware drivers), the desktop effects from compiz work really well, everything is fast. 

Even flash movies look better. I use Flash v10 beta. I tried flash v9 plugin in firefox without the ATI driver, and it was really bad, so I tried the v10 beta plugin and it got decent. And pretty good with the ati driver enabled (I don't know how flash v9 plugin works with the ati driver enabled, never tried it...).

Video playback on the other hand is very bad. Full of aliasing and very choppy. In full screen though, it is just the aliasing, it stops being choppy.

When I disable the ATI driver from System->Administration->Hardware drivers, I get good video playback and I can still use compiz pretty well.

The thing that annoys me most about not being able to use the ATI driver is the flash video quality, especially in web pages that have several flash movies showing.

I can live without compiz, but without flash movies and video quality no way...

I have ATI 1600 and fglrx installed. I have also choppy video playback. Still there is no solution to this?

---

### Post by bedjo on 2008-08-30
I had similar experience and i think, i fix it by turning off "video playback" in compiz setting. or compiling alsa sound driver again. (????)

---

### Post by jmitnik on 2008-08-30
> **bedjo said:**
> I had similar experience and i think, i fix it by turning off "video playback" in compiz setting. or compiling alsa sound driver again. (????)

I have removed compiz from my machine. Regarding also .. I am not sure ... what could be the connection between alsa sound architecture and the video playback? Anyway I am using OSS not Alsa...

---

### Post by kamion on 2008-09-01
Hi,
I had the problem with choppy video (only in avi from my Canon and 3gp files) in MPlayer on Hardy (on Totem and VLC everything was OK). When I changed audio from pulse to alsa the problem disappeared. I don't use compiz.

---

### Post by Gallardo Spyder on 2008-09-01
Well as an experienced Linux User - I also have this problem with a new Quad Core (2.4ghz) and 2 dual output PCI FireGL 3600 cards.

It seems as if it is a ATI Kernel problem (IMO).  I just downloaded and complied the newset ATI drivers and they have not yet solved the tearing issue.

However in my experimentation of the issue.  I have found a way to play video without the tearing issue and good quality as well.  I have Miro installed and have been using that instead of mplayer or other with composite on and it is working fine.

I was just turing off composite when watching video - but that was a pain so tried a few different players and Miro works every time.

---

### Post by rdfi on 2008-09-01
What is composite?

---

### Post by Gallardo Spyder on 2008-09-02
Compiz Fusion

---

### Post by dharkhan on 2008-09-23
I am not using compiz, but had the same problem. I've tried almost every suggestion I could find, still no luck - choppy video with the restricted drivers.  It wasn't until yesterday that I identified the culprit - KasBar with thumbnails enabled !!! Disabled it and video playback is smooth as it was before. :)  I guess it's something like blocking I/O call

---

### Post by rdfi on 2008-09-23
> **dharkhan said:**
> I am not using compiz, but had the same problem. I've tried almost every suggestion I could find, still no luck - choppy video with the restricted drivers.  It wasn't until yesterday that I identified the culprit - KasBar with thumbnails enabled !!! Disabled it and video playback is smooth as it was before. :)  I guess it's something like blocking I/O call

Hi,

how do I do that? disable KasBar? disable thumbnails in KasBar? what is KasBar?

Thks,
Rui

---

### Post by maino82 on 2008-10-03
I have a quad core machine with an 8800 GTS and a dual core laptop with a ATI mobile 1100 and both experience playback problems with compiz enabled. The 8800 only has problems when I have compiz enabled, the 1100 has problems even when compiz is disabled and the restricted driver is enabled. If I disable the driver as well, the problem goes away. The 8800 doesn't have problems when the driver only is enabled, leading me to believe that there are 2 problems... one with compiz and one with the ATI restricted driver.

---

### Post by qns8dn3 on 2008-10-12
I had the same pixelated movie problem on Hardy Heron. (xserver-xgl is not installed.) Disabling restricted ATI graphics driver solved the problem.


My system state before disabling ATI accelerated graphics driver from Hardware Drivers :
[list][*]compiz effect is fine.
[*]video fullscreen is pixelated in both totem movie player and vlc. (compare the first attachment screenshot which is not fullscreen and the second screenshot which is fullscreen and pixelated).
[*]fglrxinfo returns ```
display: :0.0 screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon 9550 / X1050 Series
OpenGL version string: 1.4 (2.1.7412 Release)
```
[/list]

My system state after disableing ATI driver :
[list][*]compiz effect is still fine
[*]video in fullscreen is not pixelated.
[*]But now I can't take screenshot of movie thru PrtScreen, screenshot gives black blank on movie playing area. Pressing ctrl-N (compiz invert effect) makes movie playing area blank.
[*]fglrxinfo returns nothing, i think fglrxinfo program is removed while disabling the driver.[/list]

---

### Post by xjgnsdof on 2008-10-16
I have two 4850s in CrossfireX, so I decided to manually update the drivers to 8.10 that were released on 10/15/08. I still get video flicker when I have Compiz enabled.

---

### Post by BMWDriver on 2008-10-16
(Edit: wrong problem.)

---

### Post by sirclaudio on 2008-10-18
I have a X2300 and also that flicker in video playback when compiz is enabled (using latest version of the AMD/ATI drivers). But, if i set the output as X11, instead of Xv or OpenGL (in gstreamer-properties and in vlc, my only two players), the problem goes away.
Try it.

---

### Post by xflyboy on 2008-10-18
Hi all.
 Same problem here. Inspiron 6400 - ATI x1400.

max@Inspiron:~$ fgl_glxgears 
Using GLX_SGIX_pbuffer
2317 frames in 5.0 seconds = 463.400 FPS
2452 frames in 5.0 seconds = 490.400 FPS

max@Inspiron:~$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.1.7659 Release

Problem appered when EnvyNG were installed. ATI drivers were not used before that.
At Multimedia system selector, on autodetect - Choppy wideo
If "X Window System (No Xv)" Video Output plugin selected, then video goes well.
Suggestions?
Thanks.

---

### Post by tarfito on 2008-11-02
i have been having the same problem, for some reason Elisa media center plays video full screen with no lag or choppiness

---

### Post by alwayshere on 2008-11-02
try compiz switch  [http://forlong.blogage.de/entries/pages/Compiz-Switch](http://forlong.blogage.de/entries/pages/Compiz-Switch)

i   use it for gaming etc without it graphics are all glicthy

---

### Post by johnlvs2run on 2008-11-18
It is sad to see so many still struggling with the graphics.
I went through endless fixes with ubuntu, none of which either lasted or worked at all.
Then I ran mint for a couple of months, which is similar to ubuntu but has more options and less problems.

A couple of months ago I got a sabayon dvd from ebay and finally installed it yesterday.
The install was flawless, the screen resolution is PERFECT, the video is perfect, no hassles, VIOLA!!!!!!

All this time, the biostar tf8200 mobo and nvidia grapics should have been fine, the issue was ubuntu.
My recommendation is to get a sabayon dvd, and use sabayon for your os.

---

