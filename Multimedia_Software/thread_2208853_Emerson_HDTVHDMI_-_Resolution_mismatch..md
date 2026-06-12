---
title: "Emerson HDTV/HDMI - Resolution mismatch."
date: 2014-03-02
forum: Multimedia Software
---

### Post by Curtis_Mattoon on 2014-03-02
Hi all,
I'm trying to configure XBMC on Linux Mint 15 with an Emerson LC320EM2 HDTV. When I boot the computer, the bootloader shows up fine, but once booted into Mint, the TV displayed the following error:
> The TV does not support the output format, video resolution and/or refresh rate being sent by the connected device. Please refer to the user manual of this TV for a list of supported input formats, resolutions and refresh rates and modify the settings of your connected device.

Product: [http://www.walmart.com/ip/Emerson-32-Class-LCD-720p-60Hz-HDTV-LC320EM2/16775701#Specifications](http://www.walmart.com/ip/Emerson-32-Class-LCD-720p-60Hz-HDTV-LC320EM2/16775701#Specifications)
Service Manual: [http://www.funaiservice.com/manuals/EMERSON/LC320EM2/LC320EM2.pdf](http://www.funaiservice.com/manuals/EMERSON/LC320EM2/LC320EM2.pdf)
(pages 10, 25 deal with HDMI)

I currently have SSH access to the machine via my laptop, and have run:

```
export DISPLAY=:0.0
```

When I change the resolution with "xrandr -s [resolution]" , the error message goes away for a few seconds then reappears. So it appears I'm affecting the right display with my commands.

I cannot find any resolution/display size settings on the TV menu (only RGB/Gamma adjustment). I've tried both HDMI ports as well.

**Output of "xrandr":**
```
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 16384 x 16384
HDMI-0 connected 1024x768+0+0 (normal left inverted right x axis y axis) 16mm x 9mm
   1920x1080      60.0 +
   1920x1080i     30.0  
   1360x768       60.0  
   1280x768       60.0  
   1280x720       60.0  
   1024x768       60.0* 
   800x600        60.3  
   720x480        59.9  
   640x480        60.0     59.9  
   1368x768_60.00   60.0  
DVI-0 disconnected (normal left inverted right x axis y axis)
VGA-0 disconnected (normal left inverted right x axis y axis)

```

Per another forum post, I've used gtf to generate the last modeline (1368x768_60.00), which has curiously adjusted the intended resolution of 1366x768 upwards by two pixels. I'm not sure if this matters, but the TV appears to be very particular about the resolutions.

Each resolution gives the original error message (above), Occasionally, I'll also get a "Resolution mismatch! Change device's resolution." error, mostly with the new modeline. I haven't noticed anything in particular that gives me the resolution mismatch error versus the original one.

So, my question is: What am I doing wrong? I'm not much of an A/V person, so I'm not sure if there are some obvious n00b mistakes I'm making with the resolution or other settings.

Thanks!

This setup worked fine on our other LG HDTV.

---

### Post by trag on 2014-04-14
[COLOR=#000000]your tv's native resolution is 1366x768 while in VGA mode. your TV can receive only a limited number different resolutions under HDMI,and your pc can only push out a limited number of different resolutions under HDMI.Because there is no common resolution that your pc/tv can share your will experience overscan on your monitor. If using a VGA cable is not an option for your setup than I recommend adding a VGA/HDMI adapter to the HDMI cable.The sound will still be transmitted via HDMI but the video signal will be captured and converted to VGA before making it to your tv. Go to your tv's settings and have it receive via VGA instead if HDMI and you will then get your full native resolution of 1366x768.[/COLOR]

---

