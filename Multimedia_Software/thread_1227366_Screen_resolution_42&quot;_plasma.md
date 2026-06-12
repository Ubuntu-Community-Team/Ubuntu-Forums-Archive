---
title: "Screen resolution 42&quot; plasma?"
date: 2009-07-30
forum: Multimedia Software
---

### Post by johan_tre on 2009-07-30
Hi everyone, 

I have the following problem; it looks simple, but I cannot get this to work.

As most of you know, displaying an image via HDMI connection is problematic whit GeForce boards. 
This is due to a overscan problem, whereas the signal sent over hdmi, is larger then the display can show.  
Result: missing upper/lower/left/right borders of the screen, so no linux taskbar etc.    
Solution: take a smaller resolution. 

I solved the problem partly with xrandr. 
What I use now, is the resolution 1600x1024, and I do set this via xrandr in the startup script. 

Unfortunately, this resolution is not correctly the 19:6 aspect ratio :(
Left and right, I still have a black border. Vertically the screen is nicely filled top to bottom.
According the 19:6 aspect ratio I should have 1820x1024 resolution to fill the screen.

My remaining problem:
How do I add a custom resolution??
I followed may guidelines with xrandr; and they go as follows:
(changing xorg.conf does not really help with the nvidia drivers and or jaunty)

see all modes for your running system with the screens connected: 
```
xrandr
```get the modeline for this resolution:
```
gtf 1820 1024 60
```to persist the new resolution:
```
xrandr --newmode <modename> <modeline from gtf feedback>
xrandr --addmode default "<modename given above>"
```to change to this resolution
```
xrandr --output default --mode "<modename given above>"

or 

xrandr -s <modename given above>
```This adds a new resolution in the xrandr list.

But when I switch to it I get an error saying this resolution cannot be set.

Can anyone help me please???
I'm quite a long time now on this painful problem!

System:
Ubuntu Jaunty 9.04
Plasma screen 42inch


Thanks in advance!

Johan

---

### Post by johan_tre on 2009-08-01
No one?  Plz...   this problem is becoming a pain in the neck!

---

### Post by xc3RnbFO8P on 2009-08-01
> 19:6 aspect ratio
Its 16:9

Is your TV Full HD?

> According the 19:6 aspect ratio I should have 1820x1024 resolution to fill the screen
16:9 = 1920x1080

In Terminal run:
> sudo nvidia-settings
and change the resolution there.

---

### Post by johan_tre on 2009-08-02
Hi thanks for the quick reply. 

Oops typo there :)
Indeed it's a full HD, ratio=16:9.

Changing the resolution in nvidia-settings requires that: 
1) a proper resolution is found.  
    (somethingx1024 in the proper ratio, since GeForce cards display their image overscanned which is to big for the screen) 
2) the resolution stays persistent. 
when you set the resolution with "sudo nvidia-settings", rebooting resets it to native resolution, which is 1920x1080.
Setting in the xorg.conf does not help...

So I found on quite some places on the net the xrandr solution.
This helps with effect!
Fact is, the horizontal pixel count is not correct yet. 
Currently it runs 1600x1024 (to small horizontally)

So the final question:    how to I add a new custom resolution? 
Custom resolutions are being ignored in xrandr and xorg.conf it seems....

Please help.... this looks like an easy one, though I cannot find any fix.

---

### Post by xc3RnbFO8P on 2009-08-02
You can try this(or google it, to know how to use it):
> Option         "ModeValidation" "NoDFPNativeResolutionCheck"

> Option "ModeValidation" "NoXServerModes"
in xorg.conf

---

### Post by johan_tre on 2009-08-02
Hi Ringi, 

I'll do that tomorrow evening and send some feedback. 

Is it a solution to allow funky resolutions? 
or is it a solution to allow nvidia-settings to be persistent?

Thx for the info, it is much appreciated!

---

### Post by tgalati4 on 2009-08-02
You didn't specify the make and model of your plasma TV.  Most can only display 1600x 1024 anyway.  It has to do with the scaler inside the TV.  More expensive TV's have better scalers to support higher resolutions, but most TV's have limited PC resolution.

What do the specifications say the supported PC resolution is?

