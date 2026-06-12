---
title: "DVI out to HDTV"
date: 2012-04-13
forum: Multimedia Software
---

### Post by gtippitt on 2012-04-13
I am trying to set up a PC to connect to an HTDV I just bought used.  It is a 57" Sony KP-57WS510 rear projection model that will support 1080i, 720p, 480p, and 480i connections.  (It's an old model HDTV that takes up a bit of room, but for $150, I'm still giggling like Anderson Cooper.  I live on a fixed income and had been watching an old 21" for 20 years.)

I got the TV and an eMachine PC used without any documentation, but I've read everything I can find online for documentation.  The PC has a nVidia 8500GT video card with DVI output, which the TV supports.  I connected the TV to the PC's DVI out with a single link DVI-D cable and installed Ubuntu 11.10.  The install went okay, and the screen looked pretty good for its size.  I had some overscan, which I understand can be fixed later.  With the default video drivers, it worked okay at 1280*720 resolution.

After I installed the Nvidia drivers and rebooted, the GUI screen is no longer visable.  The PC's POST, BIOS setup, and UBUNTU boot splash screen all show up fine, the the TV goes black.  I can bring up TTY01 by pressing CTRL-ALT-F1, and the text console shows up fine, but when I press CTRL-ALT-F7, I still get a blank-black GUI screen.  I did not see any obvious errors in the xorg.log.  The xserver and lightdm both seemed to have started, but the TV could not display the GUI output from the video card.  From the text console, I was able to run "apt-get remove nvidia-current" and reboot to restore the GUI screen. 

After reinstalling "nvidia-current" package and rebooting, I again get a blank-black diaplay rather than my GUI desktop.  I can access the GUI desktop using VNC-Remote Desktop Viewer from another PC without problems, which I think indicates Xserver and LightDM are fine.  I've tried it with and without an "/etc/X11/xorg.conf" file.  I've been using Ubuntu for about 5 years, but I'm confused about what the role of "/etc/X11/xorg.conf" is now.  I've tried using "dpkg-reconfigure xserver-xorg" and "nvidia-xconfig" to build new xorg.conf files, but neither one seems make any difference.  I don't have any experience tweaking the "xorg.conf" file by hand.  From a remote desktop, I've tried seting every resolution and refresh rate using the "nvidia-settings" program, but all I can get is a blank-black display on the desktop GUI.

If anyone can give me any help in fixing this problem or point me in the right direction for more documentation and examples, I would greatly appreciate the assistance.  I want to try to get it working with the proprietary nVidia drivers, because when I'm not using the PC it runnning the BOINC-SETI application that using the nVidia GPU CUDA, which will not work with the open source drivers.  If I can get the PC working with the TV, I would like to install MythTV and use it as a DVR-HTPC after the 12.04 LTS version is finalized.

Thank you,
Greg

---

### Post by BicyclerBoy on 2012-04-13
The xorg.conf file is not necessary for normal use.

You probably have to..
I guess your problem is that the TV is not detected as connected & the TV does not report EDID.

If you can access/post the file:
/var/log/Xorg.0.log

The nVidia driver readme appendix B X config options...
Options for /etc/X11/xorg.conf:

Option "ModeDebug" "boolean"
- extra debug info into Xorg.0.log

Option "ConnectedMonitor" "DFP"
-  forces use of monitor (including not detected)

Option "UseDisplayDevice" "DFP-0"
- forces use of this detected monitor

