---
title: "Tearing in X and Video playback using ATI"
date: 2008-08-03
forum: Multimedia Software
---

### Post by hxll on 2008-08-03
Hi, I'm experience tearing in both X and during video playback. Below is a screen shot taken in X when i move a window from side to side (It is the same result no matter what configuration i have used mesa, ati etc.).

I have read a lot of threads concerning the video playback issue but none of the fixes have worked for me. This tearing is present when i use mesa, ati drivers, during ubuntu installation, gparted and at boot when the orange bar is moving. I do not recall having this problem in Windows XP I have tried to reinstall windows but it corrupts the partition table so it won't boot.

**My computer:**
ATI Radeon X1950
ASUS A8R-MVP
AMD 64
Samsung SyncMaster 2493HM

Im running 2.6.24-19-generic kernel with Ubuntu 8.04 x64.

**My test results:**
**Mesa:**
*Tearing:*
	X: Yes.
	Movie: Too slow

**Envy ATI drivers:**
*Tearing:*
	X: Yes
	Movie:
		MPlayer:
			Xv: Yes
			X11: Yes (slow motion)
			gl: Yes (extremely)
			gl2: Yes (slow motion)
			
		VLC:
			Default: yes
			X11: Yes (extremely slow)
			OpenGL: Crashes.


Same result if i use aticonfig --sync-video=on, which adds the following to the device section in xorg.conf:
Option	    "VideoOverlay" "on"
Option	    "OpenGLOverlay" "off"
Option	    "TexturedVideoSync" "on"

Also the same result if i add:
Option	"TexturedVideo" "on"
and 
Option	"TexturedVideo" "off"
and
Option      "UseFastTLS" "on"
To the above options.

With these drivers the screen saver destroys they X display in some way. When the screen saver is active and i move the mouse or something to end it the screen just freezes, if i go to a console with CTRL+ALT+F1 and then back again the screen looks like the second attached image. If I let the screen saver start again when the screen is frozen i can se the screen saver moving as normal again but i can't get back to X. If i press CTRL+ALT+BACKSPACE the screen shows my desktop correctly for a second before X restarts.

**Ubuntu proprietary drivers:**
Same result as envy, except for the screen saver part. The screen saver does quit normally but it also crashes the whole system at random.

**ATI drivers from ATI's homepage:**
Same result as envy except for the screen saver part. The screen saver does make the screen look like the screen shot but switching to a console and back fixes it.

I have tried three ways to install the drivers, first the one on ATI's homepage and the second from this site: [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method_.28installing_Catalyst_8.7.29](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method_.28installing_Catalyst_8.7.29)
and third attempt i used the guide on this site: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
With the second one i could not remove the installed packages but had to reinstall ubuntu, but that's most likely because I don't know how to fix the package problem that occurred.

