---
title: "Envy NG had errors during driver install"
date: 2008-06-30
forum: Multimedia Software
---

### Post by ZippyP on 2008-06-30
Hello

I installed Envy ng with core which went fine. After running Envy there were multiple errors during the uninstall of nvidia-gtx-new ( ver. 169?)and during the beginning of the new driver install.  I had up to 1080i (1920 x 1080) resolution.  I am now stuck with 640x480 and 800x600.  I can read my screen now without my glasses, which I was not aiming for.  I tried to reinstall the original driver which seemed to go fine but I still can't go beyond the low resolution.  I Tried again with Envy and again the same errors.  Seems that it can't delete the old drivers due to, I guess missing folders? Again I reinstalled the drivers and again low resolution. I spent over a couple of hours with this including trying to activate the drive using [color=red]sudo nvidia-xconfig[/color] and [color=red]sudo nvidia-glx-config enable[/color]. I would like to add an updated driver but it looks as if I am stuck in low res for now.  This all started with a problem with the RGB Component out missing the red line.  So instead of Ubuntu being a nice brown background it was a washed out blue.  The component out works fine with other system programs, so I know it is working.  I am also a Broadcast Eng. which I am used to Component cabling, but I am far from being a Linux programmer, I'm a newbie.  After this is fixed I will go back to figuring out Mythbuntu and the stb0899 driver that I was working on before being sidetracked trying to make the component video work correctly.  I was almost at the point of removing Ubuntu and reinstalling it, but this is not the other guy's OS so I feel this could be fixed.
Any help in getting me back on track with the NVidia drivers would be greatly appreciated.
Below is the system I am working with.

Thanks

Motherboard: MSI K9NGM3 (HDMI)
AMD Athlon 64x2 4000 (2.1G)
Ram: 2G / 6400 Corsair Memory
NVidia 7050 on board video w/ HD HDMI out
OS: Ubuntu / Mythbuntu
Monitor: 42" Visio 1080P

---

### Post by NT4usB on 2008-06-30
Have you read the [faqs?]("http://albertomilone.com/envyngfaq.html") NG is for Hardy, you using Hardy?
Did you uninstall old Envys before installing NG?
Run it as root (sudo envy -i)?
Did you try Envy Legacy?
iirc, there's two # options for removing old drivers. You try both?
Try:```
 Ctrl+Alt+F1 (to get to a terminal)
sudo /etc/init.d/gdm stop
sudo envy -i (uninstall, uninstall, install...)
sudo /etc/init.d/gdm start
```

Then, there's always enabling the restricted drivers manager and letting it install them...

---

### Post by ZippyP on 2008-06-30
Thanks for your help NT4usB

I ended up having to run the restricted drivers manager.  That fixed it but now I'm back to my original issue, and that is the washed out blue video from the component RGB cable.  Ubuntu should be various shades of browns and yellows.  It seems that the red signal is not working from the computer component output.  The cable is good since it works in Gentoo.  I have that on a CF card as a second boot device.  This is the on;y problem with the video now.  If I look at it with the VGA out it is fine.  The Component RGB output just does not seem to work with Ubuntu.

Thanks again.

---

### Post by NT4usB on 2008-07-01
I had the similar trouble with my MythTV setup, RGB to TV (blue tinted picture.)
My solution was first, rtfm on the TV to see what it supported then configuring xorg to that. Turns out, the only supported RGB was HD480i.
The relevant section is below:```
Section "Screen"
    Identifier     "Screen[0]"
    Device         "Device[0]"
    Monitor        "Monitor[0]"
    DefaultDepth    24
    Option         "SecurityTypes" "VncAuth"
    Option         "UserPasswdVerifier" "VncAuth"
    Option         "PasswordFile" "/root/.vnc/passwd"
    Option         "VideoOverlay" "on"
    Option         "OpenGLOverlay" "on"
    Option         "TVStandard" "HD480i"
    Option         "ConnectedMonitor" "TV[0]"
    SubSection     "Display"
        Depth       24
        Modes      "1024x768"
    EndSubSection
EndSection

```

---

### Post by ZippyP on 2008-07-04
Hi NT4usB

This TV covers Inputs of: 1080P(Full HDTV), 1080i (HDTV), 720P (HDTV), 480P ( EDTV) and 480i (SDTV)
Computer (VGA):640x480, 800x600, 1024x768, 1280x1024 and 1920x1080
Component (RGB) Same as above.  HDMI: Same as above.
The component in for this TV covers to 1080i/P at 1920x1080. I used it before with a HD cable box before I bought my HDMI cable. 
The TV will indicate what type of resolution the input is receiving when you hit info on the remote.

I'll have to check the xorg file.  Is there a table to use to set the xorg file to the right parameters?  Looking at it it seems pretty simple, there is only a couple of lines to change.
Option      "TVStandard" "HD1080i"
Modes      "1920x1080"
I haven't tried it yet, if it works I will post my findings here.

Thanks again

---

### Post by NT4usB on 2008-07-05
Don't know of any charts but here's the [xorg manual]("http://ftp.x.org/pub/X11R6.9.0/doc/html/xorg.conf.5.html"). It's all pretty straightforward until you get into things like modelines and stuff.
Hardy is weird with how it uses all the generic settings in xorg. I couldn't figure it out so I replaced it with one I've been using since Dapper.

---

