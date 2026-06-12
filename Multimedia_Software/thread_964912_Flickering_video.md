---
title: "Flickering video"
date: 2008-10-31
forum: Multimedia Software
---

### Post by whoelse on 2008-10-31
Hi, I updated to 8.10 and everything is working fine except video playback.

The video is flickering, I cannot describe it in a better way.

I have tested different formats (avi, wmv) with different players (totem, vlc) and I have always the same result.

I have tried to deactivate my ATI-card but no improvement.
Any ideas. I would be grateful for any help.


BTW: Flash videos are working without any problems.

---

### Post by Andrewsha on 2008-10-31
I have the same problem.

---

### Post by whoelse on 2008-10-31
> **Andrewsha said:**
> I have the same problem.
Do you also have an ATi-card?

---

### Post by Andrewsha on 2008-10-31
No, i have:
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)

Or is it ATI?

---

### Post by horde on 2008-10-31
Me too.  New upgrade to Intrepid (Kubuntu) with ATI Radeon Mobility X1400 and repository drivers.  

Selecting OpenGL video in VLC gives very flickery video. Choosing X11 video output is better but still not very smooth, especially at fullscreen, and the higher the resolution the worse it gets.

Based on the following thread I've modified my xorg.conf (also below) though it hasn't helped much:
[http://ubuntuforums.org/showthread.php?t=953745&highlight=Errors+were+encountered+while+processing%3A+fglrx-kernel-source_8.542-0ubuntu1_i386.deb&page=3]("http://ubuntuforums.org/showthread.php?t=953745&highlight=Errors+were+encountered+while+processing%3A+fglrx-kernel-source_8.542-0ubuntu1_i386.deb&page=3")

Any help would be greatly appreciated!


```
Section "ServerLayout"
        Identifier     "aticonfig Layout"
        Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
        Load  "glx"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]-0"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]-0"
        Driver      "fglrx"
        Option      "TexturedVideo" "on"
        Option      "VideoOverlay" "off"
        Option      "OpenGLOverlay" "off"
        Option      "Textured2D" "on"
        Option      "TexturedXrender" "off"
        Option      "UseFastTLS" "1"
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]-0"
        Device     "aticonfig-Device[0]-0"
        Monitor    "aticonfig-Monitor[0]-0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

Section "DRI"
        Mode         0666
EndSection
```

---

### Post by whoelse on 2008-10-31
Okay, VLC with X11-output works quite fine, but Totem and Co still have the problem.

---

### Post by MightyBigMinus on 2008-11-01
Same, details if it helps:
- 8.10 64-bit fresh install
- dell optiplex 755
- ati hd 2400 pro
- I opted to install the non-free driver when the Hardware Drivers program prompted me (fglrx)
- I have dual monitor enabled via Applications-> Accessories -> ATI Catalyst Control Center -> Display Manager -> Multi-Display -> Big Desktop right of display 1
- wmv, xvid/avi, and mpeg are all affected the same
- vlc with x11-output doesn't flicker, but is choppy and every time I open a new video blanks the screen for a second.

---

### Post by milkathecow on 2008-11-01
have noticed that i had that on my ATI radeon mobility card... but only when i was on "extra" mode for the visual affects. it's fine on basic and "normal" modes.

---

### Post by Stex on 2008-11-01
If you haven't already try running (Alt+f2) [COLOR="DarkGreen"]gstreamer-properties[/COLOR]

In the video tab try a selection of the output options, these affect programs using gstreamer (e.g. totem).

---

### Post by pauloslf on 2008-11-01
thanks Stex it worked just fine for me (intrepid ati x1700)

---

### Post by jimminy_cricket on 2008-11-01
I am having the same problem, when I checked the gstreamer-properties the x window system (no Xv) option worked in the test when all the others didn't.  Vlc is still going nuts with video playback though.

Any more ideas?

Also; 01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series (and I do have the proprietary drivers turned on)

---

### Post by tomkinsc on 2008-11-01
I have the same problem on an ATI HD4850.
If I switch to X11 as the output, VLC crashes when in full screen.

---

### Post by jimminy_cricket on 2008-11-02
bump?

---

### Post by neorg on 2008-11-02
Same problem here.

ASUS V51V-series
ATI Technologies Inc Mobility Radeon HD 3400 Series
Intredip 8.10


Use VLC with the option **X11 display** set to **:1**
To set that option go to:
- Preferences -> Video -> XVideo
- select **All** by Show settings
- fill in :1 by X11 display

No fix, but now you can watch video without flickering :)

