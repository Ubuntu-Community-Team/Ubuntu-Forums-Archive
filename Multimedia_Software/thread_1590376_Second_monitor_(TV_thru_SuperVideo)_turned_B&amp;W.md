---
title: "Second monitor (TV thru SuperVideo) turned B&amp;W after Nvidia Driver installed"
date: 2010-10-07
forum: Multimedia Software
---

### Post by guntu on 2010-10-07
Hi,

I have the latest Ubuntu installed and I have my computer hooked up to the TV as a second monitor and everything was working fine.  Then I installed the "Nvidia accelerated graphics driver (version current) [Recommended]" and now when I have the second monitor - which is my TV through Super Video cable - the image on the TV appears Black and White. 

Does anyone know why this is and how to fix it? 

When I go to **System > Preferences > Monitor** I get the following message: 

"It appears that your graphic driver does not support the necessary extensions to use this tool. Do you want to use your graphics driver vendor's tool instead?"

I click "Yes" and play around with the settings but I'm not able to get the second monitor (TV) to be in colour and keeps showing B&W. 

Any thoughts? 

Thanks,

---

### Post by guntu on 2010-10-07
I forgot to mention that I have an HP Pavillion dv2000 laptop, in case that makes that matters...

---

### Post by guntu on 2010-10-09
Ok, I finally found the solution and got it working!  :P

I thought I should share it here.. 

Laptop:  HP Pavilion dv2000
Linux version:  Ubuntu 10.04
Graphic Card:  NVIDIA GeForce Go 7200 
Driver installed: NVIDIA accelerated graphics driver (version current) [Recommended]

Background: 

The problem I think came because I bought this laptop in the US (video format: NTSC) and I'm convecting to the TV in the UK (video format: PAL-I), so I got a video signal on the TV but the was only B & W. 

To fix it: 

 I found this forum thread: [https://help.ubuntu.com/community/NvidiaTVOut](https://help.ubuntu.com/community/NvidiaTVOut)  that shows you how to back up the "xorg.conf" and then edit it to make the adjustments for the video format, from NTSC to PAL - in my case. 

What you need to do is: 

1 ) Connect your laptop to the TV using your preferred method. I'm using a S-Video cable. 
2) Go to: **Administration > Nvidia X Server Settings**
3) Under X Server Display Configuration, click on "Detect Displays". You will see on the Layout window (above the buttons) that the you will now have two monitors, one is the "Nvidia Default Flat Panel" and the second one is the "TV-0"
4) Click "Save to X Configuration File" , follow the steps to save it, if prompted.
5) Click "Quit" to close the Nvidia X Server Settings.
6) Open the Terminal 
7) Back up the "xorg.conf" by typing : sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup 
8) Type: gksudo gedit /etc/X11/xorg.conf  , to open and edit the "xorg.conf" 
9) Locate ' Selection "Screen" '  , this is what refers to the TV or second monitor. 

If you have the same issue as me , getting the signal in B&W, and you identify that it may be due to a NTSC/PAL problem, then compare what's in your " xorg.conf "  and the following and add accordingly :

Section "Screen"
    ...
    Option         "TwinView"
    Option         "TVOutFormat" "SVIDEO"
    Option         "TVStandard" "NTSC-M"
    Option         "MetaModes" "1440x900,640x480; 1440x900,NULL; 1024x768,NULL; 800x600,NULL; 640x480,NULL"
    SubSection     "Display"
        ...
        Modes      "1440x900" "1280x1024" "1024x768" "720x450" "640x480"
    EndSubSection
EndSection


For example in my case the original xorg.conf file looked like this: 

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "DFP: nvidia-auto-select +0+0, TV: 1024x768 +1280+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


All I did was add the two lines that refer to how I'm sending the signal out (SVIDEO) and the format for the video (PAL-I) , which is obviously different fom the original forum thread and will maybe different for each case - the changes are marked in Bold: 

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
[B]    Option         "TVOutFormat" "SVIDEO"
    Option         "TVStandard" "PAL-I"[/B]
    Option         "metamodes" "DFP: nvidia-auto-select +0+0, TV: 1024x768 +1280+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


I saved the "xorg.conf" file and rebooted and it's now working like a charm!!

---

