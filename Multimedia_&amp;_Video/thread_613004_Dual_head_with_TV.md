---
title: "Dual head with TV?"
date: 2007-11-14
forum: Multimedia &amp; Video
---

### Post by Kymus on 2007-11-14
I'm sure there's gotta be a thread on this somewhere on the forum, but I can't seem to find one so...

My adapter cable came in from ATI today (^__^) and so I want to set up a dual-head with my TV so I can watch video files on there instead of burning everything to DVD ($$$$). I hooked everything up, went to my screen settings, and it won't let me enable the second monitor... it's grayed out

 [[IMG]http://img230.imageshack.us/img230/1710/screeniecy5.th.jpg[/IMG]](http://img230.imageshack.us/my.php?image=screeniecy5.jpg)


Some advice on how I can get this working would be appreciated :D

---

### Post by Kymus on 2007-11-14
bump

[img]http://a1350.q.twdx.net/forum/gallery/albums/july07/aae.jpg[/img]

:D

---

### Post by Kymus on 2007-11-15
bump.

---

### Post by CarpKing on 2007-11-15
I think that GUI hasn't caught up to the actual program yet.  First of all, you should tell us what video card you have.  Second, are you using the drivers that came with Ubuntu, or did you install the proprietary drivers?  

If you are using the ones that came with Ubuntu, you'll probably be using Xrandr.  There are several threads about this that you can find in the forums here, but [this]("http://intellinuxgraphics.org/dualhead.html") should help you get started.  The introduction of Xrandr means that a lot of the old threads about TV-out no longer apply, so it can be harder to find the information you need.

---

### Post by Kymus on 2007-11-15
Hi Carp King,

I think you're right; though I know nothing about this :-D

My video card is an **ATI Radeon X800GTO**

I am using the proprietary ATI drivers

---

### Post by Kymus on 2007-11-17
bump

---

### Post by Kymus on 2007-11-18
bump

---

### Post by CarpKing on 2007-11-19
You probably want to look into the "BigDesktop" thing.  I think that's what the proprietary drivers use for dual-head.

---

### Post by Kymus on 2007-11-19
I see. I found a How-To [here]("http://ubuntuforums.org/showthread.php?t=301941"), so I'll try fiddling with it and hopefully all will be wonderful (though I won't hold my breath :P).

---

### Post by Kymus on 2007-12-10
Well, I went to the previously mentioned thread and it seems that that no one who has an answer is posting on that thread anymore.

as such, I figured I would carry that problem over here to my original thread on this.

> 
I am experiencing a few problems:

    kymus@Shouxing:~/sbc/sbc$ sudo aticonfig --initial --overlay-type=Xv
    Found fglrx primary device section
    Nothing to do, terminating.

I dunno if it's supposed to do that, but I figure probably not.

the other problem:

    kymus@Shouxing:~/sbc/sbc$ sudo aticonfig --query-monitor
    Connected monitors: none
    Enabled monitors: none
    kymus@Shouxing:~/sbc/sbc$ sudo aticonfig --enable-monitor=CRT1,TV
    ati_dm: FGLRX_EnableDisplays failed when try to enable display: 5.

---

### Post by Kymus on 2008-01-20
bump.

---

### Post by Kymus on 2008-01-24
bump.

---

### Post by Kymus on 2008-02-05
bump

---

### Post by Koiti on 2008-02-08
Please stop bumping this!

I have a similar setup here, dual head (Lcd + Tv), using the repositories' restricted drivers.

Try using

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

To create a backup and then:

```
sudo aticonfig --initial=dual-head
```

This command will modify your /etc/X11/xorg.conf, adding a secondary "Screen", "monitor" and "Device" Sections to it. It'll look like this by now:

```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	Screen         "aticonfig-Screen[1]" LeftOf "Default Screen"
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection
```

Please notice that now there's TWO Screen Sections, and the "LeftOf" modifier tells the x-server the correct positioning of your monitors. The default one is "RightOf". Modify accordingly.

You can also FORCE the tv to a LOWER resolution than 1024x768 to make text easier to read. I use 800x600 but that's up to you to decide. Mine looks like this:

```
Section "Screen"
	Identifier "Default Screen"
	Device     "Generic Video Card"
	Monitor    "RDT179V"
	DefaultDepth     24
	SubSection "Display"
		Modes    "1280x1024"
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
		Modes "800x600"
	EndSubSection
EndSection
```

Output of my fglrxinfo:

```
koiti@koiti-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1650 Series
OpenGL version string: 2.0.6473 (8.37.6)

display: :0.0  screen: 1
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: 
OpenGL version string: 2.0.6473 (8.37.6)
```

Cross your fingers and restart X (ctrl+alt+backspace).

On a side note about the dual head mode, it generates TWO independent desktops, allowing to different wallpapers, but you CAN'T move your windows between them. If you just want to see your videos in this secondary monitor this will not be a problem, I think. You'll just have to open your player in the secondary desk. If you are an CLI user, just input your commands like this:

```
DISPLAY=:0.1 command
```

This is very useful with mplayer + thunar/nautilus scripts.

Cheers from Japan.

---