---

### Post by costre on 2008-11-02
I had the same problem on a laptop running Ibex.

It wasn't just vlc, all overlay video flickered, on web pages, plugins, all different players displaying video.

I uninstalled Compiz, and all was completely fine. No other modifications needed here.

---

### Post by tomkinsc on 2008-11-02
I was able to find a temporary workaround by installing fusion-icon
```
sudo apt-get install fusion-icon
```
It allows one to toggle between window managers. Switching from Compiz to metacity before watching a video does the trick.  It's not ideal, but it will do until someone has a better solution.

---

### Post by NightSt@lk3r on 2008-11-02
If using ATI and your video only flickers when compiz effect are enabled then under the device section of xorg.conf under the driver option add

Option      "TexturedVideo" "off"

This should fix it, you could try it with other display adapters but don't blame if it it messes up.

---

### Post by alwayshere on 2008-11-02
compiz switch [http://forlong.blogage.de/entries/pages/Compiz-Switch](http://forlong.blogage.de/entries/pages/Compiz-Switch)

try it

---

### Post by neorg on 2008-11-03
> **NightSt@lk3r said:**
> 
Option      "TexturedVideo" "off"


Fixed the problem for me. 
ATI Technologies Inc Mobility Radeon HD 3400 Series

Thanks!

---

### Post by jimminy_cricket on 2008-11-03
Turning compiz off worked for me... Does that mean that someone broke compiz in the upgrade?

---

### Post by GZ Expat on 2008-11-04
> **whoelse said:**
> Okay, VLC with X11-output works quite fine, but Totem and Co still have the problem.

This worked just fine for me...besides VLC is ALL I need.

---

### Post by nickpick on 2008-11-04
> **NightSt@lk3r said:**
> If using ATI and your video only flickers when compiz effect are enabled then under the device section of xorg.conf under the driver option add

Option      "TexturedVideo" "off"

This should fix it, you could try it with other display adapters but don't blame if it it messes up.

Worked for me, thanks bud.

---

### Post by ajitp on 2008-11-04
tried that modification to the xorg.conf but it didn't solve the problem. is their a bug report about this? maybe a compiz update will fix this?

---

### Post by devoda on 2008-11-04
I also have this problem with Ubuntu 8.10 i386 and fglrx driver on a ATI Technologies Inc Mobility Radeon HD 3400 Series. When changing output on VLC to x11 instead of OpenGl, the flickering stops. Then the video is choppy instead of flickering. I know this is due to the lack of video acceleration in X11 video output mode. Changing output mode to X11 is not an option because it is just as annoying as the flickering to have frames dropped left and right. Also the suggestion to add Option "TexturedVideo" "off" did not help.

      I'm guessing we all are going to have to wait for a new fglrx driver from ATI or switch to the open source driver (which is what i'm about to do).

---

### Post by dlstyley on 2008-11-05
> **NightSt@lk3r said:**
> If using ATI and your video only flickers when compiz effect are enabled then under the device section of xorg.conf under the driver option add

Option      "TexturedVideo" "off"

This should fix it, you could try it with other display adapters but don't blame if it it messes up.

This worked for me.  ATI Radeon X1200 series.

---

### Post by whoelse on 2008-11-05
So, five days of discussion and nothing specific what is messed up.

Just to everyone who reads this thread things which could help:

1) Changing the output of VLC to X11 (of course this only works for VLC)
2) Disabling all visual effects (did the trick for me)
3) Uninstalling Compiz
4) Adding *"Option "TexturedVideo" "off"* in the driver section in xorg.conf

I have only tried the first two things, so I cannot say anything about the other two.

---

