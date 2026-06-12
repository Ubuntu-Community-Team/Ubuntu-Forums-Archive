---
title: "MythVideo aspect ratio issue"
date: 2011-03-12
forum: Mythbuntu
---

### Post by A3M0N on 2011-03-12
Watching downloaded tv shows in MythVideo, they are playing letter boxed.  My tv is widescreen and connected to my MythBox via VGA.  

The files in question (from MediaInfo):
Width  : 624 pixels
Height : 352 pixels
Display aspect ratio : 16:9

The computer is outputting at 1360x768@60Hz, but the tv is reporting its resolution at 1280x768@60hz.  Not sure whats going on there, just weird.  

Any thoughts on what could be happening here?  

P4 2.66 Ghz
1 Gb ram
Radeon RV250 If [Radeon 9000]

Thanks!

*edit:* The files play fine (widescreen, fills screen up, in VLC)

---

### Post by A3M0N on 2011-03-13
Do I need to provide some more information?  Or does this really have everyone stumped?

---

### Post by newlinux on 2011-03-13
mythtv traditionally doesn't play well with ATI cards, but that may not be your problem. Have you tried adjusting your zoom or  your aspect override in the tv playback settings of mythfrontend?

---

### Post by nickrout on 2011-03-13
what is the output of ```
xwininfo -root 
```(you need to run this in a terminal, if you want to ssh in and do it, run ```
DISPLAY=0: wininfo -root
```

Also, what player are you using for videos?

---

### Post by A3M0N on 2011-03-14
From SSH:
```
(wininfo:9592): Gtk-WARNING **: cannot open display: 0:
```

I'm using the Internal player. 

I'm not an A/V guru, and have always been confused a little by aspect ratios and the widescreen tv.  16:9 material should fill the screen correct?  

I changed the aspect overide in the TV output setup to 16:9, but there are still black bars.  

Thanks!

*EDIT:*

Here is the output from the machine itself:
```
xwininfo: Window id: 0xfc (the root window) (has no name)

  Absolute upper-left X:  0
  Absolute upper-left Y:  0
  Relative upper-left X:  0
  Relative upper-left Y:  0
  Width: 1360
  Height: 768
  Depth: 24
  Visual: 0x21
  Visual Class: TrueColor
  Border width: 0
  Class: InputOutput
  Colormap: 0x20 (installed)
  Bit Gravity State: NorthWestGravity
  Window Gravity State: NorthWestGravity
  Backing Store State: NotUseful
  Save Under State: no
  Map State: IsViewable
  Override Redirect State: no
  Corners:  +0+0  -0+0  -0-0  +0-0
  -geometry 1360x768+0+0

```

---

### Post by A3M0N on 2011-03-16
> **newlinux said:**
> mythtv traditionally doesn't play well with ATI cards

Do you think the onboard Intel video will work better than the old ATI Radeon?

---

### Post by newlinux on 2011-03-16
> **A3M0N said:**
> Do you think the onboard Intel video will work better than the old ATI Radeon?

worth a shot if nothing else works. I have two intel GPUs that work well.

---

### Post by A3M0N on 2011-03-17
Well, I pulled the Radeon out and am using the onboard Intel video.  I had forgotten that the computer I'm using for my Mythbuntu box is newer than that old Radeon.  So the video is better quality, but still had to change the aspect ratio override to 4:3 (oddly) but now displays everything the way its supposed to be.  

Thanks for the help!

---

