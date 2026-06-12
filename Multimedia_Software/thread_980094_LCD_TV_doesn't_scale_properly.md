---
title: "LCD TV doesn't scale properly"
date: 2008-11-12
forum: Multimedia Software
---

### Post by Dodi cool on 2008-11-12
hey
i have a 32" LCD TV with HDMI port. ( tech specf. [http://www.soyo.com/product/Televisions/4/Priv%E9_-_32%26quot%3B_LCD_HD-Ready_TV/390](http://www.soyo.com/product/Televisions/4/Priv%E9_-_32%26quot%3B_LCD_HD-Ready_TV/390) )

i bought a new desktop computer that has Asus P5Q-EM motherboard and the video card is Intel Graphics Media Accelerator X4500HD integrated.

i first installed Windows Vista and had problem with scaling the TV, I had to go change the horizontal and vertical aspect ratio to scale it properly because changing screen resolution couldn't help.

then, i installed Ubuntu 8.10 and have the same problem that it not scaled properly to the TV. I went to Preferences and then Screen Resolution, tried to change the resolution, but every time i change it to a resolution that is not supported by the TV, the display disappears and i find no way to get back to the Ubuntu unless if i reinstall it, and that what happened twice.

I found that when i go to Screen Resolution, in the yellow box , it says TPS 35" while my TV is 32" . So, the problem that is the computer recognizes the TV as 35". 

is there any way to make it scaled properly ? or change the vertical and horizontal aspect ratio manually from the command line because Ubuntu doesn't have a property to scale the horizontal and vertical width for the Intel Video Card ? 

I'm so confused because I bought the computer for my Linux-based studies while Windows worked good!.

Any solution ?

---

### Post by Dodi cool on 2008-11-12
anyone for help ?

---

### Post by Dodi cool on 2008-11-13
come'on Linuxers !

i'm new to this OS i need help guys.

---

### Post by xc3RnbFO8P on 2008-11-13
I dont know if it works.
Try, 
ALT-F2 
gksudo gnome-display-properties
see if can you use Generic (1920x1080)

---

### Post by orduek on 2008-11-13
> **Ringi said:**
> I dont know if it works.
Try, 
ALT-F2 
gksudo gnome-display-properties
see if can you use Generic (1920x1080)

this option does not alow to change the scale (my TV is 26 and it thinks its 32).

---

### Post by xc3RnbFO8P on 2008-11-13
> this option does not alow to change the scale (my TV is 26 and it thinks its 32
Hardy or Intrepid?
HD Ready or Full HD?
Graphic card?

---

### Post by orduek on 2008-11-13
Same motherboard (means X4500HD intel graphic card).
HD ready, Metz LCD 26''
Mythbuntu 8.10

Thank you.

---

### Post by Dodi cool on 2008-11-13
i don't guys
i provided all informations
any help please ?

---

### Post by Tharangalion on 2008-11-13
Not entirely sure if this will help. I'm fairly new too.
I had a problem with 'Frequency Out of Range'. The screen would go black and I had to restart.
This was on Kubuntu Hardy Heron.

My screen resolution is 1400x1050 @ 60Hz
To solve this problem, I had to change the xorg.conf file in the ETC > X11 folder.
You will need to edit the file as root, if you want to attempt it.

I searched around the Internet and found that I had to add/change the HorizSync and VertRefresh settings:
Try to find the Horiz and Vert rates your your monitor.

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	[B]HorizSync 31.0-80.0
	VertRefresh 56.0-76.0[/B]
EndSection

I have an ATI Radeon HD card, and my monitor is not the same as yours.

Before you change xorg.conf save it as a different file, such as xorgoriginal.conf

It may also be necessary to install a proprietary driver from the SYSTEM > HARDWARE DRIVERS MANAGER menu.

If you are referring to the font size being too large for the display, which pushes windows off the display area, you may need to force the DPI to 96dpi.

Go to SYSTEM SETTINGS > Look & Feel > Fonts

I hope this helps,

Lee.

---

### Post by orduek on 2008-11-14
when I tried gnome-display-properties, the screen is up and I can choose the right resolution (1360X768) but can't press Apply, it does nothing. and when I press Close it goes out.
:(

---

### Post by xc3RnbFO8P on 2008-11-14
> when I tried gnome-display-properties, the screen is up and I can choose the right resolution (1360X76 but can't press Apply, it does nothing. and when I press Close it goes out.

What about 1280x720?

---

### Post by orduek on 2008-11-14
there is no such option.

---

### Post by clancymf on 2008-11-14
The problem you have (I currently have it too) is called overscanning. 

By changing the resolution it just maked the desktop bigger or smaller but still doesn't fix the fact that the machine thinks your screen is physically larger than it is. 

Being that most people on this forum use a typical monitor, I have found that this problem is unknown to most.  You may want to check out HTPC, Myth, XBMC... forums. Since those users normally use their computers with TVs.

Basically what I have learned in the past two days of troubleshooting (i still have not solved) is that we are going to have to manually edit the xorg.conf file with a "custom modeline" to tell the computer what our screen ratio actually is.  I have my customer modeline ready but can't get it to work with the nvidia drivers that are currently installed.  Google could be your friend but as I have said it hasnt helped me out much yet.

---

### Post by orduek on 2008-11-14
I still didn't find answer on google.
if you find something, let me know please.
thank you.

---

### Post by Dodi cool on 2008-11-14
hey guys
i face the problem and i really what to do with it.

i even tried to virtualize Ubuntu 8.10 with my vista, it worked properly but the screen resolution was 800 * 600

i just need to work with Ubuntu with anyway.

any help ?

---

### Post by orduek on 2008-11-15
OK. After playing with it a little I managed to find a 1360X768 option but when moving to that option the screen said it is unknown signal.
It's either that it on 60Hz instead of 50Hz or that it knows only 1366X768.
Either way, I'm still stuck on 1024X768.

---

### Post by aeiah on 2008-11-15
have a look here: [http://pixelmapping.wikispaces.com](http://pixelmapping.wikispaces.com)

it'll explain pixel mapping, and perhaps list your tv. not all 720p tvs (mine included) will actually accept a 1360 or 1366 input, and you'll have to use a 720p input and have it upscaled. if you have windows still, you could try getting a custom modeline from a compatible resolution using pstrip. i found it to be pretty useful. overscanning it another problem but it can be overcome with editing to the xorg.conf although it can be a pain in the ***. i managed to get mine set up and ill post my xorg settings but yours will probably be different. you might want to consider playing with the ignoreEDID flag in xorg too.

```

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "AOC L32W451"
    DisplaySize     1600    900
    HorizSync       31.0 - 50.0
    VertRefresh     56.0 - 75.0
    ModeLine       "1240x692" 69.2 1240 1296 1424 1608 692 693 696 717 +hsync +vsync
    Option         "IgnoreEDID"
EndSection

```

---

### Post by orduek on 2008-11-15
I can't find my TV there :(

---

### Post by Tharangalion on 2008-11-15
Was my earlier post of no use?
Oh, well. It was a test of my newbieness.

---

### Post by graygeek1 on 2008-11-17
this works in mythbuntu. go to the main menu and select utilities/setup. then select setup. then tv settings. then select playback. in the second screen at the top you will see scaling. you will have to plat around with these settings to get the picture where you want it but you should be able to get it. i had to play with these settings for awhile to get mine right. hope this helps.

---

