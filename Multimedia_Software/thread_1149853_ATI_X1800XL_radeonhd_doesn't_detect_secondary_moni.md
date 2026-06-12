---
title: "ATI X1800XL: radeonhd doesn't detect secondary monitor"
date: 2009-05-05
forum: Multimedia Software
---

### Post by VomitInc on 2009-05-05
Hello,

I'm one of the fglrx-using fools that upgraded to Jaunty, only to discover that the new X-server requires the Catalyst video driver >=9.4 to work... and that my X1800XL card is only supported up to <=9.3...

So I've been forced to the regular "radeon" driver, which did work and gave me a good dual head display.

But as I also want proper 3D, I'm trying to get the radeonhd driver to work.

First problem: no matter what I try in xorg.conf, only one monitor is detected.

There are two DVI displays attached, but DVI-I_1 refuses to be detected. I've toyed with the "HPD" option and then I suddenly got the other display but lost the first.
> xrandr 
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 2560 x 1024
DVI-I_1/analog disconnected (normal left inverted right x axis y axis)
DVI-I_1/digital disconnected (normal left inverted right x axis y axis)
TV_SVIDEO disconnected (normal left inverted right x axis y axis)
DVI-I_2/digital connected 1280x1024+0+0 (normal left inverted right x axis y axis) 360mm x 290mm
   1280x1024@60   59.9*+
   1280x1024      59.9  
   1024x768       60.0     59.8  
   800x600        60.3     59.9  
   640x480        60.0  
DVI-I_2/analog disconnected (normal left inverted right x axis y axis)


I presume these problems have something to do with the message

> (II) RADEONHD(0): Unknown card detected: 0x7109:0x1002:0x0B12.
        If - and only if - your card does not work or does not work optimally
        please contact [email]radeonhd@opensuse.org[/email] to help rectify this.
        Use the subject: 0x7109:0x1002:0x0B12: <name of board>
        and *please* describe the problems you are seeing
        in your message.

in the Xorg.0.log.

lspci:
> 06:00.0 VGA compatible controller: ATI Technologies Inc R520 [Radeon X1800]
06:00.1 Display controller: ATI Technologies Inc R520 [Radeon X1800] (Secondary)


> sudo rhd_conntest 06:00:0
rhd_conntest: v1.2.5, non-git sources
Found card: ATI Technologies Inc - R520 [Radeon X1800]
Checking connectors on 0x7109, 0x1002, 0x0B12  (@06:00:00):
  Load Detection: RHD_OUTPUT_TMDSA
  HotPlug: RHD_HPD_0
  DDC: RHD_DDC_0 RHD_DDC_1


> sudo rhd_conntest 06:00:1
rhd_conntest: v1.2.5, non-git sources
Unknown device: 0x1002:0x7129 (06:00.01).


Is there a way of specifying/overriding this unknown ID as some module parameter without having to patch/recompile stuff? Or otherwise get dual head to work?

(using the "radeon" with the default minimalistic xorg.conf the randr detection works fine:)
> xrandr
Screen 0: minimum 320 x 200, current 2560 x 1024, maximum 2560 x 1024
DVI-1 connected 1280x1024+1280+0 (normal left inverted right x axis y axis) 360mm x 290mm
   1280x1024      60.0* 
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
DVI-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024      75.0     60.0* 
   1024x768       75.0     70.1     60.0  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     59.9  
   720x400        70.1  


---

