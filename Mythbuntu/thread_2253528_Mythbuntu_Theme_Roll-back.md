---
title: "Mythbuntu Theme Roll-back"
date: 2014-11-20
forum: Mythbuntu
---

### Post by davefor2 on 2014-11-20
Hi

I and currently running Mythbuntu 12.04.03 .25 and had Mythbuntu 25.30 as my theme
I updated to .27 so I will still get Schedule Direct data. Only problem is that I updated 
to the new Mythbuntu theme I thinks it now 28.something. The new theme has huge fonts
and can't see a lot of items as they are now pushed off the screen. Is there a way to reduce
the size or roll-back the theme to 25.30?
I did notice that after updating to the new theme it removed 25.30 from theme chooser list and would
like it back.

Thanks
Dave

---

### Post by tgm4883 on 2014-11-20
> **davefor2 said:**
> Hi

I and currently running Mythbuntu 12.04.03 .25 and had Mythbuntu 25.30 as my theme
I updated to .27 so I will still get Schedule Direct data. Only problem is that I updated 
to the new Mythbuntu theme I thinks it now 28.something. The new theme has huge fonts
and can't see a lot of items as they are now pushed off the screen. Is there a way to reduce
the size or roll-back the theme to 25.30?
I did notice that after updating to the new theme it removed 25.30 from theme chooser list and would
like it back.

Thanks
Dave

Can you send a screenshot?

---

### Post by davefor2 on 2014-11-20
I can try to make a simulated screen shot when I get home. If I connect via VNC I can scroll up/down side to side.
Its the image on the TV that is to big.
Also like to add more information The recording play back is fine not much overscan at all.
It just the GUI.
The new version is Mythbuntu 28.16.
I loaded a new install on spare machine to see if the is any thing different I did notice the follow:
Mythbuntu 25.30 1280x720
Mythbuntu 28.16 1920x1080
Not sure if this matters or not but my output from Mythbuntu is with s-video. 
In order to play recording so they are not stretched I have 4:3 set as the 
default. Also this is a Nvidia video card with s-video out

---

### Post by tgm4883 on 2014-11-20
> **davefor2 said:**
> I can try to make a simulated screen shot when I get home. If I connect via VNC I can scroll up/down side to side.
Its the image on the TV that is to big.
Also like to add more information The recording play back is fine not much overscan at all.
It just the GUI.
The new version is Mythbuntu 28.16.
I loaded a new install on spare machine to see if the is any thing different I did notice the follow:
Mythbuntu 25.30 1280x720
Mythbuntu 28.16 1920x1080
Not sure if this matters or not but my output from Mythbuntu is with s-video. 
In order to play recording so they are not stretched I have 4:3 set as the 
default. Also this is a Nvidia video card with s-video out

I really need a screenshot, even if it's just a camera shot of your TV screen. Without that, I won't know if what you are seeing is unexpectedly large fonts, or by design.

The resolution wouldn't affect it.

---

### Post by davefor2 on 2014-11-20
I attached 2 sample Pics one full screen and one I added white borders on side so you can see whats cut off
It a 52" 16x9 widescreen tv

---

### Post by tgm4883 on 2014-11-21
> **davefor2 said:**
> I attached 2 sample Pics one full screen and one I added white borders on side so you can see whats cut off
It a 52" 16x9 widescreen tv

Hmm, maybe it's a forum limitation, but those images are pretty small. Something doesn't look right though. The recording date shouldn't be cut off like that and the theme is cut off on all sides.

1) I'm not sure I understand the white border you added (maybe because of the small size of the images). How did you add the white border? Can you upload the whiteborder one to [http://imagebin.ca/](http://imagebin.ca/)
2) What model TV do you have?
3) What is the output when you run 'xrandr' and 'xdpyinfo | head -n 100' and 'echo $LANG' in a terminal? (You'll need to do these locally, not via ssh)

---

### Post by davefor2 on 2014-11-21
1) The white borders are just from the TV. I change aspect from 16:9 to 4:3 on the TV which adds white borders on side to fill
     the screen. Did this so you can see the cut-off area better.

2) It a old rear projection TV.  Its 51" widescreen (I thought it was 52" as noted above)
    Hitachi Model 51GWX20B

3) Here are the outputs you asked for I also included mythbuntu version info.


dave@Mythbuntu:~$ xrandr
Screen 0: minimum 8 x 8, current 1024 x 768, maximum 8192 x 8192
DVI-I-0 disconnected primary (normal left inverted right x axis y axis)
DVI-I-1 disconnected (normal left inverted right x axis y axis)
TV-0 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0*+
   800x600        60.0  
   720x480        60.0  
   640x480        60.0  
   640x400        60.0  
   512x384        60.0  
DVI-I-2 disconnected (normal left inverted right x axis y axis)
DVI-I-3 disconnected (normal left inverted right x axis y axis)

==================================================================================

dave@Mythbuntu:~$ xdpyinfo | head -n 100
name of display:    :0.0
version number:    11.0
vendor string:    The X.Org Foundation
vendor release number:    11501000
X.Org version: 1.15.1
maximum request size:  16777212 bytes
motion buffer size:  256
bitmap unit, bit order, padding:    32, LSBFirst, 32
image byte order:    LSBFirst
number of supported pixmap formats:    7
supported pixmap formats:
    depth 1, bits_per_pixel 1, scanline_pad 32
    depth 4, bits_per_pixel 8, scanline_pad 32
    depth 8, bits_per_pixel 8, scanline_pad 32
    depth 15, bits_per_pixel 16, scanline_pad 32
    depth 16, bits_per_pixel 16, scanline_pad 32
    depth 24, bits_per_pixel 32, scanline_pad 32
    depth 32, bits_per_pixel 32, scanline_pad 32