Also, most scalers only handle 4:3 resolution so you can either get letterbox (black bars) or stretching to fill the screen.

---

### Post by johan_tre on 2009-08-02
Here are the specs.
Hope you can make something out of it.   Its a full HD though. 1920x1080.

[http://www.panasonic.be/html/nl_BE/Producten/Flatscreens+VIERA/Plasma+schermen/TX-P42V10/Specificaties/2407769/index.html?trackInfo=true](http://www.panasonic.be/html/nl_BE/Producten/Flatscreens+VIERA/Plasma+schermen/TX-P42V10/Specificaties/2407769/index.html?trackInfo=true)

Regards,    Johan

---

### Post by tgalati4 on 2009-08-03
It does look curious:
	VGA, WVGA, SVGA, XGA, WXGA, SXGA 60Hz, 1920 x 1080
One gets the impression that it can drive 1920 x 1080, but the 60Hz refresh is limited to:

VGA, WVGA, SVGA, XGA, WXGA, SXGA

I don't remember what those resolutions are, but I bet they are crappy.

wikipedia to the rescue:

[http://en.wikipedia.org/wiki/SXGA](http://en.wikipedia.org/wiki/SXGA)

Looks like 1280x1024 at 60 Hz is your best PC resolution.  This is typical in these TV's.

This is a 5:4 ratio, so you will have to play with stretch or letterbars.

Samsung has some high-resolution monitors at also display HD TV.  Decent monitors, but crappy TV's. It's hard to engineer a display with both high-quality PC display resolution and high-quality HD motion display.

Let me know if you find one.

---

### Post by LowSky on 2009-08-03
If your TV is 1080p you should run 1920 x 1080

if its 1080i or 720p your better running at a 1366 x 768

also use the d-sub input, its made for monitor selection, HDMI isn't the best choice for pc use, ok I shouldnt say that, but d-sub (VGA) it is known to actually work and not cause issues

---

### Post by johan_tre on 2009-08-05
The solution 
> 
 	Quote:
 	 	 		 			 				Option         "ModeValidation" "NoDFPNativeResolutionCheck" 			 		 	 	 
 	Quote:
 	 	 		 			 				Option "ModeValidation" "NoXServerModes" 			 		 	 	 
in xorg.conf 	

is not working.   
I do have the impression that I see more resolutions in the list in xrandr, as well as in nvidia-settings though. 

The pain is that I cannot create an extra resolution myself.   (e.g. 1820 x 1024)

Isn't there no way then to create my own custom exotic resolution in Linux at all?

---

### Post by tgalati4 on 2009-08-07
You can create any resolution you want, however the hardware may be limited to drive that resolution.  If you look in /var/log/Xorg.0.log you will see discarded resolutions because of hardware limitations.

I bet the display mode 1280 by 1024 works.

---

### Post by johan_tre on 2009-08-08
yep... 1280 by 1024 (and so many others) are working, but are not reasenable fit for the plasma. 

But that is not the resolution I want.
I only want a full screen...   that can't be to hard I guess??
I want 1820 by 1024 to work!!  (1024 is already exact) only the horizontal resolution is still not correct.

And also, how do I make this happen?    nvidia-settings doesn't seem to care much about it...

Trying gtf on 1820 by 1024 returns 182**4** by 1024 for some mistery reason. 
Anyway, that resolution is not possible to set with xrandr either :)

---

### Post by cebo0650 on 2009-08-23
I have exactly the same problem on my 50" Panasonic Plasma.

Would love to find the solution.

---

### Post by johan_tre on 2009-08-24
The solution to this, (as far as I got, still no improvement) is defined in the first post.
 Use "xrander" to do your fix. 

Everyone in the linux world says you can change resolution to any exotic custom mode you like. 
I only see the opposite of that.   

The screen limits the possibilities, and there seems no way to ignore these pre-screen-defined resolutions. 
So if the screen makes a mistake (like in a plasme case) you are bugged big time.

---

### Post by JMorsing on 2009-08-24
The solution that worked for me was simply to turn of the overscan feature on the tv. That can be done in settings. I have a PX80 conneted with HDMI. Hope it works for you to. 
 
Jesper

---