With The ATI drivers i have tried what the following sites says without success:
[http://ubuntuforums.org/showthread.php?t=754712](http://ubuntuforums.org/showthread.php?t=754712)
[http://www.uhlala.it/technology/linux-ati-fglrx-and-tvtime/](http://www.uhlala.it/technology/linux-ati-fglrx-and-tvtime/)
[http://ge.ubuntuforums.com/showthread.php?t=82368](http://ge.ubuntuforums.com/showthread.php?t=82368)
[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)
[http://forum.compiz-fusion.org/showthread.php?t=6957](http://forum.compiz-fusion.org/showthread.php?t=6957)
[http://ge.ubuntuforums.com/showthread.php?t=301941&highlight=flicker](http://ge.ubuntuforums.com/showthread.php?t=301941&highlight=flicker)
[http://bbs.archlinux.org/viewtopic.php?id=45524](http://bbs.archlinux.org/viewtopic.php?id=45524)

There are some compiz specific ones in there, but none of them worked with or without compiz.

I have tried the xorg.conf option DisplayPriority without any success.

I have not tried the Open source drivers.

**Other remarks:**
*SGI rendering:*
```

$ glxinfo | grep vendor
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: ATI Technologies Inc.

```
Is it suppose to use SGI as glx ?

*Direct rendering:*
With all configurations of the ATI driver i have had direct rendering
```

$ glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: Radeon X1950 Series

```

*Bios:*
I thought maybe this could be due to an old bios version but i haven't been able to download the latest drivers because asus homepage is not working. Could this be a possible solution ?

*Monitor configuration:*
I was in the IRC channel and asked for help about this, I got the suggestion that i should configure my monitor since it's just some default settings in xorg.conf. My monitor is not listed so i took the closest one and changed the minor refresh rates a bit but then X refused to load my desired resolution so i switched back to the default settings.

It doesn't feel like the monitors fault since taking a screen shot reveals the problem.

This problem is not that annoying in X but when plying movies it really bugs me. I'm open for any suggestions or explanations why this happens.

---

### Post by Siggma on 2008-11-04
:lolflag:
This is probably no consolation but I'm still stuck with Windows (Vista) for the very same reason. I'm using an X1650 and although I seem to get a little better results than you, I still see horizontal and diagonal (lightning strike) tearing during any video that requires fast just off horizontal or fully diagonal panning. It's bad enough that I can't use it. There is also no hardware acceleration support for the r500 despite their claims to the contrary. I see horrible stair stepping in Compiz for most effects but certain screensavers don't tear at all, even at very high frame rates.

[I]In comparison, the Vista driver is very nice, supports all the cards features and won't tear the video no matter what the settings or even which video player I use.
[/I]
There is a DRI utility that allows you to mess with the Direct Rendering options here if you want to mess with it but it has no effect on video output, another clue: [http://dri.freedesktop.org/wiki/](http://dri.freedesktop.org/wiki/)

Tearing can only occur when the video output hardware is writing to the screen while something else is changing memory. It's a very simple matter to write RAM only during Video refresh to prevent tearing in the video output *yet their driver has no **usable** option to prevent this occurrence*. 

TIVO uses the X window system. If it were X there would be no TIVO.

This may sound odd but I think the poor video performance is deliberate on the part of ATI and possibly others in the video industry. It think it's an attempt to steer people away from Linux towards the only other "Operating System" in the industry. There is no way the driver can play video so smoothly during straight horizontal panning but ONLY TEAR on specific types of video updates, like diagonal panning. The hardware is clearly capable and although X has some video issues, video playback does not depend specifically on X for full screen output. In many ways it's worse than a Pentium 90 driving an old Chinese 8 meg card. *Note there is no Xvidix driver for these cards either, due in part to the lack of hardware references from which to code them.*

I suspect the newer ATI cards will be obsolete before there are usable video drivers for them. [Phoronix.com]("http://www.phoronix.com/scan.php?page=home") is the semi-official place to get ATI/AMD hype about why this or that won't work. It's curiously disorganised and the "Bridgeman" character is either mentally retarded (acting like he has no idea what's going on until you ask a specific question, then it's mostly blame) or he's there simply to calm the masses while the cards get old, people get fed up and either move back to Microsoft or try another vendors hardware.

Lastly, these newer 3D cards are different to be sure. Most don't have any hardware "overlay". They render video at the output (mixer) rather than painting a chromatic XV Window so multiple videos can play simultaneously. Remember how annoying it was when only one video could play at a time? Still, full screen output can easily bypass any X limitations but does not. It would only take a couple hours to write a working full screen video playback routine for any video card if you have the hardware specs. In the end it's up to you...or it is?
-Tom

---

### Post by L815 on 2008-11-04
This is also the reason why I haven't fully switched to Ubuntu. Majority of the other issues I had are fixed or not a big problem, but this one is a bit annoying.

I watch a lot of flash and video and it is really annoying having to be distracted by tearing.

It's not a compiz issue because it happens it on and off. I just can't wait till the day it is fixed!


Oops, forgot to mention I'm on an intel gm965 card ;p

---

### Post by jengo on 2008-11-04
i was having a lot of problems with an older video card as well, I found the following guide EXTREMELY useful. 

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Hope that helps!

---

### Post by radox1912 on 2009-01-19
bump ?

---

