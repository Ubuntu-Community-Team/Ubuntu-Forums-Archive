---
title: "Mythbuntu Frontend issues"
date: 2014-02-08
forum: Mythbuntu
---

### Post by dan57 on 2014-02-08
I have been successfully using Mythbuntu at my house for years with a combination frontend/backend system, now my parents have decided to plunge in as well, and asked me to configure a system for them.  For a number of complicated reasons, they are requiring the implementation of a separate backend and frontend system.  Further, they only have an old style CRT TV with either RCA composite or S-Video inputs available.  I've struggled with the backend install and setup, but after 2 weeks and 8 reinstalls I managed to get it configured properly and running correctly using the mythbuntu-12.04.3-desktop-amd64.iso install.  Now on to the frontend.  Using the knowledge I gained from the multiple backend installs, I got the frontend installed from the same iso today.  The frontend connects to the backend and things are looking good except for the following nightmares:
1) MCE remote does not work, exactly the same model as what I use on my system: 
[http://www.amazon.com/dp/B000W5GK5C/ref=pe_385040_30332200_pe_309540_26725410_item](http://www.amazon.com/dp/B000W5GK5C/ref=pe_385040_30332200_pe_309540_26725410_item)
On my system the IR receiver box illuminates a red LED when it is receiving something.  Pointing the new remote at my existing myth system works (box works and commands move the system items on screen).  On the new frontend box, there is nothing, not even the red LED in the receiver, it is almost like the usb configuration is wrong, and I don't know how to fix this.
2) The window resolution is wrong.
    a) The default resolution was 1980x1200
    b) Changing the resolution to 1200x1024 seems to work.
    c) Starting mythfrontend causes the system to resize based on the resolution
    d) Navigating to the view recordings screen has info chopped off on the righthand and bottom end of the screen
    e) The frontend system appears to be shifted down and to the left
        i) There is "desktop" background visible to the left of the frontend display
        ii) The application launch bar is visible above the frontend display
    f) The computer is outputting through the HDMI port on the computer ([http://www.newegg.com/Product/Product.aspx?Item=N82E16856107123](http://www.newegg.com/Product/Product.aspx?Item=N82E16856107123))
    g) The HDMI is being converted to RCA composite with an external box ([http://www.amazon.com/gp/product/B00DSSCBZ8/ref=wms_ohs_product?ie=UTF8&psc=1](http://www.amazon.com/gp/product/B00DSSCBZ8/ref=wms_ohs_product?ie=UTF8&psc=1)) VHD-168.
How do I fix this?  I've tried the X11 conf file, the automatic screen setup setup wizard and display resizing.  If I use the screen auto setup wizard, then it resizes mythfrontend to only use part of the available display area.  If I zero out the screen size in the display configuration then mythfrontend restarts and uses the full screen area, however all setup screens have info chopped off on the lefthand side so it is hard to configure as the beginning of any info lines is chopped off.
3) I've tried using both the mythcenter 1.1 and the mythcenter-wide 1.6 theme with no change (same issues with the default theme).  I would like to use the metallurgy theme as that is what I use on my original setup but I can't find it.  How do I import it?

At this point I am at my wits end on this project.  Please help me.  What additional info is needed to troubleshoot this mess?

Thanks in advance,

Best regards,
Dan

---

### Post by blm-ubunet on 2014-02-08
A VGA to composite would have been a lot simpler because the video card would be in complete control of generating the output video mode & overscan etc..

Your adaptor box only outputs 480i & 576i by down-scaling everything..& you have little control on what is happening.

I would set the PC output to be 640x480 (p60) or 768x576 (p50)..
(I prefer to use 60Hz modes on old CRT TV, even with 50Hz video)
Set mythtv to use same video mode for video as GUI
Set mythtv to be full screen (not windowed)
Use screen size wizard to set the corners extremes to allow for the normal old CRT overscan..
I don't understand the problem you were having with this & why there is a video mode change happening.
(untick "use separate video mode for GUI")
You should get an effective usable screen of 710 by 530 pixels maybe..
Using the desktop could be problem so maybe below is better soln.

Fix DE & mythtv overscan:
If you use the video driver overscan compensation you do not need to use mythtv screen size wizard.
The latest nVidia driver has re-introduced the GUI adjustment tool else you have to use viewportin & viewportout settings in xorg.conf or with "nvidia-settings" 

Are you using the proprietary nVidia driver (& VDPAU) ?

A 32" LCD (HDMI 720p) TV is probably < US$200

---

### Post by dan57 on 2014-02-09
I am using the proprietary nVidia driver that was automatically selected (the 3.0 option which didn't specify VDPAU in the description).  There was an option to select a nVidia driver with VDPAU, should I do that?  I checked, the video card has a DVI-I output on it, which supports VGA, but I can't find any DVI to VGA adapters.  I'm not opposed to this solution, do you have a recommendation for a VGA to TV connection (I can use composite video - yellow connector, or S-Video options).  I'll either find or get a DVI-VGA adapter if this is a better solution.  Going with this route, would you change any of your suggestions from above?

As for the TV, it is a 36" Sony Trinitron flatscreen CRT, which is the largest TV that will fit into the entertainment center.  Going with a flat screen LCD that fits into the same area will result in a smaller usable screen, so that idea is not acceptable....

---

### Post by blm-ubunet on 2014-02-09
I don't know any proprietary nVidia driver that is labelled as 3.0.
But then I uninstall the software centre & never use jockey tool.
The prop. driver supports VDPAU  on the 8200 onwards (mostly)..

The DVI-I/A to VGA adaptor is passive & normally comes with the video card. Should cost < $US5.
The DVI port must be DVI-I or -A (& not just DVI-D).
[https://en.wikipedia.org/wiki/File:DVI-VGA-Adapter.jpg](https://en.wikipedia.org/wiki/File:DVI-VGA-Adapter.jpg)

If you're watching 16:9 & 2.35:1 movies on a 4:3 monitor (with side speakers) then you're watching an much smaller equivalent LCD TV. The bezel width on modern LCDs is thin (..so is the sound quality) so you get more screen width at the **correct aspect ratio**. You could fill the remaining space with a passive sound bar/centre speakers

The VGA to s-video convertor is pretty simple. But you will need to create/edit /etc/X11/xorg.conf file to allow interlaced video modes & ignore the missing EDID etc
I have working examples of these settings.
Don't have any VGA adaptor recommendations as my CRT has VGA input.
[http://www.ebay.com/itm/NEW-VGA-SVGA-TO-TV-RCA-S-VIDEO-CABLE-ADAPTER-FOR-LAPTOP-PC-/380801587980](http://www.ebay.com/itm/NEW-VGA-SVGA-TO-TV-RCA-S-VIDEO-CABLE-ADAPTER-FOR-LAPTOP-PC-/380801587980)
Something like this should work..

Is the TV a widescreen or 4:3?
Do it accept progressive scan 480p or 576p?

---

### Post by dan57 on 2014-02-09
The TV is a KV-36XBR250 WEGA capable of 480i video input.  The single  component input is used by the DVD player.  I have S-Video and composite  video options open to me.  Per this page:  [http://en.wikipedia.org/wiki/FD_Trinitron/WEGA](http://en.wikipedia.org/wiki/FD_Trinitron/WEGA) it might be capable of  853x1080i video, but nothing in the manual suggests this.  The video  card has DVI-I output and I will get the DVI to VGA and VGA to TV  adapters.  What do you recommend for the X11/xorg.conf file?  TV is 4:3.

Thanks,
Dan

---

### Post by blm-ubunet on 2014-02-10
I think s-video only supports 480p & 576p max & most s-video devices only support 480i & 576i.

Your TV does not support any progressive scan modes (which is slightly odd)..
The component inputs are possibly wasted on a DVD player unless it has progressive scan &/or good up-scaler.
The picture quality from the computer can be better than almost any DVD player.

Could use DVD player on s-video & let PC have component, then you can try the 1080i video mode.
Problem is that most (all cheap) VGA-component adaptors are RGB video & not YPbPr video.
The adverts have incorrect/misleading info.
And the convertor boxes have "smart" scaler chips & will interfere with custom video modelines etc.

So in summary...the s-video adaptor is a better proof-of-concept & should be low cost.
I'll post some suggestions for the xorg.conf file in next 24hrs..

---

### Post by dan57 on 2014-02-10
Thanks for the continued help on this.  The S-video adapter is in the mail.  I'm looking forward to the xorg.conf file suggestions.

Best regards,
Dan

---

### Post by blm-ubunet on 2014-02-11
This example xorg.conf has been setup assuming:
- 1 DFP debugging display (with EDID)
- 1 CRT connected to VGA (no EDID)
- CRT supports 480i60 (interlaced NTSC)
- separate xscreens (no twinview, no xinerama)

I have (attempted) calculated screen size from 36" & 4:3 aspect ratio.
The calculated modelines in the file are prob exactly the same as the built-in Xserver modes but by generating your own you know the exact name/label of the mode.

There is a keyword option (commented out) "ModeDebug" that can be useful..

So to use this file I would:
- create the xorg.conf file by using nvidia-settings (as root with sudo) & use the option button to save setup to xorg.conf file.
- edit the /etc/X11/xorg.conf file & start changing/adding things..
You can logout & login to restart the Xserver.

The DFP-1 & CRT-0 labels may need to be changed depending on the internal wiring arrangement of your PC.
The names/labels will be shown/revealed in "nvidia-settings" program or
xrandr -q -d :0.0
xrandr -q -d :0.1
nvidia-settings -q :0.0/Refreshrate

---

