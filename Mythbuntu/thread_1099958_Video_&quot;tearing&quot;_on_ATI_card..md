---
title: "Video &quot;tearing&quot; on ATI card."
date: 2009-03-18
forum: Mythbuntu
---

### Post by AKADAP on 2009-03-18
I'm using an ATI HD4850 video card on Ubuntu 64 and having trouble with tearing of the video (a horizontal discontinuity of the picture that shows up during horizontal scrolling or horizontal motion of objects).
This used to occur at a slowly vertically moving line on the screen. 

I have since updated my proprietary ATI driver to 9.2 and turned on the vertical sync check-box in the mythTV front end setup (the one that did not do anything with the older ATI driver)

Now the tearing occurs on a fixed horizontal line across the screen in the top 15% of the display. How do I adjust the timing of the refresh relative to the vertical sync to move this discontinuity off the viewable portion of the video?

---

### Post by AKADAP on 2009-03-19
The tear is at 15% from the top on standard definition material, it is almost exactly half way for hidef material.

---

### Post by theophile on 2009-03-19
[http://www.mythtv.org/wiki/Frame_display_timing](http://www.mythtv.org/wiki/Frame_display_timing)

---

### Post by AKADAP on 2009-03-19
> **theophile said:**
> [http://www.mythtv.org/wiki/Frame_display_timing](http://www.mythtv.org/wiki/Frame_display_timing)

Unfortunately, this does not help me.

My system is using the  openGL timing method which is preferred over the RTC method, and the linked page only describes how to increase the interrupt rate of the RTC method, nothing about adjusting the timing of the SGI OpenGL method.

2009-03-19 15:02:28.672 Video timing method: SGI OpenGL

---

### Post by AKADAP on 2009-03-19
Just for completeness, I switched back to RTC mode and cranked the allowable interrupt rate up to 1024 Hz, and was back to the tear scrolling slowly up the screen. 

I switched back to SGI OpenGL method and was back to the tear in a fixed location close to the middle of the screen.

---

### Post by AKADAP on 2009-03-19
> **AKADAP said:**
> Just for completeness, I switched back to RTC mode and cranked the allowable interrupt rate up to 1024 Hz, and was back to the tear scrolling slowly up the screen. 

I switched back to SGI OpenGL method and was back to the tear in a fixed location close to the middle of the screen.

Well, my test was pointless. I checked the log and found:
2009-03-19 15:19:19.108 Video timing method: USleep with busy wait
so it is not using the RTC method and the interrupt rate won't make any difference. 

I don't see any way to specify to use the RTC method.

---

### Post by rob3435 on 2009-03-19
Hi AKADAP

This has been a known problem between ati binary drivers and mythtv for some time.

[http://www.mythtv.org/wiki/ATI_Proprietary_Driver#Tearing.2FVsync_problem](http://www.mythtv.org/wiki/ATI_Proprietary_Driver#Tearing.2FVsync_problem)

The only solutions is to use the opensource ati driver, with it's tear free exa,xv acceleration.  Since you have a r700 series card you will need the lastest drm from the r6xx-r7xx-support branch.

[http://cgit.freedesktop.org/mesa/drm/log/?h=r6xx-r7xx-support](http://cgit.freedesktop.org/mesa/drm/log/?h=r6xx-r7xx-support)

and the latest from [http://cgit.freedesktop.org/xorg/driver/xf86-video-ati/](http://cgit.freedesktop.org/xorg/driver/xf86-video-ati/)

Or wait for jaunty, since this was just pulled in the other day..

Regards,

---

### Post by AKADAP on 2009-03-20
I am reluctant to try the open source driver because I believe it is the default driver that Ubuntu attempts to load. With that driver, I was unable to install Ubuntu as my video card effectively shut itself off. I had to install in video safe mode and was stuck with 800x600 until I installed the ATI proprietary drivers.

Also in the process of installing the 9.2 ATI drivers I needed to uninstall the the old ATI drivers. Doing that left me with a screen resolution of something lower than the 2560 x 1600 resolution of my monitor (but much better than the 800x600 I was stuck with when I first installed Ubuntu) with no option for a higher resolution. I think this means that in the mean time, the open drivers have gotten better, but still not good enough.

If someone will tell me that the open source driver is now working with my video card at 2560x1600 without issues I might try it again as so far I have no need for the 3D effects.

---

### Post by rob3435 on 2009-03-20
Sorry i don't have any monitors that can handle 2560x1600.

As far as video tearing, both my test box's (3850 & 4850) will play videos streamed from my mythbox (which is r5xx based) with no video tearing using the latest opensource ati drivers along with the drm branch.  It's working well enough, i'm planning to upgrade the r5xx to a 4650 (silent cooler) this weekend.

Regards,

---

### Post by Mize on 2009-04-02
> **rob3435 said:**
> Hi AKADAP

The only solutions is to use the opensource ati driver, with it's tear free exa,xv acceleration.  Since you have a r700 series card you will need the lastest drm from the r6xx-r7xx-support branch.

[http://cgit.freedesktop.org/mesa/drm/log/?h=r6xx-r7xx-support](http://cgit.freedesktop.org/mesa/drm/log/?h=r6xx-r7xx-support)

and the latest from [http://cgit.freedesktop.org/xorg/driver/xf86-video-ati/](http://cgit.freedesktop.org/xorg/driver/xf86-video-ati/)

Or wait for jaunty, since this was just pulled in the other day..

Regards,

Any chance there's a simple howto on implementing the free drivers   with the "drm branch"? I'm running a 780G motherboard with an HD3200 and I have video and sound over hdmi but significant tearing issues.

Thanks.

---

### Post by rob3435 on 2009-04-02
There is more notes located here: [http://www.x.org/wiki/radeon](http://www.x.org/wiki/radeon)

But here's a simple cut down version:

Requirements (might be missing one or two more)
```

sudo aptitude install xserver-xorg-dev x11proto-xf86dri-dev x11proto-dri2-dev libxdamage-dev libxxf86vm-dev libdrm2-dev x11proto-gl-dev build-essential
```

Create a directory too save your git trees, no reason to redownload everything over and over.. (git_repo)

```

cd git_repo/
git clone git://anongit.freedesktop.org/mesa/drm

git clone git://anongit.freedesktop.org/git/xorg/driver/xf86-video-ati
or
git clone git://anongit.freedesktop.org/git/xorg/driver/xf86-video-radeonhd
```

Build DRM 
2.6.27's: (/char/drm/?) 
2.6.29's: (/gpu/drm)
```

cd ~/git_repo/drm
git pull
git checkout -b r6xx-r7xx-support origin/r6xx-r7xx-support
./autogen.sh --prefix=/usr
make
cd linux-core
make radeon.o drm.o
sudo cp drm.ko /lib/modules/YOURVERSION/kernel/drivers/gpu/drm/
sudo cp radeon.ko /lib/modules/YOURVERSION/kernel/drivers/gpu/drm/radeon/
cd ..
git checkout master
git branch r6xx-r7xx-support -D
```

Rebuild ati/radeonhd
```

cd ~/git_repo/xf86-video-ati
git pull
./autogen.sh --prefix=/usr
make
sudo make install
```

Reboot or reload modules, then verify:
```

voodoo@ubuntu-lvrm:~$ dmesg | grep drm
[   26.056909] [drm] Initialized drm 1.1.0 20060810
[   26.313540] [drm] Initialized radeon 1.29.0 20080613 on minor 0
[   26.789846] [drm] Setting GART location based on new memory map
[   26.804948] [drm] Loading RV670 CP Microcode
[   26.805079] [drm] Loading RV670 PFP Microcode
[   26.819983] [drm] Resetting GPU
[   26.820045] [drm] writeback test succeeded in 1 usecs
```

Regards,

---

### Post by Mize on 2009-04-02
Nice. Big thank you. I'll give it a whirl tonight.
HDMI sound working?

---

### Post by rob3435 on 2009-04-02
With certain chips, sound output thru hdmi works with the radeonhd git tree.

I don't use that feature with my mythbox, and have always just ran the ati driver.

Regards,

---

### Post by Mize on 2009-04-03
I'm having no luck...after fumbling with trying to get the latest radeon (not hd) driver running on 8.10 I decided to install the Jaunty Beta. While it boots and what not I only have three resolutions available and I'm getting overscan (or under - whatever makes the edges past the screen - can't see the menu bars). Manually editing xorg.conf to add modes doesn't work at all - x crash.

I'm running over hdmi to an lcd flat panel with native 1366x768.

edit: btw I can live with no sound over hdmi if I can get rid of the tearing in 2d.

---

### Post by rob3435 on 2009-04-03
I Mize,

Would you please pastebin your /var/log/Xorg.0.log & current /etc/X11/xorg.conf

Regards,

For Reference, here's the xorg.conf i use for my Samsung LN32A450 (dvi->htmi)
```

Section "Monitor"
	Identifier	"HDMI"
	Modeline "1360x768" 85.500 1360 1440 1552 1792 768 771 777 795 +hsync +vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"HDMI"
	Device		"Configured Video Device"
	DefaultDepth	24
	Subsection "Display"
	        Virtual 1360 768
        	Modes "1360x768"
	EndSubsection
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Option "AccelMethod" "EXA"
        Option "DRI" "on"
	Identifier	"Configured Video Device"
	Driver	"radeon"
EndSection

```

---

### Post by Mize on 2009-04-03
Thanks for the help Rob.
I used much of your xorg.conf changing the mode to my screen's native resolution. Still no go. Attaching both.

Good news is that I have no tearing with this driver and I have sound working (analog for now). It appears the driver is only detecting the monitor's PC (vga) modes so topping out at 1280x720. The monitor displays that it's running in 720p at 60 Hz.

At 640x480 I get the edges, but of course that's a rather useless mode.

---

### Post by Mize on 2009-04-03
Latest update:

Radeon free driver using VGA (RGB) output I get 1366x720 (yay!) only my tv only supports composite for sound on RGB (boo).

Radeon free driver using hdmi or dvi I get 1280x720 underscanned with sound on analog (my tv doesn't have optical in). No tearing but edges dorked.

Using non-free drivers all works (sound over hdmi, hdmi, full resolution and no underscan) but 2d tears something fierce.

---

### Post by rob3435 on 2009-04-03
So close.. ;)

What is the model of your lcd display?  Otherwise we should be able to borrow the modeline settings the closed source ati blob had used.

Nevermind, found a reference in the log.. Try this modeline

[http://www.mythtv.org/wiki/Talk:Vizio_VX37L](http://www.mythtv.org/wiki/Talk:Vizio_VX37L)

---

### Post by Mize on 2009-04-03
Thanks again but no luck. It seems the driver is defaulting to the TVs reported modes and not xorg.conf's modelines. If you look at the X log file the only modelines listed are the ones the TV is reporting. If I boot from RGB I get the higher modelines - it won't report these on HDMI for some reason (unless I use the non-free, tear driver).

Bummer!

I'll keep at it, but is there some way to have xorg.conf override the detected modes?

---

### Post by Mize on 2009-04-03
I'll probably drag up an old pc speaker set-up and run off the rgb with those for now :(

Thanks for the help.

---

### Post by rob3435 on 2009-04-03
Reading this: [http://www.mythtv.org/wiki/Modeline_Database#Vizio_L37HDTV_37.22_LCD_720p_.281360x768_PC.29](http://www.mythtv.org/wiki/Modeline_Database#Vizio_L37HDTV_37.22_LCD_720p_.281360x768_PC.29)

ati must do something very special.

Otherwise as long as the modeline is in the Monitor section it should force that mode.

You can try adding 

Option "IgnoreEDID" "on"

to your xorg.conf to have it ignore the edid data..

Regards,

---

### Post by Mize on 2009-04-03
> **rob3435 said:**
> 
You can try adding 

Option "IgnoreEDID" "on"

to your xorg.conf to have it ignore the edid data..

Regards,

BINGO!
That did it. I'm running 768p over hdmi with (analog) stereo sound.

This thread has the solution for free radeon drivers with no tearing 2D on Jaunty with a 780G chipset and embedded HD 3200. 

Thanks!

Now about that audio over hdmi... :)

---

### Post by nickrout on 2009-04-03
Just to add something, if you get problems with overscan there is sometimes a setting on the tv/panel to fix it. For example on my sony 46 inch 1080p tv playing from a nVidia card over dvi/hdmi cable I get a large overscan which is fixed by a setting that "full pixel" rather than "auto"or "normal"

---

### Post by Mize on 2009-04-04
> **nickrout said:**
> Just to add something, if you get problems with overscan there is sometimes a setting on the tv/panel to fix it. For example on my sony 46 inch 1080p tv playing from a nVidia card over dvi/hdmi cable I get a large overscan which is fixed by a setting that "full pixel" rather than "auto"or "normal"

Yes. My better TV (50" Panny Plasma with the ps3/x360/denon surround) has such a feature. This cheapo Vizio does not unfortunately so the right mode and ignoreedid were crucial.

---

