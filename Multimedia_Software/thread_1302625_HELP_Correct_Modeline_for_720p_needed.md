---
title: "HELP: Correct Modeline for 720p needed"
date: 2009-10-27
forum: Multimedia Software
---

### Post by Master One on 2009-10-27
I have a LCD projector Epson EMP-TW680, which has a native display resolution of 1280x720 and supports 720p.

I have installed Ubuntu 9.10-RC on a computer, which is connected to that projector by VGA-cable (unfortunately this computer has neither DVI nor HDMI).

The problem is now, that the projector does not seem to report the supported resolutions to the computer, because after boot it defaults to 800x600 (without offering any higher resolution).

I already searched the net, and found the following way to feed a modeline and switch to it after login using a terminal:```
xrandr --newmode "1280x720" 74.11 1280 1392 1440 1648 720 723 725 750 +Hsync +Vsync
xrandr --addmode VGA "1280x720"
xrandr --output VGA --mode "1280x720"
```
That way it indeed switches to 720p, the picture looks just perfect, but it is not centered on the LCD panel (a little off to the left and down), and a little too wide. I can correct the position using the according menu on the projector, but that setting is not saved, and needs to be corrected every time after initalization or mode change.

The modeline was mentioned somewhere to be the correct one for 720p, but I guess it is not, means there has to be a way to set the mode in a way, that the picture is shown without the need of correcting the position afterwards, but how?

The manual of the projector does not give any useful data for this problem, on the net I found some differing 1280x720@60 modelines, but how am I supposed to find the correct one?

BTW What's the best way, to add and switch to that modeline/resolution after boot/login?

---

### Post by Master One on 2009-10-28
Yesterday evening I tried two other modelines as well:

Modeline "1280x720" 74.48 1280 1336 1472 1664 720 721 724 746 -Hsync +Vsync
Again picture looks as expected, but is shifted to the right.

Modeline "1280x720" 73.78 1280 1312 1592 1624 720 735 742 757 +Hsync +Vsync
This line gives a color distorted picture shifted to the right, so unusable.

I already read up on modelines, but I still have no clue, how to find out the proper values, so that the picture shows up centered and pixel-correct automatically.

How can I find out the proper modeline, without playing around with trial&error like forever?

---

### Post by robobot on 2009-11-03
Here is the correct modeline:
```
ModeLine "ATSC-720-60p" 74.25 1280 1320 1376 1650 720 722 728 750
```

Others can be found here:
[http://www.mythtv.org/wiki/Modeline_Database]("http://www.mythtv.org/wiki/Modeline_Database")

---

### Post by Master One on 2009-11-05
Thanks, that line kind of worked. The picture is still off to the left, which is why I had to switch off the automatic picture adjustment function of the projector, and manually center the picture. At least it's now shown pixel correct, so the picture is exactly the size of the panel resolution. I added "+Hsync +Vsync" to your line, but I was too lazy for trying all four +/- combinations. With the automatic picture adjustment function turned off at least I don't have to recenter the picture every time I turn on the projector.

---