### Post by horde on 2008-11-06
I've done the following, but no improvement:
1) ' Option "TexturedVideo" "off" ' in xorg.conf
2) Disabled all visual effects
3) Uninstalled Compiz
4) Changed output in VLC to X11 (which makes video choppy instead of flickery)

Is devoda correct...is this simply a deficiency in the new fglrx driver?  Also can someone please post their experiences with the open-source driver?

Many thanks.

---

### Post by neorg on 2008-11-06
After the latest kernel update this morning I have no flickering video any more. 

- Totem is Perfect!
- VLC is perfect (I even removed the :1 in VLC X11 ouput)

---

### Post by Open-SuSe-A-Me on 2008-11-06
hello 

i have an integrated intel 965 graphics card and video will not play right as it did in hardy.  this is true with or without compiz enable and even with compiz completely uninstalled.  the video flickers/tears like crazy.

most of the fixes on the forums talk about not using compiz.  i thought the intel drivers were supposed to be very linux friendly and video works flawlessly on hardy right out of the box.  there must be something terribly wrong here.

i have found one temporary fix - alt+F2 gstreamer-properties and selecting "Video Overlay".  this makes video play fine in Totem but i hate totem and while this setting is on my screen will flicker alot.  VLC and Mplayer flicker on every video output setting.

any help would be great - thanks.

---

### Post by tuxsheadache on 2008-11-08
When I went to my xorg.conf to edit it all I got was:

#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection


Any advice?

---

### Post by neorg on 2008-11-08
> **tuxsheadache said:**
> When I went to my xorg.conf to edit it all I got was:

#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection


Any advice?


Add the line:

   Option "TexturedVideo"                  "off"

in the Device section.

The device section looks like this 
```
Section "Device"
        Identifier      "Configured Video Device"
        Driver  "fglrx"
        Option "TexturedVideo"                  "off"
EndSection
```

NOTE: you can edit your xorg.conf with the command:
```

sudo gedit /etc/X11/xorg.conf

```

---

