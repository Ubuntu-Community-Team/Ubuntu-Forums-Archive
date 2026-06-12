---
title: "Clipped display on Samsung TV"
date: 2011-09-24
forum: Mythbuntu
---

### Post by MickSulley on 2011-09-24
Hi 
Using Mythbuntu 11.04 with a Samsung PDP 42 inch TV.  It works but all of the edges are clipped off the screen, so I cannot see the panel at the top of the screen etc.  I have seen suggestions in other posts to change the TV settings, but there don't seem to be any that help this.

I am connected via an HDMI cable and using the on board graphics on an Intel i3-540 processor

Thanks
Mick

---

### Post by papibe on 2011-09-24
> I connect my computer to my TV too (XBMC though). In the case of my Sony Bravia and my brother's Samsung, the problems was in the HDTV side.

In the Sony you can fix it by setting 'Full Pixel' to Screen -> Display Area. In the Samsung set the attribute P.size to 'Full Scan' ( in the Picture Options -> Screen Size menu if I remember correctly).

I hope it helps,
Regards.

Have you tried another TV HDMI input?

---

### Post by LowSky on 2011-09-25
its called overscan. Some TVs have a setting to change it, some don't. the one who don't mean you need to edit it from the software side

there are quite a few link on here, but here is one that might help

[http://ubuntuforums.org/showthread.php?t=796776](http://ubuntuforums.org/showthread.php?t=796776)

---

### Post by nickrout on 2011-09-25
> **LowSky said:**
> its called overscan. Some TVs have a setting to change it, some don't. the one who don't mean you need to edit it from the software side

there are quite a few link on here, but here is one that might help

[http://ubuntuforums.org/showthread.php?t=796776](http://ubuntuforums.org/showthread.php?t=796776)

True, fixes in order of preference:

1. TV setting to reduce overscan - depends on make/model, google for make of TV and either 'overscan' or 'just scan' or '1:1'.

Here is a good start

[http://pixelmapping.wikispaces.com/Samsung+TVs](http://pixelmapping.wikispaces.com/Samsung+TVs)

2. nvidia settings has an option to reduce overscan, if you have an nvidia card of course.

3. the setting within mythtv.

---

### Post by MickSulley on 2011-10-02
Firstly thanks to those who replied and apologies for taking a while to get back.

The link, and many others that I have found, involve modifying X11 settings, but it seems that in 11.04 there is no X11, or have I misunderstood?

I checked the TV setting on the link suggested, I have a PS42E7 and it just says "Severe overscan on HDMI" so no hope there I guess.

Settings within mythtv, Just tried that and it does set the size, but only for the MythTV application, if I go to the desktop I still cannot see the panel to do anything.

Are there any other option?  Is there any way to install X11 and use that, and if I did would it solve anything?

Any help would be appreciated!

Thanks
Mick

---

### Post by nickrout on 2011-10-02
> **MickSulley said:**
> Firstly thanks to those who replied and apologies for taking a while to get back.

The link, and many others that I have found, involve modifying X11 settings, but it seems that in 11.04 there is no X11, or have I misunderstood?

you have misunderstood.> 

I checked the TV setting on the link suggested, I have a PS42E7 and it just says "Severe overscan on HDMI" so no hope there I guess.

Settings within mythtv, Just tried that and it does set the size, but only for the MythTV application, if I go to the desktop I still cannot see the panel to do anything.

Are there any other option?  Is there any way to install X11 and use that, and if I did would it solve anything?

Any help would be appreciated!

Thanks
Mick


You have X11 installed, believe me.


googling about that model and overscan produces no nice results with easy fixes, just a general feeling that you made a bad choice of TV, I am sorry to say.

Do you have an nvidia graphics card? If so there is a fix available using the nvidia driver's overscan compensation.

---

### Post by MickSulley on 2011-10-03
No nvidea I'm afraid, I am using the on board graphics on the Intel i3-540 processor.

---

### Post by lucazade on 2011-10-03
I had some issues with a samsung lcd tv and hdmi connection. I had to rename the hdmi source in the monitor-tv to 'pc'.

---

### Post by xc3RnbFO8P on 2011-10-03
Do you have this button on your tv remote

[IMG]http://www.tvanswers.org.uk/images/aspectratiobutton.jpg[/IMG]

---

### Post by taurial on 2011-10-03
I would start from setting native PDP resolution 1024x768 (check the manual) and lowest possible frequency of 50 or 60Hz. After that I would try to resize and position TV picture using PDP menu. If all goes well, resolution can be increased and fixed or you can always come back to base values.

Maybe, another way to get it to work. Try connecting PDP to computer with VGA cable and also start from base resolution and frequency.

I also remember one helpful thing from other Linux when a window doesn't fit to the screen. Press and hold Alt, click and hold mouse button over the desired window and drag it.

Hope that helps.

P. S. Posting a picture with a problematic picture would help us to resolve this issue faster.

---

### Post by MickSulley on 2011-10-03
OK I have done some more investigation.

Renamed the HDMI to PC and power cycled, no difference

Remote doesn't have that button, picture attached.

I have attached pictures of the screen when plugged into the TV and also a similar picture plugged in to my monitor.  As you can see on the monitor I can see the 'Applications' menu and a tab for each running application, on the TV they are above the top of the screen and so not visible.

I have also played around with Settings Editor, setting values for xfce4-settings-editor and xfce4-settings-manager, setting values for window height and width.  These make no difference at all.  What are they for?

I also did a search for X11 stuff and yes there is some stuff there.  Is there anything I can edit to fix this problem?  I seem to remember way back when I had a problem with resolution on my laptop there was a file that listed all of the available resolutions, and I edited that to fix it, but I cannot remember which file it was.  

Any other ideas what I can do here?  It is so frustrating.

Thanks
Mick

---

### Post by nickrout on 2011-10-03
You can apparently use the VGA input on the TV and you will get no overscan, but will be limited to something like 1024x768 - ie no HD resolutions, so you may not want that solution.

Look in the man page for your video driver, I don't know which driver your card uses, but /var/log/Xorg.0.log will tell you. Look through the man pages for any overscan or underscan settings and apply any you find to /etc/X11/xorg.conf.

The available resolutions should be listed if you run xrandr. Here is a sample output:

>  DISPLAY=:0 xrandr
Screen 0: minimum 320 x 240, current 1920 x 1080, maximum 1920 x 1080
default connected 1920x1080+0+0 0mm x 0mm
   1920x1080      50.0*    51.0
   1680x1050      52.0     53.0
   1600x1024      54.0
   1600x900       55.0
   1440x900       56.0
   1400x1050      57.0     58.0
   1360x768       59.0     60.0     61.0
   1280x1024      62.0
   1280x960       63.0
   1280x800       64.0
   1280x720       65.0
   1152x864       66.0
   1024x768       67.0
   960x600        68.0
   960x540        69.0
   896x672        70.0
   840x525        71.0     72.0
   800x600        73.0     74.0
   800x512        75.0
   720x450        76.0
   680x384        77.0     78.0
   640x512        79.0
   640x480        80.0     81.0
   576x432        82.0
   512x384        83.0
   400x300        84.0
   320x240        85.0


Basically the problem is in your TV and anything you do on the computer is a compromise. However an nvidia card that supports overscan adjustment could be a good solution.

---

### Post by nickrout on 2011-10-03
Oh you COULD try to run mythfrontend in a window and set the window size to be within the viewable frame. This won't help your menus at the desktop, but hey it is an appliance. If you need to access the applications menu,use ctrl-esc on a keyboard.

---

### Post by BicyclerBoy on 2011-10-04
Could try a overscan correction with xrandr
Assuming the sad 1024x768 resolution..
```

xrandr --output LVDS1 --fb 992x736
xrandr --output LVDS1 --pos 16x16

```

replace LVDS1 with your screen name from xrandr.
This works with latest intel driver from xorg-edgers on a netbook..

---

### Post by nickrout on 2011-10-04
> **BicyclerBoy said:**
> Could try a overscan correction with xrandr
Assuming the sad 1024x768 resolution..
```

xrandr --output LVDS1 --fb 992x736
xrandr --output LVDS1 --pos 16x16

```

replace LVDS1 with your screen name from xrandr.
This works with latest intel driver from xorg-edgers on a netbook..

Actually I don't think we even know what resolution he is getting. Apprently 1024x768 is the maximum on vga, but that set should to at least 720p if not 1080i/p on hdmi.

---

### Post by BicyclerBoy on 2011-10-04
That's why I wrote "Assuming"..

As far as I can tell:
- it's an old plasma with native of 1024x768.
- Is is possible that native res is not used /not able to be used..
- The TV VGA input takes the std video modes (not native) inc 1080i/720p
- hdmi may not be any better

But if HDMI accepts native res, it should look better.

A cheap video card will out perform the TV input scaler.

---

### Post by goffa on 2011-10-07
Did you try going through all the options when pressing the p.size button on your remote? My Samsung has 4 different size modes.

---

