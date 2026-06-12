---
title: "Fixed My Flash full screen performance"
date: 2009-09-20
forum: Multimedia Software
---

### Post by StevenHarper on 2009-09-20
Hi I am on Ubuntu 9.04 64bit
I am running Compiz effects
I have a 4870 ATI card with the binary drivers installed.

Previously iPlayer and Youtube full screen performance was very poor.  In both Firefox 3.0 and Chromium.

It appears that the problem was the flash (I use the standard ubuntu repository version) I have is not detecting the hardware excleration and is leaving it off.  

To fix this a config file is needed to turn off the hardware detection.

basically I put the text **OverrideGPUValidation = 1** in a file at **/etc/adobe/mms.cfg** and re-start the browser.

Such a simple fix.

Here is how to do it in steps

```

sudo touch /etc/adobe
sudo gedit /etc/adobe/mms.cfg

```

Paste in the text

```
OverrideGPUValidation = 1
```

Save the file.

Open a browser.

Enjoy fast full screen video.

Please post if this works for you : I am so pleased it has worked for me.

*** Edit

If this still doesn't seem smooth try right clicking on the flash object and un-checking the "enable hardware excleration" box

---

### Post by UKBB on 2009-09-25
When I run these two commands gedit tells me no such directory exists.

sudo touch /etc/adobe
sudo gedit /etc/adobe/mms.cfg

---

### Post by gabi83tm on 2009-09-30
> **UKBB said:**
> When I run these two commands gedit tells me no such directory exists.

sudo touch /etc/adobe
sudo gedit /etc/adobe/mms.cfg

I got that same error because I didn't have an adobe directory, and the touch command creates a file instead of a directory.

So, I first deleted the file I just created, then created a folder with the same name, and then put the mms.cfg inside it.

sudo rm /etc/adobe
sudo mkdir /etc/adobe
sudo gedit /etc/adobe/mms.cfg

Then I restarted my browser.

BUT it still didn't do the trick.

Anyhow, right clicking on the flash object and un-checking the "enable hardware acceleration" box slightly improved the performance, but still not good enough. I think I'm going to install the Video Download Helper extension and just download the videos I really want to see in full screen.

LATER EDIT: Yeah, Video Download Helper extension for Firefox is a reasonable solution. You can even view videos while they're downloading.

---

### Post by pkchips on 2010-05-03
Hello guys, does anyone know how to get this fix working in Ubuntu 10.04?

It worked great for me in 9.04, suddenly my Youtube videos played full speed in fullscreen resolution at 1080p.

Before the fix, I couldn't even run a 360p video without it being really choppy.

However, the same fix doesn't seem to work on 10.04... :S

---

### Post by ram130 on 2010-05-03
same here..anyone???

---

### Post by AlexanderDGreat on 2010-05-15
Nope didn't work for me tried it on Firefox and Chrome, full screen looks like 16:9 aspect ratio. Any help? Thanks.

---

### Post by radko.dinev on 2010-08-17
Right clicking on any flash video, then "Settings", "Display" tab (the first one) and uncheck "Enable hardware acceleration".

That fixed the choppy poor performance Flash when in full screen. Now 720p HD flash videos (on YouTube) run smoothly in full-screen (using Intel Core 2 Quad, Intel On-Board GMA 4500 HD).

---

### Post by ram130 on 2010-08-17
Doesn't work for ATI

---

### Post by pmbsa on 2010-08-26
Anybody managed to get this working on Lucid, I have tried all these little tricks and it makes no difference. The result is still a very choppy fullscreen flash.

I am running Lucid on a Zotac Nvidia ION chipset.

Has anybody perhaps managed to get something playing nicely on a browser in wine, I would gladly do that as an alternative if it works.

thanks
Paul

---

### Post by no2498 on 2010-08-26
write down your settings first so if need to be set back. and try this

5.1.&#8195;The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
      This means, that your cpu is doing all the work. Change it to "xvimagesink"
      ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and change the appropriate settings.

---

### Post by pmbsa on 2010-08-30
Hi, I gave that a try with no success. Is this a new issue that is suddenly appearing in Lucid or is it a general issue with Adobe Flash at the moment on linux?

---

### Post by rawlins02 on 2010-08-30
I just tried the OverrideGPUValidation = 1 suggestion.  No improvement. I should mention that with Flash 10 I had to disable hardware acceleration (right click on the video) to prevent Flash from crashing.  Videos run fine when not in fullscreen mode.  In fullscreen it essentially pauses every 2-3 seconds.  I understand Flash in fullscreen does not run well on many systems.

My system is Dell Studio XPS 1645, Intel(R) Core(TM) i7 CPU Q 820 @ 1.73GHz, 8GB RAM, ATI Mobility Radeon HD 4670, Lucid Lynx.  

