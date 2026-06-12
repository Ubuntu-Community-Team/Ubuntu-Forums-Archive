---
title: "Video Tearing in Natty"
date: 2011-04-29
forum: Multimedia Software
---

### Post by teonghan on 2011-04-29
Greetings,

Finished a fresh install of Ubuntu Natty. Faced the good old video tearing issue once more. I am using the latest nvidia driver and tried my videos on smplayer and umplayer. I enable every single "vsync" options that I can find in compiz settings manager and nvidia x server settings but no avail.

Anyone experience this?

---

### Post by 749 on 2011-04-29
Same issue here. I tried every combination of options in compiz and nvidia-settings with no luck.
The same computer has no tearing at all using the old Ubuntu 10.10

---

### Post by Roosje on 2011-04-29
> **teonghan said:**
> Greetings,

Finished a fresh install of Ubuntu Natty. Faced the good old video tearing issue once more. I am using the latest nvidia driver and tried my videos on smplayer and umplayer. I enable every single "vsync" options that I can find in compiz settings manager and nvidia x server settings but no avail.

Anyone experience this?

Same here after update 'final' version from 10.10. Nvidia GT220 card btw, 4 core AMD phenom Black edition.
Any idea how to fix/circumvent this? Have you tried the Nouveau driver? BTW, Gnome player, and VLC show same problem, jittery (with movement) video and tearing.
Here i was so happy 11.04 was stable ;-)

---

### Post by scu on 2011-04-29
Updated to Natty from 10.10 and unfortenately same problem here. 

nVidia GeForce 8200
Nvidia driver version 270.41.06

Sync to VBlanks selected from Nvidia X server settings, tried also all possible combinations of compiz settings too.

---

### Post by el_koraco on 2011-04-29
Does the nvidia control center have something like a tear free desktop option? I find that disabling that one in Catalyst gives me smooth video feedback. In Kubuntu though :D

---

### Post by Dr_Frost on 2011-04-29
I also have bad tearing now in natty, all settings that used to work in 10.10 does not work at all, i have tried about 50 settings now

My take on this is that the unity bar and many things now have a dedicated openGL, i cannot see the normal blink of the desktop when using "Unredirect Fullscreen Windows" 


This is a GIANT deal breaker for me, i kinda like the unity system, ones you get use to use it it is ok

But if no fix for this im going back to 10.10

EDIT: ALSO zooming lags like it is running on a 100MHz machine, what's going on!!!!, this is not an upgrade in any way

---

### Post by 749 on 2011-04-29
> **Dr_Frost said:**
> 
My take on this is that the unity bar and many things now have a dedicated openGL, i cannot see the normal blink of the desktop when using "Unredirect Fullscreen Windows" 

I think unity has nothing to do with tearing. I tried to see a video using Ubuntu Classic instead of unity but nothing changed.

---

### Post by Roosje on 2011-04-29
Also using Classic desktop, not Unity. Kinda disheartening that a clean install shows the same problems. Anyone having a Nvidia card without the problem when running say 720p vids with smplayer, vlc etc?

---

### Post by Eromatic on 2011-04-29
I've seen video tearing while only running under "Ubuntu Classic without Effects" & VDPAU. I had to follow the guide (Disabling the Composite Extension) at:

