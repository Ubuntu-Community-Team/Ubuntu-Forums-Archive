---
title: "ati tv out video is cut in half"
date: 2006-10-14
forum: Multimedia &amp; Video
---

### Post by threedguy on 2006-10-14
I've managed to install ati's drivers and I've managed to get them to output to my tv using the s-video output, with the tv set as primary, but my only problem is video files played in a video player are like cut in half.  It's like the window is too small for the video.  Changing resolutions doesn't seem to help.  I've tried looking all over the forums and google for a solution to this problem and I can't seem to find anything.  Any suggestions?

---

### Post by threedguy on 2006-10-16
Does anybody have any idea where to even start on solving this problem?  I've had so much trouble getting this stupid card to work, I'm starting to consider dishing out the money for an nvidia...

---

### Post by nalmeth on 2006-10-16
That is a weird problem..
Perhaps changing the -vo driver in your video player would make a difference.
Totem doesn't have this option, but if you use mplayer, vlc, or just about anything else, you can change this driver. It's probably set to XV, try changing to X11.
Also, if you're using the totem player that came with ubuntu, try installing totem-xine instead. It will replace totem-gstreamer, and might solve the problem aswell.
Good luck, and definitely think about Nvidia next time.

---

### Post by threedguy on 2006-10-18
yeah, that fixed it.  At first, i switched to just X11 mode and then full screen didn't take up the whole screen, but X11(Open gl) seems to do the trick just fine.  Thanks for the help.  Yeah, i had already pretty much given up on totem, it doesn't seem to want to play anything.  Mplayer is much better in my opinion.

---

### Post by junkalam on 2006-11-25
Totem doesn't have the option to change the driver in the GUI, I hope its added in future versions. In the mean time you can always edit its config file:

```
gksudo gedit ~/.gnome2/totem_config
```

find this block:

```

# video driver to use
# string, default: auto
# video.driver: auto

```

change it to:

```

# video driver to use
# string, default: auto
video.driver:OpenGL

```

Start up Totem & it should work fine

---

### Post by mkljun on 2007-08-14
This solusion only works for totem. If you want a general solution (for all players) then set VideoOverlay in xorg.conf to off ([http://ubuntuforums.org/showthread.php?t=290048](http://ubuntuforums.org/showthread.php?t=290048)).

I added my device section from xorg.conf below. I use fglrx driver (since with oss driver my tv-out did not work). When I had VideoOverlay to on I saw only upper half of the video. With VideoOverlay set to off I can see whole video. The older fglrx driver did not have this problem though. It happened when I upgraded to 7.04.

How to install fglrx drivers can be found here: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-796aa4d6d0477c8ed722acef1878cc5626855ae3](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-796aa4d6d0477c8ed722acef1878cc5626855ae3)

Device section from xorg.conf.

```

Section "Device"
	Identifier	"ATI Technologies Inc RV350 AP [Radeon 9600]"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
        Option "VideoOverlay" "off"
        Option "OpenGLOverlay" "on"
        # ########## disable PnP Monitor ##########
        Option "HWcursor" "yes"
        # ### generic DRI settings ###
        Option "NoTV" "no"
        Option "TVFormat" "PAL-G"
        Option "TVStandard" "COMPOSITE"
        Option "TVHSizeAdj" "0"
        Option "TVVSizeAdj" "0"
        Option "TVHPosAdj" "7"
        Option "TVVPosAdj" "0"
        Option "TVHStartAdj" "0"
        Option "TVColorAdj" "0"
        Option "GammaCorrectionI" "0x06419064"
        Option "GammaCorrectionII" "0x06419064"
        # this extends monitor (TV) to the right
        Option "DesktopSetup" "0x00000200"
        Option "MonitorLayout" "AUTO,AUTO"
EndSection

```

---