Funny, my 5yo Lenovo T60 with Radeon X1400, duo core 1.83 GHz, 2GB RAM plays Flash in fullscreen well, particularly in Windoze XP.  Not good....

---

### Post by egprince on 2010-09-10
> **radko.dinev said:**
> Right clicking on any flash video, then "Settings", "Display" tab (the first one) and uncheck "Enable hardware acceleration".

That fixed the choppy poor performance Flash when in full screen. Now 720p HD flash videos (on YouTube) run smoothly in full-screen (using Intel Core 2 Quad, Intel On-Board GMA 4500 HD).

this fixed it thanks alot

---

### Post by MrWestwood on 2010-09-10
None of the above suggestions have worked for me. 

I have done the GPU validation thing, I've done the mms.cfg thing and I've just tried unticking disable hardware acceleration.

I have Intel core 2 duo 2.33Ghz, 2 gig of Ram and I'm running Lucid 64.

Added: Since unticking the acceleration button in flash I get more crashes.

Are canonical going to address this issue? It's getting pretty poor now. I love Ubuntu and will rave about it to most people but this is just embarrassing. How am I supposed to put Lucid on the odd netbook if when people ask if they can use Youtube I have to tell them "yes but not very well". 

I don't think the thread title should have the SOLVED prefix either as it clearly isn't.

---

### Post by caeroe on 2010-09-11
Ubuntu blames Adobe, Adobe blames Linux.  The problem won't be fixed.  
My desktop, however, has enough power behind it where it can handle the sluggish performance of Flash in Linux.  My netbook does not, so I had to put WinXP on it to get the most out of the device.
So the only "solution" is a work-a-round.  The point of me getting a netbook was to take it with me, enjoy web content, etc.  I cannot do that (fully) with UNR.

---

### Post by ram130 on 2010-09-11
> **caeroe said:**
> Ubuntu blames Adobe, Adobe blames Linux.  The problem won't be fixed.  
My desktop, however, has enough power behind it where it can handle the sluggish performance of Flash in Linux.  My netbook does not, so I had to put WinXP on it to get the most out of the device.
So the only "solution" is a work-a-round.  The point of me getting a netbook was to take it with me, enjoy web content, etc.  I cannot do that (fully) with UNR.

sucks really..:-|

---

### Post by pmbsa on 2010-09-18
sorry, posted to wrong topic! cant work out how to remove it

---

### Post by MrWestwood on 2010-09-18
Found something that helps the full screen playback issue on 64 bit OS. There's a 32 bit version available too but I don't think Ubuntu 32 has the problem.

The frame rate seems better but it still slightly hangs when you move the mouse.

