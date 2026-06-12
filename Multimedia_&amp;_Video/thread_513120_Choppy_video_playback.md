---
title: "Choppy video playback"
date: 2007-07-30
forum: Multimedia &amp; Video
---

### Post by Rovdjur on 2007-07-30
Now I assume that this is a videocard-related problem? I have an ATI Mobility FireGL V5250, and I installed the fglrx drivers with the control panel.

The card says that it has OpenGL enabled, and my renderer is Mesa GLX Indirect.

Here is my Xorg:

```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1680x1050"
	EndSubSection
EndSection

```

Boy, if I could get this to work, then my system would be working at 100% Everything works except full-screen video playback (I should probably mention that when the video are fairly small they play just fine. Only when they get big and in fullscreen mode is it choppy).

Any advice on how to fix this is appreciated, thanks!

---

### Post by gentine on 2007-07-30
From what I understand ubuntu hates ATI. So this may be unsolveable.

---

### Post by Gausian on 2007-07-30
what cpu do you have?  some videos at higher bitrates rely heavily on cpu speed.

---

### Post by deadgobby on 2007-07-30
Is the choppy play back from on  line or DVD? Amount of cpu and ram speed can play a factor. If the internet it could be just slow. Like if you use dial up VS. DSL or cable modem.
Gobby

---

### Post by TravMan63 on 2007-07-30
I say this with hesitation... try windows.  

On a machine with 700mhz, 256 MB, intel vido (810?) .... xubuntu and elive ... using totem, xine, mvideo,and vlc players...

totem wouldn't play most wmv's
xine would play some choppy... (usually homemade ones - from XP) - otherwise xine did fine

mplayer (elive) - had the audio/video out of sync. -- this was the best performer overall except for the sync problem.

vlc - played ok - on a 1.5 ghz machine

Windows XP and windows media player on same 700mhz machine... 'just works'.
Plus it's better for powerpoint/open office - it's main application.
Impress is also 'choppy' and laggy with it's transitions.

------
I PREFER linux... but in this real world ap - it just isn't cutting it
------
Anyone know WHY this is?  Video drivers? Codecs?

---

### Post by Rovdjur on 2007-07-30
Oh yes, sorry for not posting my computer specifications! I can assure you all that it is not my computer.

I have the folllowing:

Intel Core 2 Duo T7600 (2.33GHz)
2GB RAM (2x1 667MHz)
ATI Mobility FireGL V5250 (256MB)

And this is just from a normal, legal, store-bought DVD that I am experiencing this choppy playback with. I am running a dual boot and in Windows XP Pro the video playback is just fine.

---

### Post by TravMan63 on 2007-07-30
> 
Intel Core 2 Duo T7600 (2.33GHz)
2GB RAM (2x1 667MHz)
ATI Mobility FireGL V5250 (256MB)


The speed of your cpu and RAM certainly is not the problem.  Someone else mentioned problems with ATI support.  In the Nvidia world, there are different 'drivers' you can use on linux, than could be something worth exploring.

> 
And this is just from a normal, legal, store-bought DVD that I am experiencing this choppy playback with. I am running a dual boot and in Windows XP Pro the video playback is just fine


Like in my situation, windows 'just works'... and this clearly indicates your hardware is capable of doing what you want.

I have found various players in linux work with different results.
Mplayer seems to use less resources, vlc works with wmv's better (had sync problems in mplayer), xine  didn't play some wmv's well at all, and totem performed the worst.  Have you tried all these players?

I tried Elive, with mplayer and vlc - (on a 2Ghz pc) - I don't have the DVD player to play with - but they performed very nicely in that setup.  Just apt-get install vlc.  No extra codecs etc was needed in my scenario... and Elive looks quite nice (but it's e17 version is still immature but quite usable)  

I have e17 installed on UbuntuCE with Kde, Gnome, and E17 (on the 2ghz machine) - and all 'is good' - so far.

Good luck
TM

---

### Post by JimmE on 2007-07-31
I have exactly the same problem. I installed ubuntu on my ex-main-windows PC, and tweaked /etc/X11/xorg.conf to enable dual-monitor support.

I get choppy video whenever trying to watch media on this PC. I have tried the default media player and also VLC, which, like the OP, works fine in a small window but not when the video is resized to full-screen.

I saw a post on the internet which suggested it was to do with ubuntu's default bit-depth being 24 and that changing it to 16-bit would enable hardware acceleration for the card. However, the post was vague about the xorg.conf edit required, and despite trying several times, any edit I make either makes no difference or prevents the PC from booting, and I have to boot into recovery mode and undo the changes in xorg.conf using vi.

If this is the right principle, does anyone have any more idea of how to change the bit-depth successfully? Hopefully this would work for the OP's PC as well.

---