[http://www.mythtv.org/wiki/VDPAU#Disabling_the_Composite_Extension](http://www.mythtv.org/wiki/VDPAU#Disabling_the_Composite_Extension)

...as that corrected the issue with my 9500 GT & Video Driver 270.41.06-0ubuntu1. If intending to use Unity or Ubuntu Classic with Effects, you probably will not want to do this though...

---

### Post by Dr_Frost on 2011-04-29
I installed gnome 3.0 instead and it has no tearing, but both gnome 3.0 and unity really have almost no ways to customize, like putting the panel in the bottom, so it's back to my 10.10, one thing i like with ubuntu is that you can make it look like you want to, this can cannot see in the new 11.04, so i will wait for the next upgrade, to try again.

---

### Post by scu on 2011-04-29
> **Eromatic said:**
> I've seen video tearing while only running under "Ubuntu Classic without Effects" & VDPAU. I had to follow the guide (Disabling the Composite Extension) at:

[http://www.mythtv.org/wiki/VDPAU#Disabling_the_Composite_Extension](http://www.mythtv.org/wiki/VDPAU#Disabling_the_Composite_Extension)

...as that corrected the issue with my 9500 GT & Video Driver 270.41.06-0ubuntu1. If intending to use Unity or Ubuntu Classic with Effects, you probably will not want to do this though...

This solved the tearing problem for my ubuntu classic (no effetcs) set up. Thanks! O:)

---

### Post by fotosam on 2011-04-29
> Originally Posted by Eromatic  
I've seen video tearing while only running under "Ubuntu Classic without Effects" & VDPAU. I had to follow the guide (Disabling the Composite Extension) at:

[http://www.mythtv.org/wiki/VDPAU#Dis...site_Extension](http://www.mythtv.org/wiki/VDPAU#Dis...site_Extension)

...as that corrected the issue with my 9500 GT & Video Driver 270.41.06-0ubuntu1. If intending to use Unity or Ubuntu Classic with Effects, you probably will not want to do this though...
This solved the tearing problem for my ubuntu classic (no effetcs) set up. Thanks! 


This solves the Tearing on natty and Ubuntu classic!

Thanks Alot

---

### Post by 749 on 2011-04-29
Thank you for the solution, but i really hope there is a way to get things working with effects enabled.
Gnome without effects is a bit poor, and Gnome 3 is really ugly in my opinion.
I still can't understand why Maverick works perfectly and the same settings do nothing on Natty...

---

### Post by Dr_Frost on 2011-04-29
my tearing is gone again, but im of course back to 10.10, will wait for next upgrade, and i would like to comment also on gnome 3. damm it's not pretty.....

---

### Post by Norton3000 on 2011-04-29
Disabling the Composition Extension fixes the tearing problem but unfortunately breaks everything else (window decoration etc).

---

### Post by 749 on 2011-04-30
On launchpad there is an open bug about the issue we're discussing in this thread.
If you have an account and you experience video tearing with nvidia gpu, please subscribe it:

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/600178](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/600178)

---

### Post by lakerssuperman on 2011-05-01
I have also experienced this.  I'm running a Core i7 and GTX 560 ti.  There should be no reason for any slowdowns of any kind on that type of system.  I have tearing in videos, mostly towards the top of the screen.  VDPAU crashes hard with Gnome Mplayer when I minimize in either Unity or Classic with effects.  Switching of windows pauses the whole desktop for an instant when playing back video.  Smooth scrolling starts to drag.  If I close everything the desktop speeds back up but playing a video or going to a Flash intensive website seems to drag everything down again.  This is a major problem as the NVIDIA driver is, in my opinion a premiere video solution on Linux.

I tried installing 10.10 on my Core 2 Quad Q600 and GTX 275 rig and there was zero issue, even running the same NVIDIA drivers from the X-SWAT ppa.  This leads me to think it may be something with the new X server or the new version of compiz.

Just as an aside, things may be bad with NVIDIA but I tried Unity on some of my AMD video hardware and it's almost unusable it is so slow and laggy.  I really like Unity but these are show stoppers for the time being.

---

### Post by masterluke on 2011-05-01
This fixes it for me..
 
[http://ubuntuforums.org/archive/index.php/t-1390284.html](http://ubuntuforums.org/archive/index.php/t-1390284.html)
 
I think the important bit is manually setting the refresh rate in CCSM

---

### Post by Dr_Frost on 2011-05-01
well i gave it another go, and it works, but im running classic (no effect), if i just run classic then the window decorations go away when opening a video.
But only problem with running classic (no effect) is that some of the functions i often use are not available, like desktop zoom, no matter how i set it up nothing happens......

But the tearing issue is gone, now there are just other issues, this natty version is still not very good, there are just to many things missing.

Should i just give up and go back to 10.10 or 10.04?

---

### Post by 749 on 2011-05-02
> **masterluke said:**
> This fixes it for me..
 
[http://ubuntuforums.org/archive/index.php/t-1390284.html](http://ubuntuforums.org/archive/index.php/t-1390284.html)
 
I think the important bit is manually setting the refresh rate in CCSM

Indeed, this is the first thing I tried to do, because it worked in previous releases, but seems to do nothing on natty for me. What gpu are you using? And does it work in both unity and classic desktop?

So far the solution found by Norton3000 is the only one working for me, but getting rid of tearing means breaking everything else in the desktop enviroment.
This release is the most buggy i've ever seen in Ubuntu, it seems more an alpha release than a stable one, and not only for the tearing... :(

---

### Post by jebus_beler on 2011-05-02
I have the same problem on natty with an msi gtx 560 twin frozr ii.  I've had the problem once now.  I watched a couple of videos which were fine and then I left my system on overnight and when I tried it in the morning everything was (embarrassingly) slow and choppy including videos.  Restarting X did not fix this problem but rebooting did.

Can anyone confirm that this problem only happens after running videos?  I've added myself to the list for the bug on launchpad (there are only 10 others listed now ... please register the bug if you have it) but for now I just want a working system.  I'm willing to give up watching videos on this system for now if it will avoid the issue but does anyone know if it will?  Do I also have to watch out to not run any flash sites?  I would downgrade but I'm worried that would break drivers for usb and audio, etc.. that I'm using on my motherboard.  I guess this doesn't look like its going to be solved in the short term...

---

### Post by jebus_beler on 2011-05-03
Ok well sadly I can confirm that this problem does crop up by itself even if I don't play any videos.  Messing with "Sync to Vblank" doesn't really help though it makes things seem like they might go faster for a sec but ultimately the only solution is a reboot.

How are people managing with this?  Has anyone found a way to avoid it?  I don't really think its practical to keep rebooting every few hours.

Any idea if this affects kubuntu?  Or should I backtrack to an earlier release of ubuntu?  I recall people saying this also occurred in 10.10.  Would that mean I'd have to go back to 10.04 to get a stable system?

---

### Post by Dr_Frost on 2011-05-03
Well i gave it another go, and can now say for sure im going to wait a few months to try again and see if it is better.

But for now and some time im back in 10.10, and it is NICE, everything works to the full extent, tried 10.04 but there where many things that ignored me like crazy.
I have my Frost_10.10 updated to today, and on request and guidance (for me), i can torrent upload it.

---

### Post by Dr_Frost on 2011-05-03
Ok if anybody else wants a 10.10 thats fully upgraded (besides firefox 4, but the ppa is added, so update the 15MB and it's there)

---

### Post by Jukka76 on 2011-05-05
I went through all compiz plugins and found that when disabling "Windows Decoration plugin" I can play Full screen videos smooth and without tearing. "Composite" extension enabled in Xorg.conf and using Unity-3D. 
I'm using VDR and playing using xine (vdpau) as output device.

xorg.conf settings
```

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9400"
    Option         "RenderAccel" "true"
    Option         "AllowGLXWithComposite" "True"
 Option         "ModeValidation" "DFP-0: AllowNon60HzDFPModes"
EndSection

Section "Screen"

    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "ExactModeTimingsDVI" "True"
    Option         "UseEDIDFreqs" "True"
    Option         "UseDisplayDevice" "DFP-0"
    Option "FlatPanelProperties" "Scaling = Native"
    Option         "TwinView" "0"
    Option         "metamodes" "1920x1080_50 +0+0; 1920x1080_24 +0+0; 1920x1080_60 +0+0"
    Option         "DynamicTwinView" "false"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "On"
EndSection

```

Load default compiz settings, then change these:

Composite plugin:
Check "Unredirect Fullscreen Windows"

Workarounds plugin:
Check "Legacy fullscreen support"

Window Decoration plugin:
Disable

Restart gdm.

Now the videos plays smooth and without tearing in full screen. 

So is the problem in "Window Decoration plugin". When it's enabled, maybe compiz does not detect window is full screen and does not enable full screen workarounds?

Disabling window decoration can't be used as workaround, because then you don't have title bar and corners and can't move/resize windows. Can it be replaced with some other plugin?

---

### Post by guiodic on 2011-05-05
Using mutter, tearing seems disappears.

I tried **everything**, included to downgrade compiz to 0.8.6 version. 

It should b a bug involving X and/or nvidia drivers but nvidia drivers cannot be downgraded because precedent releases do not support Xorg 1.10.x

I'm seriously thinking to downgrade to Maverick.

Video playback quality is very important for me, I use my notebook to see movies very often.

---

### Post by greybot on 2011-05-05
Had screen tearing using my external monitor at full resolution (1680x1050) with my t30 ibm thinkpad (radeon driver). Really noticeable when scrolling in firefox and moving windows around. 

Tried the compiz CCSM trick, disabling composite, setting refresh rate in xorg.conf, but nothing helped. 

Am back to 10.10 for the time being.

---

### Post by erikdstock on 2011-05-05
I am one of the people whose 3d desktops stopped working with the non-free nvidia modules on upgrade to 11.04 beta... I have a passable experience with nouveau now but nothing as smooth as nvidia's drivers were. Before i mess things up I'm wondering if this issue has been resolved yet... can i/will i be able to switch back to the nvidia drivers any time soon?

---

### Post by AgentWD-40 on 2011-05-05
I'm having the same issue using an Nvidia 8600GT video card with a Samsung Syncmaster 205BW monitor connected with a DVI cable. I put more details in another thread at [http://ubuntuforums.org/showthread.php?p=10773096]("http://ubuntuforums.org/showthread.php?p=10773096"), but for consistency please do not respond to that post. I'm also considering a switch back to 10.10.

---

### Post by dino99 on 2011-05-05
you might test without xorg.conf (rename yours if you need it back) as it often conflict with builtin kernel's graphic settings

---

### Post by guiodic on 2011-05-06
> **dino99 said:**
> you might test without xorg.conf (rename yours if you need it back) as it often conflict with builtin kernel's graphic settings

done, no matter. I tried pretty every thing possible in xorg.conf

It is a bug in nvidia driver and/or Xorg.

---

### Post by 749 on 2011-05-07
Ok, i found a workaround:

Open CompizConfig-settings manager (if you don't find it, just install it from Ubuntu Software Center).
[LIST]
[*]Enable Workarounds -> Force full screen redrews (buffer swap) on repaint
[*]Disable Workarounds -> Don't wait for video sync
[/LIST]
Open NVIDIA X Server Settings

[LIST]
[*]Enable X Server XVideo Settings -> Sync to VBlanck
[*]Enable OpenGL Settings -> Sync to VBlank
[/LIST]
Open Startup Applications and add a new program:

[LIST]
[*]Name: antitearing
[*]Command: bash -c "sleep 2; compiz --replace"
[/LIST]
Reboot

---

### Post by debd on 2011-05-07
I'm having the same problem with 10.10
[http://ubuntuforums.org/showthread.php?t=1751851](http://ubuntuforums.org/showthread.php?t=1751851)

The problem seems to belong to the X.Org server and seems a issue old enough.

This page is a good read. [http://lwn.net/Articles/268378/](http://lwn.net/Articles/268378/)

---

### Post by Eromatic on 2011-05-07
> **debd said:**
> I'm having the same problem with 10.10
[http://ubuntuforums.org/showthread.php?t=1751851](http://ubuntuforums.org/showthread.php?t=1751851)

The problem seems to belong to the X.Org server and seems a issue old enough.

This page is a good read. [http://lwn.net/Articles/268378/](http://lwn.net/Articles/268378/)
I've seen multi-tearing such as yours under Ubuntu Classic with Effects when doing: 
*sudo nvidia-xconfig --composite --damage-events --render-accel*

---

### Post by debd on 2011-05-08
> sudo nvidia-xconfig --composite --damage-events --render-accel

well, I dont know what that would do.

but, after enabling vsync from ccsm, the display is better now, less tearing.

---

### Post by Jukka76 on 2011-05-08
Here's example of video which is choppy with xine or totem, when played full screen and composite and vblank enabled.

[http://koti.kapsi.fi/~bogey/video_samples/00001.ts](http://koti.kapsi.fi/~bogey/video_samples/00001.ts)

When composite is disabled and vblank enabled the bottom scroller plays smooth.

---

### Post by Jukka76 on 2011-05-10
I found workaround, how I got "Unredirect Fullscreen Windows" working again. It is really ugly, but is ok for me for now.

Before I start fullscreen video application (xine or xbmc), script kills "unity-window-decorator". After video application exists, script starts "unity-window-decorator" again.

---

### Post by synace on 2011-05-26
> **749 said:**
> Ok, i found a workaround:

Open CompizConfig-settings manager (if you don't find it, just install it from Ubuntu Software Center).
[LIST]
[*]Enable Workarounds -> Force full screen redrews (buffer swap) on repaint
[*]Disable Workarounds -> Don't wait for video sync
[/LIST]
Open NVIDIA X Server Settings

[LIST]
[*]Enable X Server XVideo Settings -> Sync to VBlanck
[*]Enable OpenGL Settings -> Sync to VBlank
[*]Disable DFP...(name of your screen) -> Force Full Gpu Scaling
[/LIST]
Open Startup Applications and add a new program:

[LIST]
[*]Name: antitearing
[*]Command: bash -c "sleep 2; compiz --replace"
[/LIST]
Reboot

odd.. works for me though.

---

### Post by Pixel-man on 2011-06-08
> **749 said:**
> Ok, i found a workaround:

Open CompizConfig-settings manager (if you don't find it, just install it from Ubuntu Software Center).
[LIST]
[*]Enable Workarounds -> Force full screen redrews (buffer swap) on repaint
[*]Disable Workarounds -> Don't wait for video sync
[/LIST]
Open NVIDIA X Server Settings

[LIST]
[*]Enable X Server XVideo Settings -> Sync to VBlanck
[*]Enable OpenGL Settings -> Sync to VBlank
[*]Disable DFP...(name of your screen) -> Force Full Gpu Scaling
[/LIST]
Open Startup Applications and add a new program:

[LIST]
[*]Name: antitearing
[*]Command: bash -c "sleep 2; compiz --replace"
[/LIST]
Reboot
Ubuntu 11.04 x86_64. Nvidia GeForce GTS 450. NVIDIA Driver Version: 270.41.06.
It works for me. Thanks.

---

### Post by O__ on 2011-06-10
Post 749 works for me, too.
natty x86 gt220 270.41.06 vlc xbmc

But:
If I Disable DFP...(name of your screen) -> Force Full Gpu Scaling, my Samsung TV says "this mode is not supported" when i switch video to fullscreen. But still no tearing without disabling.

After this my pass-through doesnt work anymore in natty "and" my before-working backup karmic. Strange thing this intel-hda chipset thing.

thx

---

### Post by BasioMeusPuga on 2011-06-14
I was getting video tearing on a clean install of Natty x64 on a 9600M GT and 4GB RAM. That and compiz animation slowdowns.
I did the "Sync to VBlank" and set refresh rate dances and well, that didn't work.

But I did: 
a) Download the 270.41.19 Nvidia drivers from their repository (nvidia-current-dev) and;
b) Set the Powermizer to maximum performance in X server settings (Something that has to be repeated after each reboot).

That seems to have worked.
Let me know if it helps any.

---

### Post by teonghan on 2011-07-02
> **749 said:**
> Ok, i found a workaround:

Open CompizConfig-settings manager (if you don't find it, just install it from Ubuntu Software Center).
[LIST]
[*]Enable Workarounds -> Force full screen redrews (buffer swap) on repaint
[*]Disable Workarounds -> Don't wait for video sync
[/LIST]
Open NVIDIA X Server Settings

[LIST]
[*]Enable X Server XVideo Settings -> Sync to VBlanck
[*]Enable OpenGL Settings -> Sync to VBlank
[/LIST]
Open Startup Applications and add a new program:

[LIST]
[*]Name: antitearing
[*]Command: bash -c "sleep 2; compiz --replace"
[/LIST]
Reboot

Works for me but unfortunately sometimes, I got weird problems such as "missing" gnome panels when I boot into Ubuntu (actually visually missing; I can't see them but I can still click on the menu/clock for example) and also missing windows decorator (happened few minutes after booting). Try on Ubuntu 11.04 64-bit (Unity and Gnome Classic with effects) and Linux Mint 11 64-bit. By the way, Kubuntu 11.04 64-bit did not have such problem for me.

---

### Post by teonghan on 2011-07-02
> **BasioMeusPuga said:**
> I was getting video tearing on a clean install of Natty x64 on a 9600M GT and 4GB RAM. That and compiz animation slowdowns.
I did the "Sync to VBlank" and set refresh rate dances and well, that didn't work.

But I did: 
a) Download the 270.41.19 Nvidia drivers from their repository (nvidia-current-dev) and;
b) Set the Powermizer to maximum performance in X server settings (Something that has to be repeated after each reboot).

That seems to have worked.
Let me know if it helps any.

I manually install the Nvidia driver from nvidia.com (version 275.09.07 as of 2/7/2011, [here]("http://www.nvidia.com/object/linux-display-amd64-275.09.07-driver.html")). Set all vsync on Nvidia X-Settings and now I manage to get rid of the problem. I tried this on Linux Mint 11 64-bit though.

Update:
Did not completely remove video tearing, just slightly reduce it.

---

### Post by teonghan on 2011-07-10
I tried disabled the compositing in xorg.conf and video tearing gone (completely I would say) but now I have screen tearing for example when I am moving the windows (terminal, file manager, you name it). I switch to openbox and still the same.

As far as the stuff I tried, I would say KWin (or Kubuntu) is the best out there, with compositing enabled, no video/screen tearing but unfortunately Kubuntu is not my cup of tea (no offence, Kubuntu/KDE fans).

Still looking for solutions...

---

### Post by rubbersoul.josh on 2011-08-08
i'm having the same problem in natty.  i've tried the drivers you get from ubuntu software manager as well as the latest from nvidia (280.13).  neither can provide full screen video without tearing despite enabling vblank sync in xserver settings and compiz, and changing the refresh to 60 in compiz.

one thing i noticed is, despite changing the refresh rate manually to 60 in compiz, the "monitor preferences" pane says the rate is still 50.  this is confirmed by xrandr.  xrandr -r 60 returns "rate 60 hz not available for this size."

it seems that the manual setting of refresh rate in compiz doesn't actually take effect.

---

### Post by thegoonden on 2011-08-09
Having same issue here after a dist-upgrade from Maverick.

Using KDE, no compiz or anything like that as I use a desktop stretched across two monitors, which disables compiz anyway.

I tried updating nvidia drivers but for some reason X cannot load the nvidia kernel module with those and I had to use the 173 version.
32bit here.

mplayer is highly ugly with this, I'm surprised that 4 months from release there has been no fix from Ubuntu themselves.

---

### Post by thegoonden on 2011-08-10
I have now tried every fix I could find and none of them achieve anything.

Do we even know which package is broken?
Are Cannonical even aware that their latest release is not fit for use?

This is cracking me up, soul destroying.

I can't even use any 3d applications, in case the framerate runs away and overstresses my GPU (although oddly enough.....glxgears is just fine and locks to 60fps)

I'm at my wits end.
As soon as I can work out how to roll back a dist-upgrade, I'm back to Maverick, because it worked.

This kind of thing (no response whatsoever from maintainers/publishers) gets Open Source a bad name (the fact that the closed source world is little better doesn't really matter to most haters).


Has anyone tried the Alpha of the next release to see if THAT works or is Ubuntu doomed to ugliness and melted GPUs from now on?


Anyway.....
</hissy-fit>
Thanks to all those above who chucked their two cents in, it might have worked :D

---

### Post by BicyclerBoy on 2011-08-10
Video playback may be openGL XVideo or VDPAU etc..

Are you using VDPAU in mplayer ?
VDPAU video decode/presentation is always internally vsync. (the driver states it is guaranteed not to tear).
VDPAU is compatible with twinview & Xorg xinerama extension.

The vsync settings in nvidia-settings tools relate to openGL & Xvideo vsync.

The compiz/unity crap seems to interfere with everything else.
The refresh rate in compiz must be changed to match the real refresh rate as reported by monitor or nvidia-settings tool. Gnome display preferences do not work.

You could try to disable composite extension in xorg.conf as expt
or **try using "classic" desktop** (no effects) login..this is basically like 10.10

If you want to update your nVidia drivers the best way is from another ppa. This means your package manager handles all updates/installs/dependencies etc..
Try the xorg-edgers or x-swat team ppa...

---

### Post by thegoonden on 2011-08-10
Now that's one I hadn't though of.....my vdpau is defunct at the moment, but I could always try and re-enable it.)

As for the other suggestions, I'm on KDE (not Kubuntu as such, Ubuntu with KDE bolted on).....but they may prove useful to others.



Right...gonna give vdpau a try......natty lives another day.


That's if it works on 8800s I seem to recall reading it only works on G90 based GPU's whereas 8800GTX and 8800GTS 320 cards are the G80.

I'll have to check that out.

Thanks.



EDIT....balls!

Unsupported hardware from the GeForce 8 series includes the 8800GTS 320/640 MB editions and the 8800GTX.
^^^ from the vdpau page on wikipedia.
Which would explain it since I recently swapped an 8600GT out and an 88--GTS320 in.
Back to the drawing board.

---

### Post by drawkcab on 2011-08-10
I've tried just about everything under the sun.  Playback in Ubuntu is OK, not massively tearing.

When I want to watch something sans tearing I fire it up in XBMC.  XBMC is, for some reason, smooth even though I launch it from within Natty.

Go figure.

Anyway, if you wanna install XBMC, just remember to id the repos as maverick repos.

---

### Post by BicyclerBoy on 2011-08-11
from the 275 readme
```
model.............id......vdpau feature set
GeForce 8800 GTX      0x0191      -
GeForce 8800 GTS      0x0193      -
GeForce 8800 Ultra      0x0194      -
**GeForce 8800 GTS 512   0x0600     A**
GeForce 8800 GT          0x0602      A
GeForce 8800 GS          0x0606      A
GeForce 8800M GTS       0x0609      A
GeForce 8800M GTX       0x060C     A
GeForce 8800 GS           0x060D     A
GeForce 8800 GT           0x0611      A

GeForce 8600 GTS     0x0400     A
GeForce 8600 GT     0x0401     A
GeForce 8600 GT     0x0402     A
GeForce 8600 GS     0x0403     A
GeForce 8600M GT     0x0407     A
GeForce 8600M GS     0x0425     A


```

XBMC uses a specific video playback method. Most serious media apps have their own config settings.

---

### Post by thegoonden on 2011-08-11
Xbmc opens across both my displays though, and it doesn't appear to have the same range of key commands as mplayer, so it's not really an alternative. :(
(in my case anyway).
In fact I just checked and it doesn't even have basic key commands like rewind/ffwd.

I'll install it though just to verify it's useless.


Think I'm just gonna go back to maverick, and wait on the next release, and if it's broken too, it just has to accepted that it's intnentional and it's time to try Arch :D

EDIT....as I said above, VDPAU does not work on G80 chips....my GTS is the 320MB version, and therefor has no VDPAU capability in hardware. Not about to spend several hundred pounds on a new video card and power supply just because some dolt broke X :D

EDIT2: I tried xbmc, and even adding -geometry options wont make it display on just the left hand screen......and it doesn't seem to accept input files from the commandline, so I have to browse for each video like a windows user instead of just telling what I'd like to play.....and still no vdpau. It's  a nice app if you only have a single screen and don't understand the commandline, but it's not really an alternative for mplayer or vlc....thanks anyway though, it MIGHT have worked, and MAY for people with one screen who are used to windows.  It DOES have rewind and ffwd keys at least though, even thought they are no listed in the online key command list.

---

### Post by BicyclerBoy on 2011-08-11
The line from me about XBMC was to the other guy...

I posted the table of vdpau just in case you have a few more video cards lying around.
Can not trust everything on wikipedia.

Gaming cards are not HTPC video playback cards..
Only the recent gaming models have all the video features of the low spec cousins.
The only cross-over was the shader performance.
Video decode runs in a separate bit-stream processor.

A GT220/430 do perfect VDPAU playback & no power & cheap.
GT520 is lower power again & feature set D but too slow for shader de-interlacing.
GT520 is likely US$40. GT530 is OEM only

So you are using twinview..
The recent desktop manager does not seem to understand the twinview meta-screen.
XBMC & MythTV are made to be HTPC frontends not just desktop media players.

---

### Post by thegoonden on 2011-08-11
Sniffing about on ebay for a new card :D
A GTS240 which seems about the same spec as the 8800GTS

The way I have this set up, the "right" monitor is what I'm using now to type this. The "Left" monitor, the TV is playing a movie.

I WISH I could think of some other way of providing the same functionality without twin view....For example two X servers, but as far as I am aware, and have been able to achieve, only one can be active at a time....I'm sure there is a way to do it since big Unix systems can drive multiple X capable workstations....but it eludes me. It would be easier if I would never have need of using the big screen as a desktop too for work that needs big real estate. Without twin view.....XBMC AND all the cool 3d stuff would work.

The odds are 50-1 that as soon as I find another way, or fit a new card that works with VDPAU (ironic.....I "upgraded" my 8600GTS to get better HD video performance because it was RIGHT on the edge when playing full HD stuff...not realising the older core in the 8800 didn't do vdpau).....the vsync bug will be fixed within days. :D
It was all working so beautifully under Maverick.



One of those days....more video battling the desktop, then the windows games machine yanked my chain for a while, then my netbook pretended to be stone dead. Staying away from anything dangerous for a while LOL

Thanks!

---

### Post by BicyclerBoy on 2011-08-12
An 8600GT/GS will have no problems with HD playback (vdpau A), just does not look very good compared to feature set C/D.

No not a GTS 240 it is only feature set A

Maybe GTS450 or GTX 550Ti

Separate X screens is exactly what you are describing.
I think it is ideal for full screen playback.

DISPLAY=:0.1  vlc
this launches on 2nd screen.

Launcher/menu item/hotkey points to this script..
```

#!/bin/sh
# Run MythTV front end on display 1
export DISPLAY=:0.1
mythfrontend

```

Big Unix workstations use professional nVidia quadro cards which support **mosaic** ..
Same GPUs as consumer cards, different price & support.

---

### Post by thegoonden on 2011-08-12
The 8600 was JUST able to manage it, but it's fan was dead so it wasn't coping too well.


The 240 has no VDPAU Or only ugly vdpau, then?
Ooooops....I thought everything newer than the G80 based cards had vdpau support......let's hope I get outbid then :D

Dunno if I can afford a 450/550

As for separate screens........ I can't seem to get that working on Ubuntu.......if I go to a term and do startx -- :1 then only ONE of the servers will work at a time. I suppose what I need to do is launch ONE X server with two screens, but then I have to work out how to run two separate desktops too (because I do use the telly as a big monitor too for audio/video work).....it all seems a bit tricky.

I'll have to have a google for how to do it. I assume it needs done "by hand" rather than with the nvidia control panel.

I would lose the ability to just drag a youtube tab out of chrome on the monitor to the TV......which I SUPPOSE I could live without....I could always download any clip and mplayer it.

MythTV and I do not get along, it's playback is ugly compared to mplayer (with deblock and AA and stuff), It looks exactly like Windows Media Player's output, and it doesn't seem to be able to launch with a set of imput files,(I hate browsing my collection for stuff when a simple commandline can find it instantly.)

Again, thanks.....new hardware is a bit of a severe workaround but still it beats tearing.



EDIT.....some googling suggests it's no possible to have two separate screens with 2 separate desktops and a mouse that can move between them.....the only way is twinview......and that kills all the cool 3dstuff. So it's it's either ugly dekstops in twinview, or separate screens and use the monior rather than the TV for all work (it also means that any guests have no screen to work on....at the moment, visitors plonk themselves down in front of the TV and if they need the net or a game they can just take the mouse over there and work away......with any of the separate screen setups I can find on google, they would have to kick me off my sick-bed and use the monitor).
It DOES seem what I have is the best option.

EDIT2: since I have no 3d anyway in twinview, maybe I should get my 8600 back (I gave it to a friend's daughter who doesn't use it anyway) and just HOPE the GPU doesn't melt.....though as I said with full 1080 HD stuff, it gets a bit stroppy from time to time, it's Juussssst able to do it.

---

### Post by BicyclerBoy on 2011-08-12
As you were using 8600 & 8800 I assumed you were a gamer.
If you were having video playback problems with 8600 I would guess that you were not using VDPAU correctly.

VDPAU support exists in all the new cards and lots of old ones but that does not mean they are a good solutions.

For VDPAU feature set & shaders performance is everything..

GT220/240/430  perfect playback  feature set C
GT520 **no** VA de-interlace (slow shaders)  feature set D halfheight low power

GTS240   not good waste of money
GTX550ti/560  perfect everything but hi power/cost.

The GT430 is the best currently..supports HDA over HDMI

Separate X screens is not separate X servers..it is still one desktop but without the window dragging (& no icons)..

MythTV is easily the most capable & robust media player I have every used..

---

### Post by thegoonden on 2011-08-13
Well, the 8600 was bought for the Linux machine as a half decent all round card for not much cash.
The 8800GTS was bought as a gaming (specifically racing) card for a windows machine some time ago, and only put in the linux machine because I thought it was a step up from the 8600 (the windows machine has been through an 8800GTX and now has a GTX280 ).

I got outbid on the 240 and now have £30 riding on a 430, fingers crossed.

I hope all your help on this proves useful to some other folks as well......though not everybody is as pig headed as me and are more likely to wait for the normal X video drivers to be fixed.

It's greatly appreciated by me nevertheless.


I've not had much joy with MythTV.....I can't understand why it insists on setting up a database server for (I believe) tv schedules when there are none......and I never found all the same filters as mplayer in it (deblock AA etc). The other thing that annoyed me about it is that I can't do this.......

mplayer  -geometry 720x480+50+50 -vm -fs -aspect 16:9 -cache 16384 -vf pp=ac -vsync -af volnorm=2:.4:comp /media/Sam1TB-5/trek/Star.Trek.DS9.COMPLETE/Season\ 2/Star.Trek.DS9.S02*

(most of that is aliased and I wouldn't need the -geometry etc).

I just hate the idea of having to slowly and windowsly browse for a file over and over and over and over and over.

I will take another look though to see if I missed this functionality.


EDIT: as far as I can tell I have to copy ALL avi files that mythtv is to be able to play to a single directory in /var......I have 6 1TB drives full of videos, stored in a nice logical order...the drives are offline and then connected through a sharkoon sataport. So mythtv if totally pointless for me since it basically can't play my files.....either that or all the google results I found are wrong. Can't it just BROWSE like a proper program?
EDIT.....turns out mythvideo is mplayer anyway, so it's really just a load of bright and shiny menus that make it much harder to do what I'm doing already. And it definitely can't deal with dynamic directories (in fact it refuses to play anything for me at all at the minute, I point it at /mnt/play where there are some videoes, run mythfilldatabase and nothing is offered in the "watch videos" page. Oh well, it LOOKS nice :D

---

### Post by BicyclerBoy on 2011-08-13
Note the GT430 is a recommended video playback HTPC card. It is not a gaming card.

But TV is all about the scheduler & database..
Without them TV is just mind-numbing dross..
MythTV has its own player, it is not mplayer ..but you can use any external player.

mythfilldatabase is used for TV scheduling.
The video folders are different, also check out storage groups.
You can have your folders anywhere/any number..

mplayer smplayer MythTV XBMC are all built using ffmpeg libav..

MythTV's player has unbeatable seek performance (fast/accurate) & I find it to be the most capable but this likely because it is a weekly build update..

But I don't think MythTV is for you..maybe XBMC..
XBMC can be used as a frontend for a mythtv backend.

MythTV & XBMC are complete HTPCs setups,, this does not seem what you want.

AVI file/containers are completely inappropriate for modern video codecs..

Your cmd line does not look to be using VDPAU.
What codecs hide inside these .avi files (don't tell me XVid or DivX)...

---

### Post by thegoonden on 2011-08-14
oh it's not using vdpau.....that's the first choice in mplayer.conf.....and comes up as missing on this card.

The codecs are all over the place no two files the same and stuff. That particular bunch....

Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)


From what I could read, which may be massively out of date, mythtv's internal player is based on mplayer code.

I must investigate further.


430 will do me fine as I only had gaming cards in the machine because they are hand-me-downs from my DOS games PC......rarely bother gaming much in Linux, and when I do, Linux is so much less of an **** that a slower card will do the trick :D

Thanks again for the help, hopefully it will benefit others as well as myself.

---