Option "UseEDID" "boolean"
- do not use any part of EDID (good if no EDID reported
- can still use built-in modes
- don't necessarily need custom modeline

But post the log file with nVidia driver running (console login)..

---

### Post by SeijiSensei on 2012-04-13
Try booting the recovery kernel, drop to a root shell, and run "nvidia-xconfig".  Does that help?

---

### Post by gtippitt on 2012-04-13
Thank you so much BicyclerBoy !!

Even though my Sony is a rear projection and not a flat panel, that fixed the problem.  The nVidia driver was seeing the TV as a CRT, maybe because I'm using the DVI interface rather than s-video.  I added the DFP option to xorg.conf and restarted lightdm.  Everything was great.

I've got to tweak it a bit more to fix the overscan, but otherwise it is great.  I'll post my final xorg.conf for others as a template when I get it finished.

The nVidia readme can be found as a text or HTML at the links below:

[http://developer.download.nvidia.com/compute/cuda/4_0_rc2/drivers/docs/README_Linux.txt](http://developer.download.nvidia.com/compute/cuda/4_0_rc2/drivers/docs/README_Linux.txt)

[http://us.download.nvidia.com/XFree86/Linux-x86/190.42/README/appendix-b.html](http://us.download.nvidia.com/XFree86/Linux-x86/190.42/README/appendix-b.html)


BicyclerBoy, once you got me pointed in the right direction, I found the following two links that also provide a bit more explanation of the options for the driver.

[http://www.mythtv.org/wiki/NVidiaProprietaryDriver](http://www.mythtv.org/wiki/NVidiaProprietaryDriver)
[http://en.wikibooks.org/wiki/NVidia/TV-OUT](http://en.wikibooks.org/wiki/NVidia/TV-OUT)


SeijiSensei,
I could get a TTY01 text console by pressing CTRL-ALT-F1, but none of the normal fixes that build an new default xorg.conf would fix the problem.  They all created conf files with a CRT for the display.

Thanks,
Greg

---

### Post by gtippitt on 2012-04-17
I got the output going to the TV in 1280*1080 resolution, and it looks really good.  I've not yet found a fix that works for the overscan, so I've got part of the picture missing around the edges.  The screens do not show up on the nvidia-settings program that normally let you compensate for TV overscan.  I think this is because I had to use the xorg.conf setting to tell the driver that my TV is a digital flat panel, even though my TV is a rear projection system.  If it really were a DFP display, it wouldn't have the overscan, so the driver doesn't show me the window to fix it.  Without forcing the driver to think the display was a DFP, it didn't seem to know how to output to the digital DVI interface.  Better to get most of the screen displayed that none at all, which is what I had without the DFP option.

I'm planning to install MythTV, which has its own settings to compensate so I'll worry about the overscan later.  For the time being I use it occasionally on the web, to watch videos on YouTube or if I want to look up something on IMDB while watching TV.  I'm using the old-style GNOME-Panel desktop (I hate UNITY. - "Resistance Is NOT Futile").  I increased the size of the panels at the top and bottom of desktop. 

I couldn't see the right-most and left-most items on the panels, so I brought the desktop up using VNC-remote desktop so I could see the entire desktop and tweak it a bit.  I copied the panel items in the corners and created another one next to each one.  When I look at desktop on the TV screen, the items on each end of the panels are not visible, but I can see the second one fine.  Everything else seems to work pretty well, except when I try to maximize a screen.  I simply re-sized the window for the Chromium browser, the terminal, and the VLC media player, which were the main applications I use.  I re-sized the windows to take up the entire visible part of the TV, and it works pretty good.

Thank you BicyclerBoy for your help. If I find anything better for the overscan, I'll post it here for others that find this thread.  I posted the part of my xorg.conf that BicyclerBoy helped me put together that got my display on the TV working.


```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8500 GT"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "SONY TV"
    HorizSync       28.0 - 55.0
    VertRefresh     43.0 - 72.0
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "ModeDebug" "TRUE"
    Option         "ConnectedMonitor" "DFP"
    Option         "UseDisplayDevice" "DFP-0"
    Option         "UseEDID" "TRUE"
    Option         "UseEDIDFreqs" "FALSE"
    Option         "UseEDIDDpi" "FALSE"
    Option         "TVStandard" "HD1080i"
    Option         "TVOutFormat" "AUTOSELECT"
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

---

### Post by BicyclerBoy on 2012-04-17
I have tried to find some logic in the presence/absence of the overscan comp slider..
nVidia commented couple years ago that the overscan comp requires shader scaling..
So some slow GPUs at high res can not scale.

I think the overscan slider function has just been missing in some driver versions.
Try disabling "full GPU scaling" for DFP-0

I have used a 9400GT with overscan comp on:
- HDMI 1280x768 TV
- DVI-D 1600x1200 DFP

You can make a virtual desktop bigger & smaller than physical (& offset this) to mimic the overscan correction.
You can do this immediately with xrandr extension (no logout/login).

As you say MythTV allows different video mode &/or screen size for GUI & full screen video.

You can try to add this to ~/.nvidia-settings.rc
0/OverscanCompensation[DFP-0]=32


I don't think you need the TVOutFormat option because you are not using an analogue (vga or s-video) output.

Can you post your /var/log/Xorg.0.log file ?

I think your TV has an EDID.
If you use UseEDIDDpi = false then you should add the actual DPI in the screen/monitor section.
Option                 "DPI" "75 x 75"
or add the measurement in monitor section
DisplaySize            286 179    # In millimeters
obviously measure your TV..
Setting the DPI allows you to enlarge the screen text/widgets & they stay the same actual size with different screen resolutions (good for old CRT TVs).

Sticking with gnome classic & no compiz is good plan that is more likely to **not suffer** compiz-redirection-vsync-tearing.

---

### Post by gitfiddler on 2012-04-25
gtippitt & BicyclerBoy

I have the same video card, and I also am trying to solve an overscan problem on my Toshiba DLP. I would be interested to hear if you make any progress on this problem.

gitfiddler :guitar:

---