### Post by tuxsheadache on 2008-11-08
Thanks for the code to edit xorg.conf =)
Sadly my video is still flickery, with compiz enabled or compiz disabled =(

---

### Post by lovinglinux on 2008-11-09
EDIT: I finally solved the problem on my machine by enabling "Unredirect Fullscreen Windows" under CCSM General options:popcorn:

---

### Post by ramnarayan on 2008-11-10
> **Stex said:**
> If you haven't already try running (Alt+f2) [COLOR="DarkGreen"]gstreamer-properties[/COLOR]

In the video tab try a selection of the output options, these affect programs using gstreamer (e.g. totem).

Thanks Stex , works for me 
chose X Window No XV 

will figure out what the compromise is later on

ram

---

### Post by tsbaker on 2008-11-11
VLC and MPlayer work fine now after reading this post. Totem still doesn't though. However it's not choppy video that I'm getting, it's an error "can't determine stream"

---

### Post by ALRD on 2008-11-12
I had the same problem with video playback after an upgrade to 8.10. When I had compiz effects enabled both VLC and Totem showed a flickering picture. 
This is what solved it for me: 

VLC
Open vlc and go to preferences--> video--> set output module to X11 video output.

Totem
launch (alt+f2) "gstreamer-preferences"
go to video and set default output to X window system

Hope it helps,

---

### Post by sionco on 2008-11-12
Hi,
just incase it's any use to anyone,
 I had the same problem
I have a toshiba satellite pro l20 with ATI Radeon Xpress 200M graphics.
I also have ubuntu 8.10

I had the problem of flicking video or stuttering video, no matter what program I used (vlc/totem) or if I changed the output module of VLC, and also I had flicking in 3d games, all with the ati proprietary driver.

I solved it by unistalling the driver,
and following the following instructions at the unofficial ati linux driver wiki [http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Installation]("http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Installation").

The video runs perfectly, and i can play 3D games, but only when I disable the desktop visual effects. 
However, I like the visual effects, so untill theirs a fix or a better way, I have the visual effects enabled until I want to watch a video, where I  quickly right click the desktop and disable the visual effects

---

### Post by sionco on 2008-11-12
oops

---

### Post by gsxrmike04 on 2008-11-12
none of these worked for me :(

---

### Post by jdorenbush on 2008-11-12
> **Stex said:**
> If you haven't already try running (Alt+f2) [COLOR="DarkGreen"]gstreamer-properties[/COLOR]

In the video tab try a selection of the output options, these affect programs using gstreamer (e.g. totem).

This worked. Set the output to "X Window System (No Xv)"

Also turning off Visual Effects worked.

VLC seemed to work OK, but I don't like VLC because there is no video controls when streaming video.

---

### Post by tchalvakspam on 2009-02-04
> **ALRD said:**
> I had the same problem with video playback after an upgrade to 8.10. When I had compiz effects enabled both VLC and Totem showed a flickering picture. 
This is what solved it for me: 

VLC
Open vlc and go to preferences--> video--> set output module to X11 video output.

Totem
launch (alt+f2) "gstreamer-preferences"
go to video and set default output to X window system

Hope it helps,

Those two video player choices worked for me also, essentially changing things from the default streaming method or whatever to a specific one, in this case the choices above.

---

### Post by horde on 2009-02-04
My solution for the past few months now has been to set output module to X11 video output and, when I watch videos, decrease my video resolution from 1920x1200 to 720x480.  It's a pain but I only have to do it when I watch video fullscreen.  Hopefully this problem is being looked into by the developers...

---

### Post by SVEN1 on 2009-02-11
By reading a possible solution in another post. i turned off Special effects under
Systems-Preferences-Appearance-Visual Effects
to the NONE setting.:)

But I liked the special effects...

---

### Post by greenjumper on 2009-03-03
> **alwayshere said:**
> compiz switch [http://forlong.blogage.de/entries/pages/Compiz-Switch](http://forlong.blogage.de/entries/pages/Compiz-Switch)

try it

This is a very handy little program for people with this problem!

---

### Post by horde on 2009-03-25
I got sick of the work-arounds, so I uninstalled fglrx packages and am using the FOSS radeon packages.  Obviously doesn't work as well as the binary from ATI (when it actually worked for me), but is much less hassle for now.  I may try getting the latest ATI binary to work if this isn't satisfactory over time.

---

### Post by scan1 on 2009-03-26
I'm very angry.

Stupid ati card.

I have the same problem with video flickering.

tried everything.

Newest ati driver too, but nothing.

How hard is to make a decent thing to work? You have nvidia, ati and intel video cards and it was that hard to make them all work?

At least on windows everything works. Ubuntu makes vista look good.
I can't even have a fullscreen video playback. And I don't want to turn stuff off, I want them to work.

Ubuntu 8.04 - desktop: athlon xp 1.9 ghz, 1.5 gb ram, nvidia fx 5600 128mb 
EVERYTHING WORKS PERFECTLY

Ubuntu 8.10 - laptop: intel dual core 2 ghz, 2 gig ram, ati hd 3470 512 mb
VIDEO PLAYBACK SUX, FULSCREEN VIDEO DOESN'T WORK, HD LAGS

nice update ubuntu,thanks for nothing

So I have to boot to windows to watch a movie?

Christ...

---

### Post by Melcar on 2009-03-26
Video/games flickering with Compiz running = normal and due to DRI.  Every driver out there (except nvidia, since they don't use X) suffers from this in varying degrees of severity. Only way to get around it currently is to either turn off Compiz (or whatever composite manager you're using) or switch to the slower X11 output (only works for videos).
The long term solution is DRI2, which is being worked on.  The latest fglrx (for ATI users) offers flickerless accelerated games/videos as long as they're in fullscreen mode.

---

### Post by scan1 on 2009-03-26
thanks for the reply man

I know that problem is with ati, just red on another forum that they
hope to fix this in this year!!! 2009!!!

Normal video playback in 2009 wow:-\"

Nvidia should buy ati and close them down. (like 3dfx)

---

### Post by Melcar on 2009-03-26
It's not a driver problem, but a limitation of the X infrastructure in Linux.  You can't really blame ATI for that.

---

### Post by tchalvakspam on 2009-03-29
Keep in mind that there are other steps to try as well, like changing the preferences > "multimedia systems selector" options.

---

