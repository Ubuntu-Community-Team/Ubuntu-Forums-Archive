---
title: "Ubuntu VGA out"
date: 2009-11-09
forum: Multimedia Software
---

### Post by mrdek11 on 2009-11-09
I'm trying to get my laptop to output to VGA so I can use my TV screen instead of the laptop screen.

I've looked everywhere for help connecting to it, but can't seem to find anything that works.

The "display preferences" window doesn't detect the TV, but the tv flickers when I click the "Detect monitors" button.

xrandr -q returns:
```
peterson@peterson-frontend:~$ xrandr -q
Screen 0: minimum 320 x 200, current 1280 x 768, maximum 1280 x 1280
VGA disconnected 800x600+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   800x600        85.1* 
LVDS connected 1280x768+0+0 (normal left inverted right x axis y axis) 305mm x 183mm
   1280x768       60.0*+
   1024x768       85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
TV disconnected (normal left inverted right x axis y axis)
peterson@peterson-frontend:~$ 
```

I tried:
```
xrandr --output VGA
``` but it only flickered the TV. (It flickers every time I run xrandr)

I tried: ```
xrandr --output LVDS --auto --output VGA --auto
``` 
which only flickered.

I then tried: ```
peterson@peterson-frontend:~$ xrandr --addmode VGA 800x600
peterson@peterson-frontend:~$ xrandr --output VGA --mode 800x600

```
This makes the TV at least recognize the input. It starts spitting out a bunch of static.

I'm not sure what to try next...

If anybody has any ideas, I'd really appreciate hearing them!

Thanks in advance,

Derek

[edit] I just realized that when the TV is spitting out static, it makes a humming noise. When I minimize a window, or otherwise change the screen significantly, the humming changes pitch.[/edit]

[edit] (again) It looks like the "static" is really a very unclear b/w tiling of my screen. I can very vaguely see the windows, and see them minimize, etc. I added a mode 1280x768 and applied it to VGA, and it now seems to be showing 3 tiles of my screen, but they're even harder to see.[/edit]

---

### Post by mrdek11 on 2009-11-10
lspci |grep 915 returns:
```

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)

```

I looked in my xorg.conf, which seemed to be completely default/generic.

So I searched around for specific instructions for this controller. I found: [https://wiki.ubuntu.com/HowtoSetupExternalMonitorForIntel915](https://wiki.ubuntu.com/HowtoSetupExternalMonitorForIntel915) as well as a few others, which did not work. They suggested that I use the "i810" driver. X would always open telling me the configuration was incorrect.

I tried replacing the "i810" with "intel" and it now boots, and I can fully use compiz, etc. However, running:
```
gdmflexiserver
``` and choosing "clone heads" doesn't display anything on my TV. It restarts X, but everything stays the same.

xrandr -q returns: ```
Screen 0: minimum 320 x 200, current 1280 x 768, maximum 1280 x 1280
VGA disconnected 1024x768+0+0 (normal left inverted right x axis y axis)
LVDS connected 1280x768+0+0 (normal left inverted right x axis y axis) 305mm x 183mm
   1280x768       60.0*+
   1024x768       85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
TV disconnected (normal left inverted right x axis y axis)

```

Again, I can add a resolution mode to VGA and run ```
xrandr --output VGA --mode 1024x768
``` to make the TV show a tiled and staticy version of my screen.

Can anybody help out?

Thanks,
Derek

---