### Post by Harmshi on 2007-07-31
I've had the same issue. Running on thinkpad 40/p with ATI FireGL 9000. In my case,the choppy video playback on fullscreen was due to Desktop Effects (compiz) being enabled. Try disabling the dekstop efefcts and see what happens.
Also have a look at with video output you are using (preferences in MPLayer, or VLC player). Video playback seems only to work well with Xv in my case...

---

### Post by burnfromwithin on 2007-08-20
I have found a work-around/solution to this problem, and had stumbled upon this stale thread while trying to solve the same issue.  I think this may possibly help someone who comes across this thread trying to solve the same issue

Here's the problem I was having:

On my ATI MOBILITY FireGL V5000 I was having troubles watching video in fullscreen.  If I watched it without resizing it, everything looked fine, but on fullscreen it would get incredibly choppy (I daresay, unwatchable).   I tried all sorts of settings inside VLC, tried all sorts of media players/codecs.. nothing worked.  The same file would play just fine on my Windows boot, however, so I knew it wasn't my computer's hardware.

In researching multiple ATI driver issues, I found this Wiki helpful:  [http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page)

More specifically, I used the configuring and performance issues pages:
[http://wiki.cchtml.com/index.php/Configuring](http://wiki.cchtml.com/index.php/Configuring)
[http://wiki.cchtml.com/index.php/Performance_Issues](http://wiki.cchtml.com/index.php/Performance_Issues)

I made two changes, one from each page (don't know which one did the trick, but I will get to that later..):

1.  Enable video acceleration:

```
sudo aticonfig --overlay-type=Xv
```

2.  Add the following to the 'Device' section that references the fglrx driver:

```
Option		"XaaNoOffscreenPixmaps"
```



Now, I believe that the first change is actually what fixed it, in essence doing what I found as a solution after I had fixed it: [http://ubuntuforums.org/showthread.php?t=96256](http://ubuntuforums.org/showthread.php?t=96256)

I'm new to Ubuntu and just wanted to get my video working, I give no warranties that this won't screw something else up on your system, just letting you know what worked for me and hoping I can be helpful in some way!

---

### Post by Scold on 2007-10-20
> **Harmshi said:**
> I've had the same issue. Running on thinkpad 40/p with ATI FireGL 9000. In my case,the choppy video playback on fullscreen was due to Desktop Effects (compiz) being enabled. Try disabling the dekstop efefcts and see what happens.
Also have a look at with video output you are using (preferences in MPLayer, or VLC player). Video playback seems only to work well with Xv in my case...

I had the same problem until now... For me, it worked when I turned off Beryl and set the "video output" for MPlayer to "no Xv" :D

---

### Post by DFreeze on 2007-10-23
I've searched the options of MPlayer, but I couldn't find that one. Could you post a screenshot of where that option should be? 

Also, I really like the SMplayer GUI, but that player seems to have less options for configuring the video-output than MPlayer. I couldn't find any "no XV" option there either...

---

### Post by rvm4000 on 2007-10-23
In the preferences dialog of smplayer you can see ALL video output drivers available for mplayer.

There's no "no xv" thing, use "x11".

---

### Post by revolutio on 2007-10-25
Figured I'd try this thread before dumping my video woes in full on the forum.

Anyway, I've had this problem since I updated Xubuntu to Gutsy came out (I'm not sure if that was the instigator since I was doing a number of things).  Mine is even jerky in the regular size but in double size or fullscreen (I use mplayer) it is a slide show.  I've tried a number of the solutions on this page to no effect. My processor, RAM, and video card are certainly not deficient since I am able to run heavy games on my XP partition.

I switched away from Windows to escape video playing woes amongst many other issues.  But completely impairing my movie watching ability really leaves me no choice but to go back to XP.

For our purposes lets assume I am a complete newbie.  So any ideas?

---

### Post by Haak on 2007-10-25
i have some kind of troubles too on this matter. Thing is, I installed a lot of codex. I am playing all my movies from a samba share. When I activate a caching of about 2MB, everything goes fine. This is, strange, in WinVista I never had to activate caching or anything like this. 

Haven't tested it locally. But my fileserver (Ubuntu with samba) should be more than fast enough for this kind of speeds)

My workstation is a C2D on 2,7ghz and an Nvidia 8800. Should be allright.

---

### Post by revolutio on 2007-10-28
Bringing this back up because I'm entirely running out of options.  I'm pretty sure I've tried all available solutions on the web at this point.  Here is my xorg.conf info in case any kind soul wants to help.  Let me know if you need anything else or have any ideas.  Please!

```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "vbe"
	Load  "dbe"
	Load  "v4l"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "XaaNoOffscreenPixmaps"
	Option	    "UseInternalAGPGART" "no"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "0"
EndSection

```

Help save me from being forced to go back to XP!

---

### Post by revolutio on 2007-10-29
bump :confused:

Save me from Bill Gates!

---

### Post by DFreeze on 2007-10-29
Wish I could help you, but the only thing I can do is make sure this post comes back up. So I'll bump it up for ya ;)

---

### Post by latchkeyed on 2007-10-29
@revolutio 

Have you tried disabling desktop effects? You can turn them off by going to the System Menu --> Preferences --> Appearance and clicking on the "Visual Effects" tab. If the settings are set to anything but "None," that is most likely the source of the playback issues. Go ahead and change it to None.

The change to Gutsy is causing issues with this because they made the default desktop use compositing effects, and none of the video players have their output drivers working with that yet. I'm not sure if it is only an ATI card issue, since I have one of those two, but I'm in the same playback boat as you, and turning off effects restores my playback.

---

### Post by revolutio on 2007-10-30
> **latchkeyed said:**
> @revolutio 

Have you tried disabling desktop effects? You can turn them off by going to the System Menu --> Preferences --> Appearance and clicking on the "Visual Effects" tab. If the settings are set to anything but "None," that is most likely the source of the playback issues. Go ahead and change it to None.

The change to Gutsy is causing issues with this because they made the default desktop use compositing effects, and none of the video players have their output drivers working with that yet. I'm not sure if it is only an ATI card issue, since I have one of those two, but I'm in the same playback boat as you, and turning off effects restores my playback.
Thanks for the tip, I kind of suspected something like that (something has been using my CPU a lot more than it should when I don't have apps open).  However, that menu string doesn't exactly exist in Xubuntu.  Checked Desktop Settings, Display Settings, Windows Manager Settings, Windows Manager Tweaks, and Workspace Manager.  None of them had a Visual effects tab or anything of the sort though I the Desktop Setting menu felt like it should be there.  

Haven't tried turning off "Allow XFCE to manage desktop" yet, I expect that will have some serious visual changes.  I'll give that a shot when I am done with studying (read: tomorrow afternoon).

Also thanks for the bump DFreeze.

---

### Post by revolutio on 2007-10-31
Okay the "Allow Xfce to manage desktop" is apparently just as worthless as Microsoft Security updates.  When I uncheck it the icons on the desktop disappear (I don't use them anyway) and nothing else changes, video playback is still halting.  Restarting returns it to being checked again.

Percussive maintenance didn't improve the situation but it did make my floppy drive start working again.

Any other ideas?

---

### Post by Larry Lurex on 2007-10-31
Same problem here, but with an nVidia GeForce 4 Ti4200.My problems started after the installation of Gutsy (Feisty+Compiz had no problems at all). I removed the xserver-xgl from Synaptic and enabled AIGLX in xorg.conf. Now works great, no more fullscreen "slideshows"... I hope this can help...

Cheers
Andrea

---

### Post by kshane on 2007-10-31
> **Rovdjur said:**
> Now I assume that this is a videocard-related problem? I have an ATI Mobility FireGL V5250, and I installed the fglrx drivers with the control panel.

The card says that it has OpenGL enabled, and my renderer is Mesa GLX Indirect.

Here is my Xorg:

```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1680x1050"
	EndSubSection
EndSection

```

Boy, if I could get this to work, then my system would be working at 100% Everything works except full-screen video playback (I should probably mention that when the video are fairly small they play just fine. Only when they get big and in fullscreen mode is it choppy).

Any advice on how to fix this is appreciated, thanks!

If it doesn't say ATI in xorg.conf, then ATI is not properly installed...

And Ubuntu doesn't hate ATI, it's the other way around.  But, I think hate's the wrong word.  ATI is a for profit company and, therefore provides more support to where the perceived profit is.  But, they ARE coming around.

---

### Post by revolutio on 2007-10-31
> **Larry Lurex said:**
> Same problem here, but with an nVidia GeForce 4 Ti4200.My problems started after the installation of Gutsy (Feisty+Compiz had no problems at all). I removed the xserver-xgl from Synaptic and enabled AIGLX in xorg.conf. Now works great, no more fullscreen "slideshows"... I hope this can help...

Cheers
Andrea
Xserver-xgl wasn't installed in the first place and AIGLX is specific to Compiz it seems which I don't have.  :confused:

Installing xerver-xgl out of curiosity did have hilarious results.  4:3 aspect ration movies became 98:5 aspect ratio.

---

### Post by meowsus on 2007-11-02
> **burnfromwithin said:**
> 
1.  Enable video acceleration:

```
sudo aticonfig --overlay-type=Xv
```

2.  Add the following to the 'Device' section that references the fglrx driver:

```
Option		"XaaNoOffscreenPixmaps"
```


I tried this on my machine (i have an ATI Radeon 9800) and part one made video playback insanely worse. So i checked out

```
 
sudo aticonfig --help

```

to see what to set it back to, and the only other option (beside "DISABLE") was **opengl** which i tried and now my choppyness problem seems to be a touch better.

Very useful stuff comes from using a **help** switch sometimes :D

---

### Post by revolutio on 2007-11-03
Tried it, made it slightly worse so I'm back to Xv.

In order of effectiveness of the drivers in Mplayer:
Xv
X11
gl
gl2

I'm installing VLC now and am going to see if things are different now since I got my ATI drivers working.  Previously VLC had been notably slower so I don't have high hopes.

---

### Post by EarlGrey on 2007-11-03
> **burnfromwithin said:**
> I have found a work-around/solution to this problem, and had stumbled upon this stale thread while trying to solve the same issue.  I think this may possibly help someone who comes across this thread trying to solve the same issue

Here's the problem I was having:

On my ATI MOBILITY FireGL V5000 I was having troubles watching video in fullscreen.  If I watched it without resizing it, everything looked fine, but on fullscreen it would get incredibly choppy (I daresay, unwatchable).   I tried all sorts of settings inside VLC, tried all sorts of media players/codecs.. nothing worked.  The same file would play just fine on my Windows boot, however, so I knew it wasn't my computer's hardware.

In researching multiple ATI driver issues, I found this Wiki helpful:  [http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page)

More specifically, I used the configuring and performance issues pages:
[http://wiki.cchtml.com/index.php/Configuring](http://wiki.cchtml.com/index.php/Configuring)
[http://wiki.cchtml.com/index.php/Performance_Issues](http://wiki.cchtml.com/index.php/Performance_Issues)

I made two changes, one from each page (don't know which one did the trick, but I will get to that later..):

1.  Enable video acceleration:

```
sudo aticonfig --overlay-type=Xv
```

2.  Add the following to the 'Device' section that references the fglrx driver:

```
Option		"XaaNoOffscreenPixmaps"
```



Now, I believe that the first change is actually what fixed it, in essence doing what I found as a solution after I had fixed it: [http://ubuntuforums.org/showthread.php?t=96256](http://ubuntuforums.org/showthread.php?t=96256)

I'm new to Ubuntu and just wanted to get my video working, I give no warranties that this won't screw something else up on your system, just letting you know what worked for me and hoping I can be helpful in some way!

Thanks so much! The second way helped and solved the issue completely.

I can't tell how greateful I am :)

---

### Post by revolutio on 2007-11-03
VLC plays my videos smooth as silk.  Linux finally lived up to my fantasy of it as actually being smoother and less bulky then windows.

Then I found out that it thinks my videos are a tenth the length they actually are and that all the AVIs need fixing.

---

### Post by theknowledgeist on 2007-11-11
I've having the same problem.

I have a Core 2 Duo 2.6ghz and a GeForce 8800GTX, and I disabled visual effects (which helped but didn't solve the problem).

Its especially bad trying to play a 1080p movie in .mkv format, in both VLC Media Player and Totem. Sometimes I get less than 1fps.

I have installed the nVidia restricted drivers. 

Any suggestions? Thanks.

---

### Post by Whiffle on 2007-11-11
Not sure about those who are just playing video files, but for those playing dvd's, it wouldn't hurt to do a 

```

hdparm -d /dev/whateveryourdvddriveis

``` 

to make sure DMA is on.

---

### Post by revolutio on 2007-11-13
More updating because, well, what else can I do?

New partition, fresh install of Xubuntu 7.10.  Without doing anything else I install VLC... and it fails miserably. Still choppy, still unable to fullscreen it.

Back to square 1.  Something is fundamentally wrong here.

Currently -
Windows: 1
Linux: 0

And that is just in regards to my video problems...

---

### Post by harrissimo on 2007-11-13
I had the same problem of choppy video playback.

The fix I used was to activate the **[COLOR="Red"]DMA[/COLOR]** on my DVD drive.  This was done in the following way:

In the console type:

```
sudo hdparm -d /dev/hdc
```

This will return a value of 0 or 1.  If 0 then DMA is deactivated, if 1 your DMA is on.

If your DMA is off then you need to reactivate it by typing in the console:

```
sudo hdparm -d 1 /dev/hdc
```

When the DMA is on it should rectify the problem.

:)

I should also point out that the /hdc may be different.  This should be replaced by your device name for the DVD drive that you are activating

---

### Post by revolutio on 2007-11-14
No dice.  The problem extends beyond DVDs and DMA was already active on the drive.

I'm starting to lump this video problem in to the general problem with the OS.  Just about any action sets the CPU to 100% and takes over a second to enact (particularly file browsing in Thunar).  Though I wouldn't even know how to begin to ask for assistance on the problem since it seems so general.  :confused:

EDIT: Just found out my fglrx troubles were for naught.  
[http://ubuntuforums.org/showthread.php?p=3771089](http://ubuntuforums.org/showthread.php?p=3771089)

---