Download the latest release: [http://download.macromedia.com/pub/labs/flashplayer10/flashplayer_square_p1_64bit_linux_091510.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer_square_p1_64bit_linux_091510.tar.gz)

sudo apt-get remove --purge flashplugin-* swfdec-mozilla swfdec-gnome mozilla-plugin-gnash gnash
  
   
and then extract attached in ~/.mozilla/plugins/ create folder if not there.


A mate of mine found this so I woe him the credit.

---

### Post by AlexanderDGreat on 2010-09-19
It's the weirdest thing. I have 2 computers, 1 in the office and 1 at home. The one in the office Flash Full Screen is working fine!

But the one I have at home has the problems. I don't know why. Aren't they the same Ubuntu Lucid Lynx 32 bit?

So is this a hardware specific problem now? Nope, I didn't LOCK any kernel upgrades. They're basically the same. Everything.

---

### Post by MrWestwood on 2010-09-19
> **AlexanderDGreat said:**
> It's the weirdest thing. I have 2 computers, 1 in the office and 1 at home. The one in the office Flash Full Screen is working fine!

But the one I have at home has the problems. I don't know why. Aren't they the same Ubuntu Lucid Lynx 32 bit?

So is this a hardware specific problem now? Nope, I didn't LOCK any kernel upgrades. They're basically the same. Everything.

From what I have read, the problem only affects 64 bit OS.

You could use uname -m 

x86_64 = 64 bit
i686 = 32 bit

After further reading, some clever chap has suggested 64 bit OS users install the 32 bit Firefox. I may give this a try tomorrow and post my results.

---

### Post by fogNL on 2010-09-26
Same problem here, full screen flash is choppy when watching online streams.

Tried the /etc/adobe/mms.cfg trick and the unchecking of hardware acceleration in the settings.

Setup:

Zotac Mag HD ND01 - nvidia ion 330
Ubuntu 10.04 64bit minimal install with Openbox WM
Flash: flashplayer_square_p1_64bit_linux_091510 (tried different ones)
Browsers: Firefox and Chrome

---

### Post by AlexanderDGreat on 2010-09-26
**Can somebody please mark this as UNSOLVED?** There's no way something is solve here when we still have problems!

---

### Post by Aengus on 2010-10-02
I am running Lucid Lynx 10.04 and I have not been able to solve this problem using the fixes in this thread. I agree, can someone at least mark this as unsolved if we can't find a real fix?

---

### Post by Xenphor on 2010-10-13
I still have choppy full screen flash as well on an intel 915gm. Fullscreen works fine in windows xp.  The fixes did not work for me. I am on maverick.

---

### Post by AlexanderDGreat on 2010-10-23
**not solved yet**

---

### Post by ram130 on 2010-10-23
> **alexanderdgreat said:**
> **not solved yet**

+1                        .

---

### Post by dentaku65 on 2010-10-23
You can look to my guide regarding FF and Flash for Ubuntu 10.04 32bit

[http://ubuntuforums.org/showthread.php?t=1533664](http://ubuntuforums.org/showthread.php?t=1533664)

:)

---

### Post by coatik on 2010-10-28
The mms.cfg trick alone didn't work on my amd64 lucid lynx box.
I had to "upgrade" to the adobe development 64bit flash plugin as described here:
[https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins](https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins)

Combining both, flash videos are a lot better in full screen. It take about 10-20 seconds until the video stops dropping frames (buffering??) but then it's smooth even in full screen.

Hope it helps

---

### Post by Tian102983 on 2010-10-29
I find right clicking the flash video, and disable the hardware acceleration works, to make full screen run smoothly. And I didn't need to download anything or change anything in Terminal.

---

### Post by HeYzN on 2011-01-10
only thing that solved this issue for me - lenovo t61, ubuntu 10.04 LTS  with nvidia graphics card - was to change driver for nvidia from  recommended version to 173.
issue solved on both firefox and chrome (each running their own flash plugin)

How to:
 system -> administration -> hardware drivers
 this opened for me a window with two options for the nvidia proprietary driver
 - NVIDIA accelerated graphics driver (version 173)
 - NVIDIA accelerated graphics driver (current version) [Recommended]
 
 click activate button for 173 version. after install restart computer.
 
flash videos now work in full screen without problems and high quality/speed. :)
 no need to disable hardware acceleration either.

---

### Post by MrWestwood on 2011-01-11
> **HeYzN said:**
> only thing that solved this issue for me - lenovo t61, ubuntu 10.04 LTS  with nvidia graphics card - was to change driver for nvidia from  recommended version to 173.
issue solved on both firefox and chrome (each running their own flash plugin)

How to:
 system -> administration -> hardware drivers
 this opened for me a window with two options for the nvidia proprietary driver
 - NVIDIA accelerated graphics driver (version 173)
 - NVIDIA accelerated graphics driver (current version) [Recommended]
 
 click activate button for 173 version. after install restart computer.
 
flash videos now work in full screen without problems and high quality/speed. :)
 no need to disable hardware acceleration either.


This worked for me too. Thanks.

---

### Post by Meneltaur on 2011-02-12
> **StevenHarper said:**
> Hi I am on Ubuntu 9.04 64bit
I am running Compiz effects
I have a 4870 ATI card with the binary drivers installed.

Previously iPlayer and Youtube full screen performance was very poor.  In both Firefox 3.0 and Chromium.

It appears that the problem was the flash (I use the standard ubuntu repository version) I have is not detecting the hardware excleration and is leaving it off.  

To fix this a config file is needed to turn off the hardware detection.

basically I put the text **OverrideGPUValidation = 1** in a file at **/etc/adobe/mms.cfg** and re-start the browser.

Such a simple fix.

Here is how to do it in steps

```

sudo touch /etc/adobe
sudo gedit /etc/adobe/mms.cfg

```Paste in the text

```
OverrideGPUValidation = 1
```Save the file.

Open a browser.

Enjoy fast full screen video.

Please post if this works for you : I am so pleased it has worked for me.

*** Edit

If this still doesn't seem smooth try right clicking on the flash object and un-checking the "enable hardware excleration" box

Hello,
I am new to Ubuntu and this is my first post here, I am pleased to see how far Linux has progressed since I first tried it in the 90s - back then we had to fool around with hard disk cylinder information just to get it to recognize a 2 Gig hard disk.  I recently installed 10.10 on an HP Pavillion dv6700 laptop, and noticed that the memory usage was much better than Windows Vista (idle, Ubuntu uses ~250 MB, Vista eats up 1.3 Gigs).  And my laptop does not seem to heat up and turn on the fan as often.

