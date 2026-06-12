---
title: "Hardy Low Resolution"
date: 2008-04-27
forum: Multimedia Software
---

### Post by waterbucket17 on 2008-04-27
Hi,

After installing Hardy I just can't seem to get my resolution up there. Without installing any video drivers, xrandr says my maximum resolution is 800x600 and when I install the nvidia drivers, the max resolution drops down to 640x480!

Nothing I change in xorg.conf seems to have any effect. Where is xrandr getting these resolutions from? Is there something I'm missing or is it just a problem with the nvidia drivers?

From lspci:
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

-Waterb17

---

### Post by edaw on 2008-04-27
Ditto, Can't get higher than 800x600. Changed the xorg.conf and added a few modes and a virtual size, the virtual worked, still annoying though.
The default xorg looks very well, default, is this the easy auto configuration addition spoken of in the realease notes?

Running xubuntu before changing main pc over to ubuntu.

---

### Post by mike3244 on 2008-04-27
Same problem here. I had no issues whilst running the Beta. I did a clean install and now can only get 1024 x 768.

My card is a GeForce4 MX 420

Also I have only the standard 3 options on visual effects - no Compiz

---

### Post by Aldanga on 2008-04-27
I can verify this. I'm having the same issues. I'm running an 8800GT via DVI. I've tried running sudo dpkg-reconfigure xserver-xorg, but it never gives me options beyond my keyboard layout.

---

### Post by illuminate on 2008-04-27
yep. Im having the same problem as the OP.  i got have 7600GT XXX from xfx though... i even did a fresh install, and still nothing...

---

### Post by mgmiller on 2008-04-27
1) Right click Applications and select "Edit Menus"
2) Scroll to and select, by left clicking, the "Other" location on the left side.
3) On the right side put a check mark in the box next to "Screens and Graphics", then click "Close".
4) Go to Applications > Other > Screens and Graphics
5) On the screen tab, click the drop down next to model.
6) If you can find your model, great, if not, select generic LCD (assuming it's an LCD)
If it is a wide screen monitor, don't forget to check the wide screen box.
7) Now you can find & select your resolution and refresh rate from the list on the right side. Click OK.
8 ) Go to the Graphics Card tab.
9) Click on Driver and select what you need.
10) Click the test button to make sure all is ok.
11) Click ok and you're done.

---

### Post by Geezle on 2008-04-27
I'm having the same problems as well, but after I select my Nvidia driver and log out I get a "Signal Out Of Range" error from my monitor and I have to boot into recovery mode to get it straightened out.  Any thougts?

---

### Post by hariprs on 2008-04-27
> **Geezle said:**
> I'm having the same problems as well, but after I select my Nvidia driver and log out I get a "Signal Out Of Range" error from my monitor and I have to boot into recovery mode to get it straightened out.  Any thougts?

Easy to fix, here's how:

Boot normally, when you get to a login screen don't login, instead press ctrl+alt+F2 to get to a console, login then enter the following:

```
sudo nano /etc/usplash.conf
```

if nano is not installed then:

```
sudo apt-get install nano
```

edit the file to match YOUR resolution. Here's an example:

I want a resolution of 1680x1050:

```
# Usplash configuration file
xres=1680
yres=1050
```

save the file, crtl-o, then exit, crtl-x, then enter:

```
sudo dpkg-reconfigure usplash
```

this will create a new initrd.img file with the correct resolution for your monitor, then

```
sudo reboot
```

---

### Post by waterbucket17 on 2008-04-29
After trying three fresh installs of Hardy and two different video cards, I decided to reinstall 7.10 for the time being. And again I couldn't get a high resolution, until I added the horizontal sync and vertical refresh values to the monitor section in my xorg.conf.

I think I tried this in Hardy, but I don't remember for certain. Does this fix the problem in Hardy for anyone?

```

Section "Monitor"
	Identifier	"Monitor"
        Option          "DPMS" "true"
[COLOR="SeaGreen"][B]	Horizsync	31-81
	Vertrefresh	56-75[/B][/COLOR]
EndSection

Section "Screen"
	Identifier	"Screen"
	Device		"VideoCard"
	Monitor		"Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```

---

### Post by jwkolberg on 2008-05-08
> **mgmiller said:**
> 1) Right click Applications and select "Edit Menus"
2) Scroll to and select, by left clicking, the "Other" location on the left side.
3) On the right side put a check mark in the box next to "Screens and Graphics", then click "Close".
4) Go to Applications > Other > Screens and Graphics
5) On the screen tab, click the drop down next to model.
6) If you can find your model, great, if not, select generic LCD (assuming it's an LCD)
If it is a wide screen monitor, don't forget to check the wide screen box.
7) Now you can find & select your resolution and refresh rate from the list on the right side. Click OK.
8 ) Go to the Graphics Card tab.
9) Click on Driver and select what you need.
10) Click the test button to make sure all is ok.
11) Click ok and you're done.
I was having the same problem and this worked perfectly for me, thanks!

the only way I can get s-video to work is with nvidia x-server setting appliction and enabling cloned to lcd and tv, but switches to one or the other not both...

---

### Post by maramot on 2008-05-09
Check your menu.lst file. In case you've been upgrading from 7.10 it may have been left with the old kernel loading. You need to be loading kernel version 2.6.24.16-generic with ubuntu 8.04 otherwise it will keep you stuck in 800x600 and it will start in low graphics mode every time you reboot. That's what happened to me and here's how I fixed it: [http://ubuntu-utah.ubuntuforums.org/showpost.php?p=4922126&postcount=19](http://ubuntu-utah.ubuntuforums.org/showpost.php?p=4922126&postcount=19)

---

### Post by janunezc on 2008-05-10
> **waterbucket17 said:**
> After trying three fresh installs of Hardy and two different video cards, I decided to reinstall 7.10 for the time being. And again I couldn't get a high resolution, until I added the horizontal sync and vertical refresh values to the monitor section in my xorg.conf.

I think I tried this in Hardy, but I don't remember for certain. Does this fix the problem in Hardy for anyone?

```

Section "Monitor"
	Identifier	"Monitor"
        Option          "DPMS" "true"
[COLOR="SeaGreen"][B]	Horizsync	31-81
	Vertrefresh	56-75[/B][/COLOR]
EndSection

Section "Screen"
	Identifier	"Screen"
	Device		"VideoCard"
	Monitor		"Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```

Thanks! WaterBucket17!!! This worked perfect for my VNC + No Monitor configuration.

---

