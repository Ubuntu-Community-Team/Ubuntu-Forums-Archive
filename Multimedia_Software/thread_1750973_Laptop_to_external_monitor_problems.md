---
title: "Laptop to external monitor problems"
date: 2011-05-06
forum: Multimedia Software
---

### Post by brunobliss on 2011-05-06
Hey guys, i have an [eeepc asus 1005px]("http://newtechnotebook.com/uncategorized-asus-eee-pc-1005px-review-and?wpmp_switcher=mobile") and everything works like a charm in ubuntu, that is until i need to plug an external monitor:

1. When turning the laptop on with the VGA cable already connected, the background turns black and i get no desktop effects (compiz not working)

2. Plugging in the monitor after the logon, gives me a background view only like a separate area of the desktop which can  be solved it point 3. but:

3. If i chose same image in all monitors the resolution will simply go down to 800x600 and again, no desktop effects whatsoever.

Are these known problems?
I'm using Ubuntu 10.04

Thanks in advance.

---

### Post by Hoora on 2011-05-08
I have got the same netbook, eeepc 1005px. I haven't used Ubuntu 10.04 on this machine, since I got it only a month ago.

External monitor was working fine with the Linux Mint 10 (it is based on the Ubuntu 10.10). The external monitor was positioned "above" the laptop screen. Maybe you would like to upgrade to a more recent version to get rid of the out of date compiz problems? I had no problems with Linux Mint 10.

Today I installed Ubuntu 11.04 Natty, and it seems to be working pretty nice too. The first install I tried was with btrfs filesystem but it was very slow so I did a re-install with ext4. Only a few things bother me. 

Opening new windows will end up the window titlebar to open behind the top panel in the laptop screen. I tried to change the "CompizConfig Settings Manager" plugin "Place Windows" option "Placement Mode" to Centered but they still keep on to be placed under the panel on top of the below screen, which is the netbook screen. Also when you drag a window from the external monitor to the laptop screen (from the upper to lower), the Sticky Windows on Compiz gets stuck on the panel located on top of the netbook screen, thus stopping the mouse movement and disabling window dragging. Window titlebar is left in the external window. 

Third and a minor annoyance is that the mouse pad does not work to select text on a one and a half click (if you know what I mean). You have to tap the pad for 2½ times. But sometimes it works like it should, it's weird and I haven't noticed any pattern to it.

---

### Post by brunobliss on 2011-05-23
**Point 1** Got solved probably with updates.

**Point 2** instead of choosing same image in all monitors, i'll simply fn+F5 till i get the hardware doing that clone image setup.

**Point 3** is solved by simply re-enabling desktop effects.

I'm pretty sure this last one can be fixed with some tweaking, i believe i just didn't search enough.

---

### Post by Hansholz on 2011-05-23
I have the same problem but I don't understand how you guys solved it. I have an EeePC 1005HA with Intel 945G chipset and graphics. I got a 21" touchscreen to link to the laptop with the intention of hiding the laptop away behind it and simply using the tactile widescreen with virtual keyboard. 

My problem is that I have mirrored the screens but the bigger one will only display in 800x600 (as does the netbook even though it's a wide screen) I want to be able to run the large screen in something like 1024x600 or better, as long as its 16:9.

Cant seem to work it out. The Monitor Config don't give me any higher options than 800x600. This is the output of xrandr. If it's any help. Also my xorg.conf file is practically empty. Can anyone please help?

xrandr
```
Screen 0: minimum 320 x 200, current 800 x 600, maximum 4096 x 4096
LVDS1 connected 800x600+0+0 (normal left inverted right x axis y axis) 220mm x 129mm
   1024x600       60.0 +   65.0  
   800x600        60.3*    56.2  
   640x480        59.9  
VGA1 connected 800x600+0+0 (normal left inverted right x axis y axis) 477mm x 268mm
   1920x1080      60.0  
   1600x1200      60.0  
   1680x1050      60.0  
   1280x1024      75.0     60.0  
   1440x900       59.9  
   1280x960       60.0  
   1152x864       75.0  
   1280x720       60.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3*    56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1 
```

xorg.conf ... not sure if this is actually being used??
```
# Minimal xorg.conf for the Nouveau driver

Section "Device"
	Identifier	"Default screen"
      	Driver		"nouveau"
EndSection
```
 
Thanks in advance

---

