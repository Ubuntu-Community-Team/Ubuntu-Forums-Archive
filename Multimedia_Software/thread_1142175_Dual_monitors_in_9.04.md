---
title: "Dual monitors in 9.04"
date: 2009-04-28
forum: Multimedia Software
---

### Post by tubaking182 on 2009-04-28
to get started usually i can find my answers to this stuff in a few quick google searches, but jaunty is pretty new and i can't seem to find the answer to what i am looking for. i recently upgraded to jaunty and have been away from my second monitor and so i didn't know until about an hour ago that my dual monitor setup was broken after upgrade. in 8.10 i know i had to edit the xorg.conf and play with the settings in screen resolution but i got it up and going in a few minutes. now there is now "screen resolution" it is called display and it doesn't seem to be working. i unchecked the mirror screens box and moved the monitors around to correctly display the desktop(in theory) and i hit apply.

after that my second monitor when from black(no input) to black(with input) i can move my mouse over to the other screen but no programs. i really need to have the other screen up and running because i like to havev my virtual box for school running XP on the other monitor. my xorg.conf is still set up the way it is supposed to (virtual screensize 2048x768) but still nothing on the other screen. so i tried logging out and back in but that didn't help either.

logging out and back in just caused EVERYTHING to be stretched out really bad visually but certain things weren't clickable until i found their original spot which is now under other things. please help me out, i know i don't post much but i know what i am doing because this site is great and i really don't need to post in order to get the answers i need.

thanks in advance
-king

---

### Post by Almighty on 2009-04-28
Are you using an nvidia or ati graphics card?

---

### Post by tubaking182 on 2009-04-29
gonna go with ati since i know for sure it isn't nvidia, it's a gateway m320x notebook that was gonna get thrown away at work so i nabbed it.

here is my xorg.conf if it will help

```

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2048 768
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

```

---

### Post by mªrty on 2009-04-30
run ```
lspci
``` in terminal to find your display adapter.

I was under the impression that in 9.04 they had fixed dual-display so you wouldn't need to manually edit xorg.conf. can anyone confirm?

---

### Post by markbuntu on 2009-04-30
It depends.
I am using Jaunty with a ati HD3650 and open source drivers and can configure my 2 monitors just fine with the "display" gui in preferences in gnome but in KDE4.2 there is no way to do this at all. The system settings section for doing this is just not there. I have read that you need to use Display to do this with the ati proprietary driver also.

I know there are some issues with intel and I have no idea what is going on with nvidia.

---

### Post by mushinspace on 2009-05-07
I just attempted a brand new install of 9.04, and after unchecking the "mirror display" box, I get a wider desktop.  It did offer to update the virtual desktop with the proper size, and xorg.conf seems to show it:

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        SubSection "Display"
                Virtual 3360 1065
        EndSubSection
EndSection

However, when I try to drag a window to the other screen, it only moves it part way (about 33%) before it halts.  The mouse moves all the way to the far edge, but left-click+drag doesn't even draw the bounding box (anywhere on the right screen).

The dual-dvi display card is:

01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)

Each screen is a 20" widescreen, so 1680x1050 is appropriate ... the virtual screen shows slightly taller, but I don't see how that should affect the functional width.

I already did a system update, but perhaps there are other drivers for this nVidia?

Thanks,
Sam

---

### Post by bobince on 2009-05-07
> **tubaking182 said:**
> i unchecked the mirror screens box and moved the monitors around to correctly display the desktop(in theory) and i hit apply.

after that my second monitor when from black(no input) to black(with input) i can move my mouse over to the other screen but no programs.

Yeah, I had something like that. I don't think Xrandr quite reconfigures the monitors right on all adapters when it is bumped out of mirror-displays mode.

What's reliable for me is to untick the &#8216;mirror&#8217; option (causing it to write an xorg.conf) and then immediately log out and back in again (causing the X server to restart). At that point repositioning the screens relative to each other works fine. (Better than in Intrepid, which had a habit of kicking the main panel back to the secondary display all the time.)

If you get in a hole where your monitors are configured in an unusable way, hit ctrl-alt-F1 for console, log in and &#8216;sudo rm /etc/X11/xorg.conf&#8217;. This will return the configuration to the safer &#8216;mirror&#8217; mode.

---

### Post by addtoqueue on 2009-05-07
> **mªrty said:**
> run ```
lspci
``` in terminal to find your display adapter.

I was under the impression that in 9.04 they had fixed dual-display so you wouldn't need to manually edit xorg.conf. can anyone confirm?

It appears that they didn't. I'm still having trouble with dual monitors in 9.04 and posted it here:

[http://ubuntuforums.org/showthread.php?p=7222652](http://ubuntuforums.org/showthread.php?p=7222652)

---

### Post by kerry49 on 2009-08-08
I solved this problem after numerous hours of googling by changing the virtual settings in xorg.conf.

I have a desktop monitor with a 1024x768 setting and a Visio 26" TV/monitor at 1360x768 on an ATI Radeon RV100 QY [Radeon 7000/VE]. I could not get these to set up no matter what I tried.

I finally added the resolution of the two screens (1024+1360=2384 [+10%]= 2648x1536 (768x2) and they both now work like a charm. I initially tried it without the 10% add-on and it didn't work so make sure and throw that in.

---

### Post by wEeTeEz on 2009-10-27
hi, im some what new to Ubuntu. i just got done downloading 9.04, and i was using windows XP i have a Nvidia Geforce 8800 GT graphics card. and now my TV monitor is no longer working. im having difficulties with setting up the Seperate X screen Configuration. because when i hit Apply after i changed it to Seperate X screen from my TV being disabled it says "Cannot Apply". if any 1 could help me that would be great.

---

