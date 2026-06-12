---
title: "Blurry projector image with Intel GMA"
date: 2010-10-11
forum: Multimedia Software
---

### Post by nalgarryn on 2010-10-11
[FONT="Palatino Linotype"]Hi guys!

I'm pretty new to Ubuntu and Linux so I'm going to be pretty useless without explicit instructions. I could really use some help getting this projector to work with my notebook. Here are the details:

[LIST]
[*]Acer Aspire 5315-2681 notebook
[*]Intel GMA 965 adapter
[*]Ubuntu 10.04.1 (Lucid)
[*]Not sure what resolution the desktop is, but should be 1280x800
[*]Fn+F5 does nothing (2nd display notebook hotkey)
[/LIST]
AND
[LIST]
[*]some sort of SHARP projector
[*]Projector resolution should be 800x600
[/LIST]

This is the info from lspic:
VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)

(There is a sticker on the computer that says Mobile Intel GMA X3100, however.)

When I booted up the computer with the projector attached my bootloader appeared on the wall but not on the LCD. When I logged in my desktop appeared properly on my computer and is duplicated on the wall. However the wall image is very blurry. Part of the lower image is cut off and the right side is too short and there is a green band on the right edge a half dozen pixels wide.

When I booted (dual boot) into windows XP I got the same thing. Then I installed the proper drivers for the graphics adapter (they had not been installed because I hadn't used XP for anything but updating the BIOS) and the image lined up neatly and fit properly, and I could set the display to extend my desktop (instead of duplicate) it on the projector image. (This is what I would like to do under Ubuntu).

I'm concerned that my VGA controller doesn't have the right drivers or is set up incorrectly, but since I'm new to Linux I have no idea how to fix it.

Thanks in advance! [/FONT]

---

### Post by SnickerSnack on 2011-01-02
First I'd recommend that you upgrade to 10.10.  Then, I'd recommend that you install the mesa drivers.  Run the following command in the terminal:

```
sudo apt-get install libgl1-mesa libgl1-mesa-glx libgl1-mesa-dri
```

You can install these through Synaptic if you prefer.

Now, you're probably going to have to get your hands dirty and learn how to use xrandr.  It's not hard.

Look at the output of

```
xrandr --prop
```

to get a bunch of info on your displays.  There should be one or more lines with the word "connected" in them.  There are the names of your displays.  Here is what my output looks like:

```
zsharon@Weierstrass:~$ xrandr --prop
Screen 0: minimum 320 x 200, current 2304 x 1024, maximum 8192 x 8192
VGA1 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 340mm x 270mm
	EDID:
		00ffffffffffff00368b0f039a1f0000
		1a0c010168221b78e80f759c574c9126
		234f54afef008180818a818f6140614f
		454a454f3140000000fa00c940a94001
		010101010101010a000000fd00374c1e
		510e000a202020202020000000ff0041
		32353543313135363333340a000000fc
		004d544b20433738330a000000000022
   1280x1024      75.0*    60.0  
   1024x768       75.1     75.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     60.0     59.9  
   720x400        70.1  
LVDS1 connected 1024x768+1280+0 (normal left inverted right x axis y axis) 245mm x 184mm
	EDID:
		00ffffffffffff0030ae024000000000
		0011010380191278ea87f594574f8c27
		27505421080001010101010101010101
		01010101010164190040410026301888
		3600f5b8000000180000001000000000
		000000000000000000000000000f0061
		433c0000001302004ca35850000000fe
		004c544e3132315850303130303100a3
	BACKLIGHT: 15 (0x0000000f)	range:  (0,15)
	Backlight: 15 (0x0000000f)	range:  (0,15)
	scaling mode:	Full aspect
		supported: None         Full         Center       Full aspect 
   1024x768       60.0*+
   800x600        60.3     56.2  
   640x480        59.9 
```

So, LVDS1 is my laptop screen and VGA1 is my external monitor.  I have my external monitor sitting to the left of my laptop, so I use

```
xrandr --output VGA1 --left-of LVDS1 --mode 1280x1024
```

to extend my desktop across the two.  To clone them, I use

```
xrandr --output VGA1 --mode 1024x768 --same-as LVDS1
```

and to turn off the external connection, I use

```
xrandr --output VGA1 --off
```

You don't have to type these in every time.  I use xfce4 as my desktop environment, and I created some buttons on the panel to perform these functions.

---