keycode range:    minimum 8, maximum 255
focus:  window 0x3200004, revert to Parent
number of extensions:    28
    BIG-REQUESTS
    DAMAGE
    DOUBLE-BUFFER
    DPMS
    DRI2
    GLX
    Generic Event Extension
    MIT-SCREEN-SAVER
    MIT-SHM
    NV-CONTROL
    NV-GLX
    RANDR
    RECORD
    RENDER
    SECURITY
    SHAPE
    SYNC
    X-Resource
    XC-MISC
    XFIXES
    XFree86-DGA
    XFree86-VidModeExtension
    XINERAMA
    XINERAMA
    XInputExtension
    XKEYBOARD
    XTEST
    XVideo
default screen number:    0
number of screens:    1

screen #0:
  dimensions:    1024x768 pixels (260x195 millimeters)
  resolution:    100x100 dots per inch
  depths (7):    24, 1, 4, 8, 15, 16, 32
  root window id:    0x1ce
  depth of root window:    24 planes
  number of colormaps:    minimum 1, maximum 1
  default colormap:    0x20
  default number of colormap cells:    256
  preallocated pixels:    black 0, white 16777215
  options:    backing-store NO, save-unders NO
  largest cursor:    64x64
  current input event mask:    0x7a802f
    KeyPressMask             KeyReleaseMask           ButtonPressMask          
    ButtonReleaseMask        LeaveWindowMask          ExposureMask             
    StructureNotifyMask      SubstructureNotifyMask   SubstructureRedirectMask 
    FocusChangeMask          PropertyChangeMask       
  number of visuals:    136
  default visual id:  0x21
  visual:
    visual id:    0x21
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x22
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x23
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x24
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
dave@Mythbuntu:~$ 
=============================================================

dave@Mythbuntu:~$ echo $LANG
en_US.UTF-8
dave@Mythbuntu:~$ 

==============================================================


dave@Mythbuntu:~$ apt-cache policy mythtv
mythtv:
  Installed: 2:0.27.4+fixes.20141114.99688ed-0ubuntu0mythbuntu1
  Candidate: 2:0.27.4+fixes.20141120.65d92fd-0ubuntu0mythbuntu1
  Version table:
     2:0.27.4+fixes.20141120.65d92fd-0ubuntu0mythbuntu1 0
        500 [http://ppa.launchpad.net/mythbuntu/0.27/ubuntu/](http://ppa.launchpad.net/mythbuntu/0.27/ubuntu/) precise/main amd64 Packages
 *** 2:0.27.4+fixes.20141114.99688ed-0ubuntu0mythbuntu1 0
        100 /var/lib/dpkg/status
     2:0.25.2+fixes.20120802.46cab93-0ubuntu1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/multiverse amd64 Packages
     2:0.25.0+fixes.20120410.1f5962a-0ubuntu1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/multiverse amd64 Packages
dave@Mythbuntu:~$ 
==========================================================================================

---

### Post by tgm4883 on 2014-11-21
Ok, so the font size looks correct, but there are a few issues here.

1) You have a native resolution of a 4:3 screen (your native resolution is 1024x768), but the theme was created for a 16:9 screen. I'm making some edits so this works on both 4:3 and 16:9 screens.
2) The edges of the theme are missing because of overscan. There are possibly a few ways to fix this. Some TV's have multiple modes for displaying back PC content. You would have to check your manual for this. You can also fix this in the frontend by going to "Setup" > "Screen Setup Wizards" and fixing it so the corners of the theme are in the corners of your theme.

This was masked in the previous theme as the previous themer had quite a lot of extra space on the sides of the theme to make up for overscan, but now that we have the screen setup wizard there isn't a need to do that.

---

### Post by davefor2 on 2014-11-23
After I upgraded to .27.4 When I go in to Screen setup wizard I get a blank screen and it locks up the 
frontend. I did install 14.04 on a test drive and had the same issue with theme and used the screen setup
wizard (this one has a background of mythbusters) to try to correct it, but all it did was resize the frontend
window but didn't do much as far as what is getting cut-off. Is there a way to just reinstall the older theme
25.30?


Also I am planning on upgrading my Box and adding a video card with HDMI output. 
I would use 14.04 vs 12.04 but had a few other issues with 14.04 
Same Theme issue
Missing the check box do disable Auto-Expire default
Error trying to set mythweb password (I have this in another post)
Also couldn't figure out how to disable commercial detection

---

### Post by davefor2 on 2014-11-23
OK Quick update
I was able to switch to another theme and run the screen setup wizard
then went back to Mythbuntu theme and did some fine tuning in Setup> Appearance
GUI width   912
GUI height  745
GUI X offset 50
GUI Y offset  0
Also had a glow on top of screen from the top panel so I did the following
Applications > Settings > Panel > checked off Auotmatically show and hide the panel
Also changed Measurements Size from 24 to 16

---

