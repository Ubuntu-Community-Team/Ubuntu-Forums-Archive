---
title: "intel x4500 hd &lt;&gt; hdmi - hdmi &lt;&gt; Sony KLV-V32A10E"
date: 2008-12-29
forum: Multimedia Software
---

### Post by whirl on 2008-12-29
I dont quite know what to offer to you guys but Ill put something up here and trust that you throw a line here asking for more if you need it.

So I recently bought a new box and plan to use it as htpc and the main pc in the house. Ive run into a problem with hdmi - hdmi connection with my box and my lcd tv.

I have 8.10 i386 mythbuntu running on my new box which has Gigabyte GA-EG45M-DS2H LGA775 as motherboard and it comes with intel X4500 HD graphics card and Sony KLV-V32A10E.
Heres all that has anything to do with graphics in the lspci
```
lspci
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
```

Now the problem is with the hdmi output on the motherboard, because when I hook my tv to it with hdmi-hdmi cable and reboot it works well until mythbuntu starts to load. Only thing it gives me after flicking for a while is "Non supported video format" and it doesnt even show the mythbuntu loading screen. After few seconds this text disappears and the screen goes blank (black). But when I hook my lcd monitor with VGA-VGA everything  works smoothly and its all good. (Im writing this with that)

Now, I read from launchpad of different types of bugs but didnt find this one nor anything to do with text "Non supported video format." Should I try to upgrade the intel drivers and if so, to what and how?

Cheers again!

---

### Post by qrst629 on 2008-12-29
Adidas 35th at Finish Line just won't quit - ever. Constructed for athletes who continue to pound the pavement day after day,Adidas 35th are comfortable, stylish and built to last, which is what you have come to expect from Adidas 35th. Grab a pair of Adidas 35th and never look back.brandshoeswholesale.com carries a wide range of Adidas 35th Shoes, below is some more information and in depth links to our shoes catalog and products. [Adidas 35th Shoes](http://www.brandshoeswholesale.com/wholesale_Adidas_35th_cid_484.htm)

---

### Post by whirl on 2008-12-30
It must be something to do with my xorg.conf cause this just doesnt look right.

```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

Where to start? Ill try to do my own googling and testing but if you know what I should do please reply to this.

Cheers!

---

### Post by whirl on 2008-12-30
alright I tried to do changes to xorg.conf but didtn work. I think I got it "right" but then again Im quite new to this **** so probably messed something up. I edited xorg by adding stuff there from here [http://www.mythtv.org/wiki/index.php/Modeline_Database#Sony_Bravia_KLV-S32A10E_.28KLV-S40A10E.2C_KLV-S32A10E.2C_KLV-S26A10E.2C_KLV-S23A10E.2C_KLV-S19A10E.29]("http://www.mythtv.org/wiki/index.php/Modeline_Database#Sony_Bravia_KLV-S32A10E_.28KLV-S40A10E.2C_KLV-S32A10E.2C_KLV-S26A10E.2C_KLV-S23A10E.2C_KLV-S19A10E.29") but that didnt work so I went back to that old very short xorg.conf and it got my wondering why is it that short? But then again everything else seems to work nicely so I dont think it up to xorg.conf but more with the driver.

So I started to seek info on drivers and stumbled on this:
[http://lists.freedesktop.org/archives/xorg/2008-December/041553.html]("http://lists.freedesktop.org/archives/xorg/2008-December/041553.html")

It says about sound not working with the older driver but is the video suppose to work through hdmi? Any ideas on this one? Should I first try to get this older driver show me something or just upgrade 2.5.99.1 and hope it fixes everything. (keep in mind Ive never done that before)
EDIT: yeah I typed "man intel" to terminal and the closest supported hardware is G33 and so yeah Ill try to upgrade to that 2.6 rlc.

---

### Post by NT4usB on 2009-01-12
No answers here but fwiw, I feel your pain. I spent the weekend googling for the solution to make HDMI X4500 Intel graphics work with little success. GA-EG41M-S2H board.
I did get the analog side to work using newer Intel drivers from the Intrepid development repos.
Still haven't solved the no supported formats on the HDMI side.

---

### Post by guizzocasa on 2009-03-03
hey, I'm from italy and I have the same problem. My configuration is:

SAMSUNG LCD 40656 FULL HD.
UBUNTU 8.10 INT. IBEX ON A SMALL PC ([www.abacomputers.com](www.abacomputers.com)) HD MEDIASTATION
WITH INTEL 4500HD GRAPHICS CARD.

Everything works great with vga/vga but with hdmi cable don't work...
Have you found something to solve the problem....
I trust in you for a solution !!! i'm googling for 2 weeks but I haven't found nothing.
I think the problem is due to a bad configuration in xorg.conf

Sorry for my bad english 
:-(

---

### Post by NT4usB on 2009-03-03
I gave up and bought a nvidia card.
I did find one post that said Intel X4500 via DVI is not supported (yet) so we may be kicking a dead horse.

---

### Post by whirl on 2009-10-12
update on my situation.

I just installed 9.10 and Im happy to say that I get a picture! But the thing is that its 720x480 and I believe Im supposed to get 1280x720. I cannot change this in the system->Preferences->Display cause it only gives me the 720x480 option.

So, how do I force it to choose 1280x720? Whats all this talk about xorg.conf not even existing and what does this mean in my case?

Cheers again!

---

### Post by whirl on 2009-10-13
I tried to add modes with xrandr and then choosing them from the gui but after hitting apply the screen turned to black (while TV informed that it was running 720p).

Heres few I tried:

I got this from elsewhere as it was suppose to be the correct modeline for my TV.
```
"1280x720" 60.466 1280 1328 1456 1632 720 721 724 741 +hsync +vsync
```
and then the once that cvt proposed for me
```
cvt 1280 720 60
# 1280x720 59.86 Hz (CVT 0.92M9) hsync: 44.77 kHz; pclk: 74.50 MHz
Modeline "1280x720_60.00"   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync
```
```
cvt 1280 720 50
# 1280x720 49.83 Hz (CVT 0.92M9) hsync: 37.07 kHz; pclk: 60.50 MHz
Modeline "1280x720_50.00"   60.50  1280 1328 1456 1632  720 723 728 744 -hsync +vsync
```
```
cvt 1280 720 40
# 1280x720 39.91 Hz (CVT) hsync: 29.53 kHz; pclk: 47.25 MHz
Modeline "1280x720_40.00"   47.25  1280 1320 1440 1600  720 723 728 740 -hsync +vsync
```

To make it clear I used em like this:
```
xrandr --newmode "1280x720_60.00" 74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync
```
and after this named it as 1280x720_60.00 (maybe because it allows me to choose it from the graphical display resolution, a bit clueless here ;)
```
xrandr --addmode DVI1 1280x720_60.00
```

So all these didnt work? What next or should I just buy a new TV?

Cheers!

---

