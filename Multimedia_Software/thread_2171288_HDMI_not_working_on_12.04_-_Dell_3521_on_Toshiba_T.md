---
title: "HDMI not working on 12.04 - Dell 3521 on Toshiba TV Model 32C120U"
date: 2013-08-30
forum: Multimedia Software
---

### Post by johnjanney on 2013-08-30
I have a Dell Inspiron 3521 (advertised as a Dell Inspiron 15RV) with a fresh 12.04 install. 

I tried connecting it to my Toshiba TV via HDMI (both HDMI 1 and HDMI 2), but I got a "no video signal" message on one and an "Unsupported Video Signal" message on the other (from the TV). My laptop detects the TV just fine, but the TV doesn't seem to want to recognize the computer output. When I rebooted my laptop, the Ubuntu logo with the dots underneath appeared on the TV screen, but then the TV returned the "Unsupported Video Signal" error again when the laptop went to the login screen.

I search the forums, but couldn't find an easy-to-follow solution for my model combinations. 

I connected the TV and ran xrandr with the following output. If anyone can help me get this working, I would greatly appreciate it. 

> $ xrandr
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 32767 x 32767
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 194mm
   1366x768       60.0*+   39.9  
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 1600mm x 900mm
   1920x1080      60.0 +   24.0  
   1920x1080i     30.0  
   1280x1024      60.0  
   1360x768       59.8*    60.0  
   1280x720       60.0  
   1024x768       60.0  
   1440x480i      30.0     30.0  
   800x600        60.3  
   720x480        59.9  
   640x480        60.0     59.9  
DP1 disconnected (normal left inverted right x axis y axis)


Here are the video specs for the laptop:

[TABLE="class: section_device_title, width: 857"]
[TR]
[TD="class: section_device_title_text"]Video Card - Intel(R) HD Graphics[/TD]
[/TR]
[/TABLE]
[TABLE="class: section_device_property, width: 857"]
[TR]
[TD="class: section_device_property_block"][/TD]
[TD="class: section_device_property_key0, bgcolor: #EBEBEB"]Vendor Name[/TD]
[TD="class: section_device_property_value0, bgcolor: #EBEBEB"]Intel Corporation[/TD]
[/TR]
[TR]
[TD="class: section_device_property_block"][/TD]
[TD="class: section_device_property_key1"]Interface[/TD]
[TD="class: section_device_property_value1"]PCI[/TD]
[/TR]
[TR]
[TD="class: section_device_property_block"][/TD]
[TD="class: section_device_property_key0, bgcolor: #EBEBEB"]Video Card Chip Type[/TD]
[TD="class: section_device_property_value0, bgcolor: #EBEBEB"]Intel(R) HD Graphics Family[/TD]
[/TR]
[TR]
[TD="class: section_device_property_block"][/TD]
[TD="class: section_device_property_key1"]Video Card Memory[/TD]
[TD="class: section_device_property_value1"]1.75 GB[/TD]
[/TR]
[TR]
[TD="class: section_device_property_block"][/TD]
[TD="class: section_device_property_key0, bgcolor: #EBEBEB"]Video Card BIOS[/TD]
[TD="class: section_device_property_value0, bgcolor: #EBEBEB"]Intel Video BIOS[/TD]
[/TR]
[TR]
[TD="class: section_device_property_block"][/TD]
[TD="class: section_device_property_key1"][/TD]
[TD="class: section_device_property_value1"][/TD]
[/TR]
[/TABLE]
[TABLE="class: section_device_title, width: 857"]
[TR]
[TD="class: section_device_title_text"]Display - Generic PnP Monitor[/TD]
[/TR]
[/TABLE]
[TABLE="class: section_device_property, width: 857"]
[TR]
[TD="class: section_device_property_block"][/TD]
[TD="class: section_device_property_key0, bgcolor: #EBEBEB"]Mode[/TD]
[TD="class: section_device_property_value0, bgcolor: #EBEBEB"]1366 x 768 (32-bit) (60 Hz)[/TD]
[/TR]
[TR]
[TD="class: section_device_property_block"][/TD]
[TD="class: section_device_property_key1"]Preferred Mode[/TD]
[TD="class: section_device_property_value1"]1366 x 768 (59 Hz)[/TD]
[/TR]
[TR]
[TD="class: section_device_property_block"][/TD]
[TD="class: section_device_property_key0, bgcolor: #EBEBEB"]Signal Type[/TD]
[TD="class: section_device_property_value0, bgcolor: #EBEBEB"]Digital[/TD]
[/TR]
[/TABLE]

---

### Post by johnjanney on 2013-12-27
I installed disper, but it did not solve this issue. Anyone have any ideas?

---

### Post by johnjanney on 2013-12-29
SOLVED: Disper did provide some insight into what resolutions were supported, and it turns out that the resolution I was trying to clone from my laptop to the TV was not compatible with the TV. I changed 1366x768 to 1360x768 on my laptop and it worked. Such a simple solution. I can now mirror my display on the TV via HDMI.

---