One of the things we often do with this laptop is to watch flash videos in full screen mode, on an external monitor.  For this I noticed a problem with Firefox, Chromium and Opera, until I realized it was a problem with Adobe Flash.  I tried the technique of setting OverrideGPUValidation in the mms.cfg in /etc/adobe, and it worked.  However I followed the instructions listed here:

[http://www.omgubuntu.co.uk/2010/06/fixing-fullscreen-flash-in-ubuntu-10-04/](http://www.omgubuntu.co.uk/2010/06/fixing-fullscreen-flash-in-ubuntu-10-04/)

For some reason, it states to uncheck hardware acceleration in a flash video first, then create the file, then to turn hardware acceleration back on, then restart firefox.  Not sure if all those steps are necessary, but it worked.  For stuff like this, this is why Windows still wins on the desktop over Linux.  I was about to give up this Ubuntu over this one issue, luckily these online forums are here.

I hit one other snag in getting fullscreen flash to work:  I often put my browser in the external monitor, which is connected to my laptop through the external VGA port.  My laptop screen runs in 1280x800, and the monitor displays an extended desktop in 1360x768 (which for some odd reason is listed as 1280x768 in Windows Vista).  When I try to run flash in fullscreen mode, the fullscreen flash then pops up on my laptop screen and my monitor is still showing the browser with the embedded flash video.  How to fix this?  I first just turned off my laptop and had only the monitor running: fullscreen flash worked perfectly on the external monitor.  However I do want both screens running, so I tried another technique: instead of having the monitor to the right of my laptop screen, I shifted it to the left.  With this configuration, fullscreen flash works on the monitor and I can still work on my laptop screen.  Unfortunately, due to the different resolutions, it seems that the top bar in my Gnome desktop on the laptop screen turns completely black, where I can not see any of the icons.  I can still put my mouse there and access the icons, but I have to guess where they are.  This probably has to do more with the different resolutions, with the height of the left screen taking priority over the right screen.

Any workarounds for this?  I am suspecting somehow we have to configure a setting which gives the right screen priority over the left screen for fullscreen flash viewing on an external monitor.

EDIT:  I just did some further research, there is another thread on fullscreen flash appearing in the wrong monitor in another thread on Ubuntu: [http://ubuntuforums.org/showthread.php?t=973631&page=2](http://ubuntuforums.org/showthread.php?t=973631&page=2).  It would seem this is a bug with desktop affects.  I went to System -> Appearance -> Visual Effects and selected **NONE**.  This did the trick.  I now have fullscreen flash on an external monitor with my laptop screen intact!!  This was not an easy problem.  Looks like an Ubuntu Gnome bug?

---

### Post by V3n0M-79 on 2011-03-26
Thanks! Worked for me also by _disabling Hardware Acceleration_ on flash.

To do that, just go to [COLOR="Red"]youtube[/COLOR], open a random video and set it to pause. Then right click, select "Settings" and turn off Hardware acceleration.

That was the key issue for me!

Ubuntu - Lucid Lynx i686 with ATI HD5870 and ATI Proprietary Fglrx Drivers (11.2)

This is my xorg:

```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
	Option	    "AIGLX" "on" #->Enables Xorg's AIGLX rendering technic
EndSection

Section "Module"
	Load  "bitmap"
	Load  "extmod"
	Load  "int10"
	Load  "vbe"	# slowdown compiz?
	Load  "i2c"
	Load  "ddc"
	Load  "dri"
	Load  "dri2"
	Load  "glx"
	Load  "GLcore"
	Load  "dbe"
	Load  "drm"
	Load  "v4l"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Option	    "VideoOverlay" "on"
	Option	    "DRI"
#	Option	    "renderAccel" "true"
#	Option	    "UseFastTLS" "0"
#	Option	    "AddARGBGLXVisuals" "true"
#	Option	    "XAANoOffscreenPixmaps" "on"
#	Option	    "TexturedVideo" "off"
#	Option	    "CideoOverlay" "off"
#	Option	    "OpenGLOverlay" "off"
#	Option	    "Textured2D" "on"
	Option	    "BackingStore" "on"
	Option	"TripleBuffer" "True"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Virtual	1600	1200
	EndSubSection
EndSection

Section "DRI"
	Group        "video"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "RENDER" "Enable"
	Option	    "DAMAGE" "Enable"
	Option	    "XVideo" "Enable"
	Option	    "Composite" "Enable"
EndSection

```

Commented options (#) are yet to be tested (on my sys). Either ignore or remove them.

---

### Post by gerardodelariva on 2011-10-02
Worked for me too, thanks!

Lenovo t60 - Ubuntu 10.04

---

