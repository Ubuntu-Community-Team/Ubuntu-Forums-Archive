---
title: "Overlay on TV-Out stretched (fglrx 8.27.10 &amp; 8.28.8)"
date: 2006-09-03
forum: Multimedia &amp; Video
---

### Post by Nicksha on 2006-09-03
Since version 8.27.10, fglrx has an option to use overscan on TV, and I really wanted that. However, after installing the new fglrx driver with ATI's installer, xv picture is stretched, and it only shows the upper 2/3 of the video. This only happens when the overlay is on the TV (aticonfig --overlay-on=1), when it's on the monitor, everything is fine. The installation of the driver itself went fine, 3D acceleration is working, and there even wasn't that "API error" problem (I've got RADEON 9250). Oh, and I'm using PAL-G.

I read somewhere that people had a problem like this ever since the 8.20.* version, but that's not the case for me; Dapper's version (8.25.18) works fine. That was filed as a bug [309]("http://ati.cchtml.com/show_bug.cgi?id=309").

Does anyone else have this problem, and has anyone found some kind of workaround?

---

### Post by Nicksha on 2006-09-15
Sorry, I thought I found the solution, but it's not working again.

---

### Post by ofanite on 2006-10-07
Just thought I'd add a "doesn't work for me" post here as well.

I'm pretty good at hacking this stuff, too.  I think this driver is just buggered, especially when using TV-Out.  Par for the course for ATI, but I would love to get this working if possible.  Here's an interesting line:```
(II) fglrx(0): Largest offscreen area available: 768 x 7705
```I wonder if this has something to do with the problem.

](*,)

---

### Post by smartperson on 2006-10-09
*sigh*

I am having this exact same problem, and it is infuriating my dormmates as our MythTV box is useless like this.

If I install an older version of fglrx will overlay work properly?  I don't care about 3D acceleration at all as I have a RADEON 9100 IGP.

---

### Post by Nicksha on 2006-10-09
Yes, but you'll have to try them out to see which one works for you. For me, Dapper's default version of fglrx (8.25.18 ) works fine, and the issue only appears with the 8.27.10 & 8.28.8 versions.

