---
title: "2nd monitor display goes off-screen"
date: 2008-05-30
forum: Multimedia Software
---

### Post by inanutshellus on 2008-05-30
I have a dual monitor setup, one connected via a DVI cable, the other a standard analog VGA cable. The resolution of the analog one is incorrect, with the right and bottom edges of the desktop going off-screen. The fonts seem slightly blurry as well, as though the entire screen is just slightly zoomed in. 

The monitors are both 19" dell flat panels (1908fp and a 1907fp), so they're the same size, same resolution capabilities, etc. 

I've tried a dozen different xorg.conf changes, aticonfig and dpkg-reconfigure commands... and best case I end up where I started, but usually it ends up going nuts. I've attached a couple of the xorg.confs that display this issue. 

Any suggestions? :( Are there other files than xorg.conf that control the X display?

---

### Post by inanutshellus on 2008-06-02
bump!

I have a habit of asking for help on Friday afternoons... never works out well!

---

### Post by inanutshellus on 2008-06-02
A bit more information... I have it set up as "BigDesktop" currently, with my resolution set to "2560x1024". 

```
**$ xrandr**
Screen 0: minimum 320 x 200, current 2560 x 1024, maximum 2560 x 1024
default connected 2560x1024+0+0 0mm x 0mm
   2560x1024      60.0* 
   1280x1024      75.0     70.0     60.0  
   1280x768       60.0  
   1152x864       75.0     70.0     60.0  
   1024x768       75.0     72.0     70.0     60.0  
   1024x480       60.0  
   800x600        60.0     75.0     72.0     70.0     56.0  
   848x480        60.0  
   720x576        60.0  
   720x480        60.0  
   640x480        75.0     72.0     60.0  
   640x400        75.0     60.0  
   640x350        60.0  
   512x384        60.0  
   400x300        75.0     60.0  
   320x240        75.0     60.0  
   320x200        75.0     60.0  

**$ sudo lspci | grep -i vga**
01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Mobility Radeon X300]

```

Interestingly, when I take screenshots, they *look* as though everything matches up visually, but it doesn't! In the provided screenshot the Firefox window completely fills my monitor... :confused:

---

### Post by inanutshellus on 2008-06-03
Help!

---

### Post by Pjotr123 on 2008-06-03
You could try this:
[http://ubuntutip.googlepages.com/bugsinubuntu](http://ubuntutip.googlepages.com/bugsinubuntu)
(number 2)

---

### Post by inanutshellus on 2008-06-03
> **Pjotr123 said:**
> You could try this:
[http://ubuntutip.googlepages.com/bugsinubuntu](http://ubuntutip.googlepages.com/bugsinubuntu)
(number 2)

displayconfig-gtk has never really worked for me. It may be user error, it may be the PCs / laptops I've used it on, it may be the dual-monitor thing, but pretty much every possible configuration I try with displayconfig-gtk ends up with either a 100% locked pc (hard reboot required) or a 15 second black screen followed by the program bottoming out and closing. 

That being said, I will try without fglrx again and see how that goes.

---

### Post by inanutshellus on 2008-06-04
Ok so I've uninstalled fglrx and am now using the "ati" driver ... and I still get the same issue! I haven't even enabled dual monitor support yet! 

I'm wondering if my "monitor" and my "screen" (assuming i'm using the right terminology) are not using the same resolution. My monitor (physical) reports that it is 1280x1024 but the output of xrandr seems to think it's 1400x1050, which would explain why there's the extra pixels!

```

$ xrandr
Screen 0: minimum 320 x 200, current 1400 x 1050, maximum 1400 x 1200
VGA-0 connected (normal left inverted right)
   1280x1024      60.0 +   75.0     59.9  
   1152x864       74.8  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
DVI-0 connected 1280x1024+0+0 (normal left inverted right) 376mm x 301mm
   1280x1024      60.0*+   75.0     59.9  
   1152x864       74.8  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
LVDS connected 1400x1050+0+0 (normal left inverted right) 0mm x 0mm
   1400x1050      60.0*+
   1280x800       60.0  
   1280x768       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
S-video disconnected (normal left inverted right)

```

That is, if I'm reading xrandr's output correctly. wth. 

The saga continues.

---

### Post by inanutshellus on 2008-06-06
So after a week of fiddling... removing the proprietary ati drivers, failing to configure the open source ones, custom compiling the latest ati drivers, reconfiguring again... I'm back to where I started. 

Dag nabbit.

With the open source ati drivers my VGA-input monitor had a huge black bar on the left and top of the screen. Using the monitor's positioning controls I *was* able to move the display closer to the left and up, but nowhere near as far as would be needed. 

ah well. I guess I'll just stop maximizing stuff. Heh.

---

### Post by aeiah on 2008-06-06
have you tried messing with the 'ignore EDID' flags in xorg? maybe your monitor is reporting that it has far more pixels than it actually does

---

### Post by inanutshellus on 2008-06-06
Hm... never heard of it, I'll take a look!

---

### Post by markbuntu on 2008-06-06
Have you tried fooling around with the Catalyst Control Center?
It comes with the ATI driver and lives in your menus somewhere. Usually in Applications/Other.

It has options for scaling the monitors and setting their refresh rates and resolutions, etc. You need to ctrl-alt-backspace after making changes to reset x but you probably know that already.

I have had the most luck with changing one thing at a time and then resetting.

---

### Post by inanutshellus on 2008-06-09
> **markbuntu said:**
> Have you tried fooling around with the Catalyst Control Center?

```
**$ amdcccle**
The program 'amdcccle' is currently not installed.  You can install it by typing:
sudo apt-get install xorg-driver-fglrx
bash: amdcccle: command not found
**$ sudo apt-get install xorg-driver-fglrx**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xorg-driver-fglrx is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

I notice that the Catalyst Control Center was developed by AMD... and I have a pentium based laptop... I'd assume it would still work, but I'm apparently doing something wrong.

---

### Post by inanutshellus on 2008-06-13
> **markbuntu said:**
> Have you tried fooling around with the Catalyst Control Center?
It comes with the ATI driver and lives in your menus somewhere. Usually in Applications/Other.

It has options for scaling the monitors and setting their refresh rates and resolutions, etc. You need to ctrl-alt-backspace after making changes to reset x but you probably know that already.

I have had the most luck with changing one thing at a time and then resetting.

(The confusion about AMD turned out to be because AMD *owns* ATI now!)

You rock Markbuntu! CCC worked perfectly. I rebooted after trying the Image Scaling section (which, oddly, didn't affect my xorg.conf... *ponder*) and the image was off-center with a thin black bar at the left and top. Using the positioning controls didn't *quite* do it, so I tried resetting the monitor to factory settings and voila, perfection!

Thank you!

:KS:guitar::popcorn::KS

---

### Post by markbuntu on 2008-06-13
The newer ati drivers do not read xorg.conf unless you force them to with this command:

sudo aticonfig --input=/etc/X11/xorg.conf --tls=1

I know this causes a lot of confusion for people trying to configure with xorg.conf but since xorg.conf is mostly empty that should be a clue that the configuration is happening somewhere else. The actual configuration file is something like amdcccle.conf but this cannot be edited by hand and must be edited with aticonfig.

If you want to tweak your new ati driver for best performance, especially with compiz check this thread out:

[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)

These tweaks make a huge difference with the 8.4 (current) driver if you don't want to go through the trouble of getting the 8.5 driver.

Be sure to thank djdoo.

---

### Post by pather on 2008-06-19
Hi guys,
i seem to have the same problem, but your solution works just partialy.
I run kubuntu 8.04 and both 8-5 and 8-6 catalyst drivers "shrink" my screen size for about 10%
I use ATI X1900XT and dual-head mode. Primary monitor (which causes the problem) is LCD TV Hyundai E320D (no drivers until 8-5 have this problem) and my secondary monitor is ordinary LCD 19''
Resolutions are 1360x768 for TV (connected thru DVI) and 1280x1024 for LCD (DVI and VGA reduction, because the LCD had only VGA input)

When I turn image scaling in CCC off, image is no longer scaled, but right and bottom sides are missing...

I really want to use 8-5 or 8-6 catalyst, because video is no longer flickering, annoying few GB large logs are history and overall quality of video is just superb. But this issue really brings the joy down :)

So if anyone has anything that could help, i would be gratefull:)

Thanks a lot

---

### Post by markbuntu on 2008-06-19
I have a 24 inch and a 19 inch monitor in big desktp mode and what worked best for me was to have the larger one as monitor 1. You can do this in Catalyst Control Center.

You can force the monitor resolutions with aticonfig. type aticonfig --help for (vague) directions. Do not try to force your monitor into some modeline it does not have.

You can find all the available modelines for each monitor in the var/log/Xorg.0.log

---

### Post by pather on 2008-06-21
The first monitor is the widescreen in my case. Frankly I dont know how to force it to be another way, because no matter what I do, digitaly connected monitor always go as first one. I even tried to switch the cables on my card and DVI>HDMI is always used as primary monitor.

I did not tried to disconnect my second monitor off, because frankly, I really want to use both of them. 

Strange thing is, the windows drivers behave the same way. Even there was was picture of my widescreen shrinked to 90% of its original size. So this gave me the idea that the fatal error is not on my side, but its ATIs fault.

On the other hand, author of this thread claimed he solved this out. 

I really like k/ubuntu, really hates windows and most of this OSs I preffer OS X, because I am big fan of macs. This piece of OS simply works and thats what I want. 

But I still want to resolve this issue. When I will be really desperate, I fill out the form on ATI site. I did that one time and it looks to me, like they actually read those things :) Which is pretty good.

Thank you for your time anyway.

---