However, other ATI users have reported that this issue has bugged them ever since 8.22.5 ([http://ati.cchtml.com/show_bug.cgi?id=309]("http://ati.cchtml.com/show_bug.cgi?id=309")), and they had to revert to 8.20.8 version.

---

### Post by sparkplug on 2006-10-21
Hi,I have a 9250 too,but it has the same problem,even with the dapper default driver(fglrx 8.25.18),can you post your xorg.conf at here ,thank you and sorry for my poor English,:p

---

### Post by Nicksha on 2006-10-23
Sure. It's a bit of a mess really, I think I've been using the same one since Hoary, just adding and commenting stuff out along the way. It's in the attachment.

---

### Post by sparkplug on 2006-10-23
Thank you,I will try it .

---

### Post by justynbutler on 2006-10-24
Another me too post. I'm having exactly the same problem, although it is in fact on my FC5 box (I use Fedora and Ubuntu on different machines).

It's got to be a driver problem because it worked fine using older drivers, then when I upgraded I got the problem with stretched overlay as described, whether using the old xorg.conf or building a new one.

I went through the feedback process for the Linux drivers on the ATI website and I recommend everyone else who has this problem do the same. The more feedback they get about this bug, the sooner they're likely to fix it.

Go here to leave feedback, click "Drivers and software", then "Linux display drivers and software", then "Linux driver feedback" at the bottom of the page:
[https://support.ati.com/ics/support/default.asp?deptID=894](https://support.ati.com/ics/support/default.asp?deptID=894)

Justyn

---

### Post by justynbutler on 2006-11-01
The new ATI 8.30.3 driver is just out, and according the newsfeed:

ISSUES RESOLVED: (1) Users with X Server X.org 7.1 can now play video using XV. The ATI AVIVO Video adaptor is now present. 

I haven't tried it yet, but it looks promising! Apparently it doesn't support my hardware (Mobility Radeon 9200) because they stopped with 8.28.8 but I'm keeping my fingers crossed.

Justyn

---

### Post by pinf on 2006-11-02
> **justynbutler said:**
> The new ATI 8.30.3 driver is just out, and according the newsfeed:

ISSUES RESOLVED: (1) Users with X Server X.org 7.1 can now play video using XV. The ATI AVIVO Video adaptor is now present. 

Justyn

Same bug still exist in 8.30.3 with Xv (Option "VideoOverlay" "on"). You can try using this AVIVO feature instead (Option "TexturedVideo" "on").
Not same quality as Xv used to be though. Sad that ATI doesn't fix bugs, rather just brings new features and cuts support for "older" hardware.

---

### Post by mirak63 on 2006-11-02
I experienced this bug and for me it happened only when I switched the overlay from monitor to tv on the fly, when X was already running.

```
Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 AP [Radeon 9600]"
	Driver      "fglrx"
	Option	    "UseFBDev" "false"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "TVFormat" "NTSC-M"
	Option	    "ForceMonitors" "crt1,tv"
	Option	    "NoTV" "no"
	Option	    "OverlayOnCRTC2" "1"
	Option	    "DesktopSetup" "clone"
	Option	    "TVHSizeAdj"   "0"
	Option      "TVVSizeAdj"   "0"
	Option      "TVHPosAdj"    "0"
	Option      "TVVPosAdj"    "0"
	Option      "TVHStartAdj"  "0"
	Option      "TVColorAdj"   "0"

	BusID       "PCI:3:0:0"
EndSection
```

```
	Option	    "OverlayOnCRTC2" "1"
```

you set it to 1 for overlay on monitor and 0 for TV.

---

### Post by belly917 on 2006-11-03
Add me to the list of people experiencing this problem

If I disable Video Overlay in my xorg.conf, the video appears correctly on my tv-out, but stutters because my CPU can't handle it.  Obviously I want to be using the video overlay because this is a mythtv box connected to my TV.

I'm using the 8.30.3 fglrx drivers on an Ubuntu Edgy Server (Mythtv runs in ratpoison)

I should point out that the output of fglrxinfo states that I'm still using mesa drivers.. so this could be adding to the problem.  but Video overlay works correctly (proper video acceleration) when connected to a LCD monitor instead of my tv via s-video.

---

### Post by resolost on 2006-11-05
I am also looking for a solution for this... i have not been able to find a out completely if it is worth upgrading to the newest version of the drivers... any advice on how to get the best picture would be much appreciated...

---

### Post by belly917 on 2006-11-14
bump

(I've seen alot of duplicate posts about this, I figured bumping this would help others to find it easier)

*edit*******
I also tried upgrading to the 8.31.5 fglrx drivers released yesterday (11.15.2006) but that made no difference

---

### Post by jarjar on 2006-12-04
I have an ATI radeon 9550 and I'm using it with MythTv. It works otherwise well, but when I start the MythTv TV Playback the screensize is too big. Videos and everything else seems just ok. I only have TV connected to the computer. 

Do you think this could be caused by ati drivers? When I change the videoOverlay=opengl, the TV playback is the right size, but it stutters so much that it's unviewable. ](*,)

---

### Post by bremedios on 2006-12-10
I've gotten this to work with the 31.5 driver using the Textured Video option.

The new problem that I have is there is a very green hue to everyone (people have green skin.)  This occurs when watching TV in Myth but not when using mplayer with the opengl output.

The problem did not exist without TexturedVideo and with VideoOverlay turned both on and off.

Does anyone have any ideas?  I could manually mess with the color in MythTV but I would think that it should just work.

---

### Post by jarjar on 2006-12-12
I managed to install the latest drivers and try the TexturedVideo option, and I have the exact same problem. Where can I change the color manually? At this point I just don't care anymore as long is I get it working somehow :) ... Also, I noticed that in MythTv the small preview (in the *manage recordings*) shows correct colors as well as playing the recordings in Xine. 

Here's the errorlog from viewing TV, in case someone is able to tell what's going on here:

> 
2006-12-12 16:21:03.423 TV: Attempting to change from None to 
WatchingLiveTV
2006-12-12 16:21:03.424 Using protocol version 31
2006-12-12 16:21:03.592 DPMS Deactivated 
2006-12-12 16:21:03.632 NVP: Disabling Audio, params(-1,2,44100)
2006-12-12 16:21:03.674 VideoOutputXv: XvMCTex: Init failed
2006-12-12 16:21:03.674 VideoOutputXv: XVideo Adaptor Name: 'ATI Radeon 
AVIVO Video'
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  141
  Minor opcode:  14
  Resource id:  0x194
2006-12-12 16:21:04.375 TV: Changing from None to WatchingLiveTV
2006-12-12 16:21:04.394 Using realtime priority.
2006-12-12 16:21:04.458 Video timing method: USleep with busy wait
[mpegts @ 0xb732e500]Parser not found for Codec Id: 94211 !
[mpegts @ 0xb732e500]Parser not found for Codec Id: 94212 !
[mpegts @ 0xb732e500]Parser not found for Codec Id: 94212 !
[mpegts @ 0xb732e500]Parser not found for Codec Id: 94212 !
[mpegts @ 0xb732e500]Parser not found for Codec Id: 94212 !
[mpegts @ 0xb732e500]Parser not found for Codec Id: 94212 !
2006-12-12 16:21:05.693 VideoOutputXv: XvMCTex: Init failed
2006-12-12 16:21:05.695 VideoOutputXv: XVideo Adaptor Name: 'ATI Radeon 
AVIVO Video'
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  141
  Minor opcode:  14
  Resource id:  0x194
2006-12-12 16:21:06.122 AFD: Opened codec 0x865bd10, id(MPEG2VIDEO) 
type(Video)
2006-12-12 16:21:06.122 AFD: Opened codec 0x93fa9b0, id(MP3) type(Audio)
2006-12-12 16:21:06.174 Opening OSS audio device '/dev/dsp'.
2006-12-12 16:21:06.186 NVP: Enabling Audio
2006-12-12 16:21:10.522 msg: On same multiplex...
2006-12-12 16:21:10.634 NVP: prebuffering pause
2006-12-12 16:21:12.799 NVP: Prebuffer wait timed out 10 times.
2006-12-12 16:21:14.006 msg: On same multiplex...
2006-12-12 16:21:14.243 
RingBuf(/home/mythtv/recordings/1506_20061212162110.mpg) Error: Invalid 
file descriptor in 'safe_read()'
2006-12-12 16:21:14.975 NVP: Prebuffer wait timed out 10 times.
2006-12-12 16:21:17.135 NVP: Prebuffer wait timed out 10 times.
2006-12-12 16:21:17.384 
RingBuf(/home/mythtv/recordings/1506_20061212162110.mpg): Invalid file 
(fd -1) when opening '/home/mythtv/recordings/1506_20061212162110.mpg'.
2006-12-12 16:21:17.384 NVP, Error: JumpToProgram's OpenFile failed.
2006-12-12 16:21:17.384 NVP, Error: Unknown error, exiting decoder
2006-12-12 16:21:17.385 TV: Attempting to change from WatchingLiveTV to 
None
2006-12-12 16:21:18.441 TV: Changing from WatchingLiveTV to None
2006-12-12 16:21:18.444 DPMS Reactivated.


---

### Post by jarjar on 2006-12-12
Take a look at here: 

[http://www.mythtvtalk.com/forum/viewtopic.php?t=4031&highlight=playback+stops]("http://www.mythtvtalk.com/forum/viewtopic.php?t=4031&highlight=playback+stops")

:D

---

### Post by Jabone on 2006-12-17
I got tv-out working with texturedvideo option. 
Now video is showing in both monitor and tv but the picture is blue. 
Has anybody else had same problems. 
With opengl picture is like it should be, but it's jerky and losts frames. 

Is there any solution to this?

- Jabone

---

### Post by mirak63 on 2006-12-17
I found a way to to not have stretched overlay, or in fact understood when it happened.

It happens when you only use TV, for exemple when no monitor is connected.
So the solution is to force the radeon to act like if a monitor is plugued by forcing it.

```
	Option	    "ForceMonitors" "crt1,tv"
	Option	    "NoTV" "no"
	Option	    "OverlayOnCRTC2" "1"
	Option	    "DesktopSetup" "clone"
```
and enable overlay on tv which is secondary.
I am not sure using clone or mirror mode makes a différence in this case, however when in clone or mirror overscan control options have no effects.
Overscan option allow to change screen size and position.

there is really a bug because in single desktopsetup mode overlay is stretched on tv.

---

### Post by jarjar on 2006-12-18
You need to recompile Myth: 

> I believe the bug applies to all ATI RADEON X cards and myth needs to be recomplied with USE_ATI_PROPRIETARY_DRIVER_XVIDEO_HACK enabled. However, this may negatively effect other cards.

As stated here: [link]("https://launchpad.net/distros/ubuntu/+source/mythtv/+bug/73102")

Hopefully this will be an option in Myth in the future. I haven't tried compiling Myth yet, but I suppose I have to try it out soon.

---

### Post by jarjar on 2006-12-19
> **mirak63 said:**
> I found a way to to not have stretched overlay, or in fact understood when it happened.

It happens when you only use TV, for exemple when no monitor is connected.
So the solution is to force the radeon to act like if a monitor is plugued by forcing it.

```
	Option	    "ForceMonitors" "crt1,tv"
	Option	    "NoTV" "no"
	Option	    "OverlayOnCRTC2" "1"
	Option	    "DesktopSetup" "clone"
```
and enable overlay on tv which is secondary.
I am not sure using clone or mirror mode makes a différence in this case, however when in clone or mirror overscan control options have no effects.
Overscan option allow to change screen size and position.

there is really a bug because in single desktopsetup mode overlay is stretched on tv.

In my case, this just resulted in Floating point exception when trying to start MythTv. I think this is because the gui uses OpenGL or something. Are the quoted options the only ones to add to the xorg.conf? Thanks.

---

### Post by Nicksha on 2006-12-22
I haven't been able to find any solution that would work for me, but I've noticed that there are solutions that work for other people, like the one mirak63 posted above. Maybe it has to do with which card you actually have (mine is Radeon 9250). So I've been using the gl output in mplayer and xine, which has those tearing artifacts...

But it was mirak63's post that gave me an idea. He said:
> I am not sure using clone or mirror mode makes a différence in this case
and that reminded me that I have never tried the mirror mode. It drives your monitor at the same display resolution and refresh rate as the TV, so it didn't sound useful for other than watching stuff on TV. But the thing that I forgot is that you can dynamically switch monitors on and off, and if you switch the TV off, you can choose any resolution and refresh rate for your monitor, just like with clone mode. And, in mirror mode, when the TV is on, the annoying xv bug doesn't appear! That's probably because, in mirror mode, you don't switch overlays from one screen to another - they share the same one. 

To make things more convenient, I've made two shell scripts for switching TV on and off, and doing all the side stuff, like changing the resolution. I've put them in the ~/bin folder, and added a couple of icons to my panel. It looks like this:

[IMG]http://ubuntuforums.org/gallery/data/500/screenshot199.png[/IMG]

The content of the scripts is:
tvout-on
```
#!/bin/sh
xrandr -s 2
aticonfig --enable-monitor=nocrt1,tv --tv-format-type=PAL-G --tv-overscan=on --e
ffective=now
aticonfig --enable-monitor=crt1,tv

```

tvout-off
```
#!/bin/sh
aticonfig --enable-monitor=crt1,notv --effective=now
xrandr -s 0

```

The xrandr command changes the resolution, and the number after the -s option is something you find by typing only "xrandr" in the terminal. That will give you the list of screen resolutions with corresponding numbers. For tv-on, it shouldn't be greater than 1024x768. If you're wondering why I turn the monitor off and then on in the tvout-on script, it's because aticonfig won't change the display format to PAL-G, unless the monitor is switched off first. 

Also, obviously, in the xorg.conf file, change the "DesktopSetup" option from clone to mirror. The "OverlayOnCRTC2" option is not needed. I've noticed the corruption of the display after switching the TV off, and changing the monitor resolution to a higher one. This only happens if I log in while the TV is connected, so I don't do that. Maybe some of the ForceMonitors or the NoTV options might work. I didn't try that yet.

Hope this helps to someone else. I know how frustrating this bug is (I did start this thread:) ), and especially now, when you can't use the older version of the fglrx driver, because of the new Xorg version in Edgy. Not to mention that Radeon 9250 is no longer supported in the newer versions of the driver. Oh, and thank you mirak63, for the insight.

---

### Post by mirak63 on 2006-12-23
> **jarjar said:**
> In my case, this just resulted in Floating point exception when trying to start MythTv. I think this is because the gui uses OpenGL or something. Are the quoted options the only ones to add to the xorg.conf? Thanks.

Guss what, I have this same error now in xine !!!
I think this came with kernel updates probably.
I am 100% sure I didn't had this problem with edgy at some point.
2 weeks ago it was ok.
](*,)

---

### Post by Tschaeck on 2006-12-30
i am having the same problem with 8.28.8

i tried different xorg.conf configurations and the 2 solutions above but had no luck.

i hope there will be a solution working for me in the future.

---

### Post by jarjar on 2007-01-03
This (blue faces with ATI Xv) won't be fixed in MythTV, as I've found out in the forums / mail lists / the bugtracker. So all you can do is complain to ATI and hope they fix their drivers or compile MythTV with the ATI_PROPRIETARY_HACK. 

I've managed to compile the libmythtv with the hack enabled, but sadly even this didn't fix the problem. I'm currently working on figuring out how the hue stuff works in mythtv, so maybe I can finally get it working someday... Has anyone else tried compiling libmyth? Any ideas?

---

### Post by giorgosts on 2007-01-08
Tried all the options mentioned, all the fglrx releases for 1 1/2 year, also OpenSuSE, tv-out is cropped under VideoOverlay. My card is radeon 9600 AGP 256MB. With TexturedVideo enabled, cropping is gone but video is slower and sharpness, colors, contrast and blacks not so good. Also a big green line at the top. And big stability problems (computer freezes or reboots). All these disappear with Xv and TexturedVideo disabled. That said, I think the 8.32.5 release is a boost in performance and, unless the camera is panning madly, you forget that the video acceleration is off. I suspect that ATI is waiting for us to buy a flat-panel tv with DVI input so they don't have to fix their broken driver. Or maybe we buy an NVIDIA instead.

---

### Post by mirak63 on 2007-01-10
I am done with ATI cards TV OUT, I have built a VGA to RGB SCART cable, and with appropriate modelines, the TV is just like a monitor, and image quality is FAR better, image is as good as a sattelite set top box, or DVD player.
The fonts aren't blurred, image and fonts are sharp, colors are beautifull. :KS 

[http://www.idiots.org.uk/vga_rgb_scart/index.html](http://www.idiots.org.uk/vga_rgb_scart/index.html)

Only problem is I am forced to use open source driver, because bogus proprietary driver doesn't realise when Composite option is enabled on the modeline.
But I don't need 3D anyway, and who would complain to be forced to use proprietary driver anyway :mrgreen:

---

### Post by giorgosts on 2007-01-10
Well done  mirak63. For those of us less proficient in electronics (or generally less proficient), we can try the fglrx 8.33.6 release. Although the bug is not fixed, performance with VideoOverlay disabled has improved over the previous releases.

---

### Post by dobre on 2007-01-12
I have been having the same problem trying to get my tv out to work also.  Only the top 2/3 of the video shows on my tv.  I have mine set in a clone setup. I am using the Xv overlay.  When it is set to my monitor which is primary the videos show fine.  I tried to use the opengl overlay but when I try that I loose the screen after i login( which shows natilus and ect loading) and I also loose the top menu bar(with applications places system ect) and the task bar.  Hopefully someone can figure a way to get this to work, I know If i can I will let everyone know!

---

### Post by giorgosts on 2007-01-12
> **dobre said:**
> I have been having the same problem trying to get my tv out to work also.  Only the top 2/3 of the video shows on my tv.  I have mine set in a clone setup. I am using the Xv overlay.  When it is set to my monitor which is primary the videos show fine.  I tried to use the opengl overlay but when I try that I loose the screen after i login( which shows natilus and ect loading) and I also loose the top menu bar(with applications places system ect) and the task bar.  Hopefully someone can figure a way to get this to work, I know If i can I will let everyone know!

Yeah, ATI has to fix that first! Read previous posts and also [http://www.phoronix.net/forums/showthread.php?t=35](http://www.phoronix.net/forums/showthread.php?t=35) (That applies with Xv ovelay enabled). With TexturedVideo enabled the cropping is gone,  but performance is a little worse. The best I could do so far is remove the Overlay settings from xorg.conf and that (along with using the latest fgrx 8.33.6) is as good as it gets.

---

### Post by dobre on 2007-01-13
Well, adding the textured video option makes no change for me.  However, i found a work around for the meantime i suppose.  If i use mplayer -vo x11 I can watch video files on my tv no problem.  My next problem is that I have a dark band the scrolls up my tv every so often.  Any ideas on what that could be?

---

### Post by giorgosts on 2007-01-14
> **dobre said:**
> Well, adding the textured video option makes no change for me.  However, i found a work around for the meantime i suppose.  If i use mplayer -vo x11 I can watch video files on my tv no problem.  My next problem is that I have a dark band the scrolls up my tv every so often.  Any ideas on what that could be?

Thanks for the suggestion: It doesn't crop but it doesn't scale to fullscreen either. Any ideas? Sorry I can't think anything about your problem.

---

### Post by akschu on 2007-01-14
I don't use ubuntu (slackware for me) but I did find this thread helpful in resolving my issues so I thought I would post.

I got this all working with the following combination:

ATI 8.33.6 Drivers using this config:

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "UseFBDev" "false"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        Option      "TVFormat" "NTSC-M"
        Option      "TVOverscan" "on"
        Option      "ForceMonitors" "crt1,tv"
        Option      "DesktopSetup" "clone"
        Option      "OverlayOnCRTC2" "1"
        Option      "TexturedVideo" "on"
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]"
        Device     "aticonfig-Device[0]"
        Monitor    "aticonfig-Monitor[0]"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
                Modes    "1024x768"
        EndSubSection
EndSection

And Mythtv 0.20-fixes (from svn) compiled with USE_ATI_PROPRIETARY_DRIVER_XVIDEO_HACK.

Video looks very good and everything is smooth.

Hopefully this will help you guys.

schu

---

### Post by giorgosts on 2007-01-15
> **akschu said:**
> I don't use ubuntu (slackware for me) but I did find this thread helpful in resolving my issues so I thought I would post.

I got this all working with the following combination:

ATI 8.33.6 Drivers using this config:

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "UseFBDev" "false"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        Option      "TVFormat" "NTSC-M"
        Option      "TVOverscan" "on"
        Option      "ForceMonitors" "crt1,tv"
        Option      "DesktopSetup" "clone"
        Option      "OverlayOnCRTC2" "1"
        Option      "TexturedVideo" "on"
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]"
        Device     "aticonfig-Device[0]"
        Monitor    "aticonfig-Monitor[0]"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
                Modes    "1024x768"
        EndSubSection
EndSection

And Mythtv 0.20-fixes (from svn) compiled with USE_ATI_PROPRIETARY_DRIVER_XVIDEO_HACK.

Video looks very good and everything is smooth.

Hopefully this will help you guys.

schu

It's been known that enabling TexturedVideo stops the cropping, but you are not doing anything different than playing video using OpenGL, i.e. using the card's 3d pipe to render video. How does your performance compare with OpenGL rendering and when VideoOverlay is off? Can you work on one desktop and watch fullscreen video on the tv? (performancewise)


look at mine (also not cropping, xv disabled, dual head):

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    30.0 - 71.0
	VertRefresh  50.0 - 160.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[1]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Generic Video Card"
	Driver      "fglrx"
	Option	    "UseFBDev" "false"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Generic Video Card"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
	Depth     24
	Modes    "1024x768"
        EndSubSection

EndSection

Section "Screen"
	Identifier "aticonfig-Screen[1]"
	Device     "aticonfig-Device[1]"
	Monitor    "aticonfig-Monitor[1]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

---

### Post by akschu on 2007-01-15
I get this in the log when I use myth:

2007-01-15 08:28:47.360 VideoOutputXv: XvMCTex: Init failed
2007-01-15 08:28:47.361 VideoOutputXv: XVideo Adaptor Name: 'ATI Radeon AVIVO Video'

The second line lead me to believe that it was working with Xv.  At any rate the video is perfectly smooth, so this solution does work for me.

It looks better than my older Nvidia card (probably because of better TV out hardware).

schu

---

### Post by barney_1 on 2007-01-30
I also have the TV-Out stetched overlay problem.  I ready the treads about and see that there is a hack in the source.  The box I have the problem with is both my backend and a frontend.  If I compile the frontend from source will if effect any of the other fronts ends I run in the house?

Thanks!

---

### Post by barney_1 on 2007-01-31
I have fixed my problem with the stretched overlay:

Setup:
Ubuntu Edgy 6.10
Mythtv 0.20
fglrx from repositories - 8.28.8
AGP Video Card - ATI Technologies Inc Radeon RV250 If [Radeon 9000] (rev 01)

HOWTO:

1. Make sure you have fglrx installed.  I do not have dri running, it doesn't really matter to me.  I used [[COLOR="Blue"]this guide[/COLOR]]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide").

2. I read [[COLOR="Blue"]this bug post[/COLOR]]("https://launchpad.net/ubuntu/+source/mythtv/+bug/73102") and found that [[COLOR="Blue"]response 5[/COLOR]]("https://launchpad.net/ubuntu/+source/mythtv/+bug/73102/comments/5") had a re-compiled libmyth-0.20 deb file posted with it.  [[COLOR="Blue"]DirectDownload[/COLOR]]("http://librarian.launchpad.net/5597854/libmyth-0.20_0.20-0.2ubuntu2_i386.deb")

3. Save this file to your desktop, double click it.  I received a warning that this package was already installed, I choose to reinstall it.

4. Time to edit your /etc/X11/xorg.conf

I'm not an expert at this, here's what worked for me, I got most of it it from akschu in post #35 of this thread:

```
Section "Monitor"
        Identifier   "Visual Sensa"
        HorizSync    30.0 - 70.0
        VertRefresh  50.0 - 150.0
        Option      "DPMS"
EndSection

Section "Device"
############Following added from UbuntuForums.org - Run with Hacked libmyth####
        Identifier  "ATI Technologies, Inc. Radeon RV250 If [Radeon 9000 Pro]"
        Driver      "fglrx"
        Option      "UseFBDev" "false"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        Option      "TVFormat" "NTSC-M"
#      Option      "TVOverscan" "on"
        Option      "ForceMonitors" "crt1,tv"
        Option      "DesktopSetup" "mirror"
        Option      "OverlayOnCRTC2" "1"
        Option      "TexturedVideo" "on"
############End of custom libmyth addons#########################
        Option      "EnableMonitor" "crt1,tv"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "ATI Technologies, Inc. Radeon RV250 If [Radeon 9000 Pro]"
        Monitor    "Visual Sensa"
        DefaultDepth     24
        SubSection "Display"
                Depth     1
                Modes    "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     4
                Modes    "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     8
                Modes    "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     15
                Modes    "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     24
                Modes    "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "DRI"
        Mode         0666
EndSection

Section "Extensions"
        Option      "Composite" "0"
EndSection

```

Notice that I have commented the part that I added.  I changed things a little bit.  I need to have the desktopsetup turned to mirror or I couldn't see any video:
```
       Option      "DesktopSetup" "mirror"
```
I also found it important to add the enablemonitor setting at the end or X wouldn't start at all:
```
        Option      "EnableMonitor" "crt1,tv"
```

(Everything I use is already in the posting of my xorg.conf.  The two examples above are just to let you know why I used then, no need to add them again)

5. Disconnect your CRT Monitor, connect your S-Video out to the TV and reboot.  If all went well you should have a display on your monitor that plays video without the stretched effect.  

----

My next endeavor will be working with the overscan that I have commented out.  The TV picture doesn't quite take up the whole TV screen and I would like it to.

---

### Post by Tschaeck on 2007-01-31
> **barney_1 said:**
> 
2. I read [[COLOR="Blue"]this bug post[/COLOR]]("https://launchpad.net/ubuntu/+source/mythtv/+bug/73102") and found that [[COLOR="Blue"]response 5[/COLOR]]("https://launchpad.net/ubuntu/+source/mythtv/+bug/73102/comments/5") had a re-compiled libmyth-0.20 deb file posted with it.  [[COLOR="Blue"]DirectDownload[/COLOR]]("http://librarian.launchpad.net/5597854/libmyth-0.20_0.20-0.2ubuntu2_i386.deb")


i am always reading about fixes for mythtv. i am using vdr with xineliboutput. is there a fix for thas? something like compliling xine with USE_ATI_PROPRIETARY_DRIVER_XVIDEO_HACK?

---

### Post by posterberg on 2007-02-01
> **mirak63 said:**
> Guss what, I have this same error now in xine !!!
I think this came with kernel updates probably.
I am 100% sure I didn't had this problem with edgy at some point.
2 weeks ago it was ok.
](*,)

Me too... For me both mythfrontend, mythtv-setup and amarok crashes. It started happening after I changed from using ati driver to fglrx. I quite certain that it is the same problem.

Did anyone solve this?

---

### Post by HughR on 2007-02-02
I too have this problem.  To make this thread clearer, we should each specify our systems.
- Edgy, with all updates as of a couple of days ago
- Dell Optiples GX115, a small form factor PIII system (no AGP slot)
- Radeon 9250 PCI card
- ATI proprietary driver
- NTSC (Canada)
- testing tool: mplayer
- eventually want this to be a secondary Myth Box -- for watching recorded shows.

I worked through a number of problems by reading [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
Especially the hint about "sudo ln -s /usr/lib/dri /usr/lib/xorg/modules/dri"

In this thread, message numbers 24 and 39 looked useful, but have not solved my problem.

Mplayer seems to scale badly when using Xv.  The test material is an MPEG-2 (recorded from TV) with resolution 352x480 and should be scaled up to 640x480 (I think).  Unfortunately, the scaling seems to chop the bottom ~1/3 off.

If I use mplayer option "-vo x11", it looks as if no scaling happens and I get a picture filling the window vertically and leaving large empty sidebars.  Not only is the picture squished horizontally, everything in it lools squished.  Perhaps the same way as things look squished with Xv, except the whole pricture is visible.  Full-screen vs in-window does not change the size of the image.

I don't have a good understanding (model) of what the various options do.  I don't even know whether I should have two different device sections (the second being for the secondary controller).

I don't think AVIVO solutions apply to my Radeon 9250.

---

### Post by HughR on 2007-02-02
The ATI driver that I have is 8.28.8.  This appears to be the latest driver that supports the Radeon 9250.
ATI has released later drivers for newer cards.  8.33.6 appears to be the most recent.

I would guess that I will be stuck with any bug that exists now since there will likely be no updates.

---

### Post by DDM on 2007-02-02
I'm in the same boat here, I can't get xv to display on my TV-out without godawful scaling. For now, I've set Mplayer to use -vo gl, which is acceptable for now. I'm on Feisty if it matters and I'm using a 9700 Pro.  Now if I can just get mythfrontend to stop segfaulting on my crt, probably an OpenGL problem since it runs (slowly) through SSH -X.

---

### Post by giorgosts on 2007-02-03
With the 8.33.6 release if you add Option "TexturedVideoSync" "off" to textured video, performance greatly increases  with no cropping and correct scaling. For overscan to be correctly parsed you need to be as root to the /etc/X11/ directory and do an aticonfig from there.

Section "Device"
	Identifier  "Generic Video Card"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "OverlayOnCRTC2" "1"
	Option	    "TexturedVideo" "on"
	Option      "TexturedVideoSync" "off"
	BusID       "PCI:1:0:0"
EndSection

---

### Post by mnm on 2007-04-10
I got the video stretch issue working with an ATI X300, LCD and TV CRT using BigDesktop. I also got it working with MythTV.

**#1** Updated to latest driver (8.35.5)
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide")

**#2** Made the following changes to xorg.conf:
Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "PairModes" "1280x1024+1280x1024"
        Option      "OverlayOnCRTC2" "1"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        Option      "DesktopSetup" "horizontal"
        Option      "TexturedVideo" "on"
        Option      "TexturedVideoSync" "off"
EndSection

**#3** Fixed the blue tint issue in MythTV by installing libmyth compiled with "USE_ATI_PROPRIETARY_DRIVER_XVIDEO_HACK" by doing the following:

Download it here:
[http://librarian.launchpad.net/5597854/libmyth-0.20_0.20-0.2ubuntu2_i386.deb]("http://librarian.launchpad.net/5597854/libmyth-0.20_0.20-0.2ubuntu2_i386.deb")

Install it:
sudo dpkg -i libmyth-0.20_0.20-0.2ubuntu2_i386.deb

hold it so it doesn't get automatically updated:
echo 'libmyth-0.20 hold' | sudo dpkg --set-selections

---

### Post by barney_1 on 2007-04-11
Good to hear.  Do you have smooth video playback using this method?

---

### Post by mnm on 2007-04-11
> **barney_1 said:**
> Good to hear.  Do you have smooth video playback using this method?

It's definitely much better than using the old fglrx driver, 8.28.8. But it's still not as smooth as using the opengloveraly, especially when there is fast movement.

I'm done with ATI on linux. I'm getting an nvidia card.

---

### Post by barney_1 on 2007-04-12
Just be careful what you get.  I purchased an nVidia MX 4000 card and had worse playback (jerky motion) than on my ATI Radeon 9000.

Good luck!

---

### Post by volksman on 2007-04-13
> **mnm said:**
> 
I'm done with ATI on linux. I'm getting an nvidia card.

I'm SOOOOO with you on that one.  I've read the horror stories about setting up MythTV and it scared me from doing so for a year or so now.  I ran a Windows based PVR (GBPVR) which is damn nice and easy to setup but I wanted something a little more (not to mention get away from M$) and ventured into Myth.  

Honestly MythTV with a DVB card was easier to setup then the windows equiv.  The ONLY thing causing problems is the damn ATI drivers.  I've spent a week of after work nights working on just getting TVout and last night finally did it.  Then realized playback was choppy so added the Xv overlay and BAM! Picture aspect goes out of whack and overscans.  Yet the playback is nice and smooth....Just can't win....

Done with ATI.  Boycott for me begins now.

---

### Post by mnm on 2007-04-29
I just updated to feisty, all the channels when using myth come in much, much smoother and crisper. A real great improvement. (Check the bug post from above, the user posted an updated deb package for libmyth for feisty to fix the blue people issue.)

But....

When I just go in to mythtv and click "WatchTV", everything is fine. If I pause it, the video gets very jittery and is unwatchable. Sound is okay

This also happens if I try to play back a movie from the previously recorded, or if I just open up a DVD using VLC.

So this looks like an issue with video playback in general, and not just in myth. Anyone have this problem?

---

### Post by posterberg on 2007-05-02
> **volksman said:**
> Then realized playback was choppy so added the Xv overlay and BAM! Picture aspect goes out of whack and overscans.  Yet the playback is nice and smooth....Just can't win....

I use the option '-vo vidix:radeon_vid.so' in mplayer. gives me very smooth playback. Just haven't figured out how to solve the problem with the internal player in Myth. Have that annoying overscan in my Myth as well :-(

Running Fiesty with prop dirvers, had the same problems in Edgy.

---

### Post by posterberg on 2007-05-17
Using the mentioned VGA-SCART cable is much better option. Have been using that for about a week now.

No more issues with anything and a lot better image quality. :-)

Recommend this option to anyone who are familiar with some soldering and modeline tweaking.

---

### Post by tda5701 on 2007-05-17
Since version 8.27.10, fglrx has an option to use overscan on TV - and how to use it , ?
thanks, someinfo i did not find on [www.ejinz.com](www.ejinz.com)

---

### Post by mnm on 2007-05-18
Anyone here using an ati x300 and running mythtv in feisty? Just wanted to know if you were also experiencing choppy playback.

I did figure out that if I use the "blend" deinterlace method in VLC, video playback is okay. I tried every deinterlace type in mythtv, but none of them worked.

Live tv using the internal mythtv player is fine, as long as I don't pause it. But once I pause live tv and resume, or if I watch previously recorded shows, the playback is choppy.

---

### Post by posterberg on 2007-06-08
> **posterberg said:**
> Using the mentioned VGA-SCART cable is much better option. Have been using that for about a week now.

No more issues with anything and a lot better image quality. :-)

Recommend this option to anyone who are familiar with some soldering and modeline tweaking.

Have anyone been successfull with creating a conf for the SCART cable that works with the fglrx driver?

If just get static if I use the same modeline and driver config as I do with the ATI driver.

Section "Device"
        Identifier      "ATI Technologies, Inc. RV350 AP [Radeon 9600]"
        Driver          "ati"
        Option      "DynamicClocks" "true"
        Option      "ForceMinDotClock" "14MHz"
        Option      "MergedFB" "false"
        Option      "IgnoreEDID" "true"
        Option      "VGAAccess" "false"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
HorizSync    14.0 - 18.0
        VertRefresh  50.0  - 50.0
        Option      "DPMS"
        ModeLine  "1024x576" 19.875 1024 1057 1105 1272 576 580 584 625 composite interlace +hsync +vsync 
EndSection


The above works just fine with the ATI driver, but I would prefer to use the fglrx driver since there are some other stuff that I can't get to work with the ATI driver.

Suggestions?

---

### Post by segalion on 2007-06-11
I can confirm problem in Xv overlay & TV out.

With xpress 200M and latest fglx 8.37.6, no 2/3 crop  but full image compressed on the 2/3 size.

What "ati-people" think "rest-of the-world" want TV-OUT for?

I recommend "ati-people" leave their code to opensource, and "rest-of-the-word" don´t buy ati cards for HTPC projects.

---

### Post by mnm on 2007-08-02
I got an nvidia 7600GT a while back. Best decision I made. Easy to set-up, and everything works the way it should.

---

### Post by segalion on 2007-08-22
Seem that finally opensource people will win to ati people.
 RandR 1.2 tvout support (see evolution at [http://gitweb.freedesktop.org/?p=xorg/driver/xf86-video-ati.git;a=shortlog;h=randr-1.2](http://gitweb.freedesktop.org/?p=xorg/driver/xf86-video-ati.git;a=shortlog;h=randr-1.2)
)

Thanks to Alex Deucher (and rest) for this code.
Please Ubuntu wait to include this Xorg on next release

---

### Post by segalion on 2007-10-03
Tested ATI TV-out opensource support available in Gutsy Beta release.
To activate radeon TVout:
```
xrandr --addmode S-video 800x600 
xrandr --output S-video --mode 800x600

```

You can make things like:

```
xrandr --output S-video --off
xrandr --output S-video --right-of LVDS or VGA-0
xrandr --output S-video --set tv_standard pal

```vaild options are pal, ntsc, ntsc-j, pal-60, pal-m,scart-pal,default
after setting the standard, you'll have to turn the tv output off and then on again [thanks [Alex Deucher]("http://mailman.linux-thinkpad.org/pipermail/linux-thinkpad/2007-August/039885.html")]

To change XV port seems that xvattr could be used. You need install [xvattr package]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=xvattr&searchon=names&subword=1&version=gutsy&release=all") 
and follow [xvattr man pages]("http://linux.die.net/man/1/xvattr") you could put:
```
xvattr -p 1 -a XV_COLORKEY -v 10
```
To switch overlay to second monitor (S-video):
```
xvattr -a XV_CRTC -v 1

```
It works fantastic !!!
Thanks to every people developping this great feature in radeon driver.

---

### Post by vemon on 2007-10-19
Do you know if it's possible to statically add that (xrandr) information to xorg.conf so that I wouldn't need to "add mode" and "enable s-video" with a separate command?

---

