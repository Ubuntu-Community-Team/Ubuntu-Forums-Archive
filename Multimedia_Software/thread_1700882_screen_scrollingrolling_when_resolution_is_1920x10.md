---
title: "screen scrolling/rolling when resolution is 1920x1080"
date: 2011-03-05
forum: Multimedia Software
---

### Post by Noldoaran on 2011-03-05
I recently bought a 37" Vizio M370NV HDTV and connected it to my Kubuntu 10.10 desktop. Currently my resolution is 1280x1024, so there is black bars on the side of my screen. I want my resolution to be 1920x1080, which is what the TV/monitor says is it's primary resolution. However, when I set that resolution in nvidia-settings, my screen scrolls up. By that I mean that my screen keeps moving up my monitor and appearing at the bottom. 
I know it is some kind of vertical syncing problem, but I don't know how to fix it.

---

### Post by Yellow Pasque on 2011-03-06
Can you set the 1920x1280 resolution and then restart the Xserver (i.e. log out and in). Then, post your /var/log/Xorg.0.log as an attachment or use [ code ][ /code ] tags.

---

### Post by Noldoaran on 2011-03-07
Here is the log file.

---

### Post by 1clue on 2011-03-07
Try this:

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.old

Then reboot.

Without the nvidia driver, it should just work out of the box.  Then you can go to nvidia-settings again and it should rewrite a file just like the first time you did it.

---

### Post by Noldoaran on 2011-03-07
I ran 'sudo mv /etc/X11/xorg.conf /etc/X11/xorg.old' then restarted the X server. nvidia-settings told me that the nvidia drivers weren't running and said I should run 'nvidia-xconfig' as root, which I did. Then, I restarted the xserver, and got the right resolution, but my screen was scrolling like last time. I restored my xorg.conf and I'm back to my old resolution (1280x1024).

---

### Post by 1clue on 2011-03-07
So you have a virtual screen that's bigger than the physical one?

That's really odd.  I'm using nvidia with dual monitors, I just install the OS and it works with mirrored displays automatically, no scrolling.  I then install the nvidia-drivers and that works too, and then I set it up with two separates and it just works.

Do you WANT scrolling and it won't?  The way I read your posts, you HAVE scrolling and DON'T want it.  I can't stand scrolling (which is why dual 1920x1080 monitors) so I've never tried to put it in.

---

### Post by BicyclerBoy on 2011-03-07
Many/most HDTVs will not allow native resolution over VGA.
The VGA connection is normally limited to 60Hz only
Do you have any real specs for the display inputs ?

Is your scrolling/rolling like the old analogue TV with no sync ?

Your Xorg.0.log does not show any EDID video modes from the display. I'm not sure why..
Maybe your TV does not provide any EDID data but that would normally generate an error message.

The reviews of these TV:
 > 
The VGA port for computer display supports 1024 x 768, 1920 x 1080, 640 x 480 (VGA) and 800 x 600 (SVGA) resolutions.

This TV is also compatible with 480i, 480p, 720p and 1080i video signals (HDMI
So it does seem to support 1080i over VGA...
Maybe not with reduced vertical blanking timings ?
Maybe the review information is just wrong..

From the TV manual
> Resolution through RGB Input
If your PC supports VESA Reduce Blanking timing via the VGA card drive program (usually offered by the VGA Card Manufacturer), your TV set is equipped to have the 1920x1080 resolution display through this connection using the following timing 138.5MHz. The following parameters are often the values required by the software or programs to set up the display:

Nvidia driver uses CVT-RB for DFP over DVI & HDMI..
It probably uses GTF timing for CRTs.
You may need a custom modeline to force the CVT-RB timings..
I'll try to calculate one for you...

---

### Post by 1clue on 2011-03-07
Wait.

Tell me you're using DVI or HDMI.  If you're not, then find some way to use modern connectors at every stage of the signal.

---

### Post by BicyclerBoy on 2011-03-08
CVT-RB modeline that exactly matches your TV requirements

# 1920x1080 59.93 Hz (CVT 2.07M9-R) hsync: 66.59 kHz; pclk: 138.50 MHz
Modeline "1920x1080R"  138.50  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync

Just figure out how to stick this into your /etc/X11/xorg.conf

---

### Post by Noldoaran on 2011-03-08
> **BicyclerBoy said:**
> 
Is your scrolling/rolling like the old analogue TV with no sync ?

Exactly! That's a good way to describe it!



> **1clue said:**
> 
Tell me you're using DVI or HDMI.  If you're not, then find some way to use modern connectors at every stage of the signal.
No, I am using VGA. The TV doesn't have DVI input, so I'd have to get a DVI->HDMI converter. I might try that if nothing else works, but I don't want to spend the money if it will just give me the same problem.

> **BicyclerBoy said:**
> CVT-RB modeline that exactly matches your TV requirements

# 1920x1080 59.93 Hz (CVT 2.07M9-R) hsync: 66.59 kHz; pclk: 138.50 MHz
Modeline "1920x1080R"  138.50  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync

Just figure out how to stick this into your /etc/X11/xorg.conf
Thanks! I'll try this when I get home and report back.

---

### Post by BicyclerBoy on 2011-03-08
A DVI to HDMI adapter is just a passive cable:

single link DVI-D to HDMI  could be $5..
The 19 pin HDMI is electrically equivalent of single link DVI-D.

That should work fine with any DVI-I output.
Most video cards have at least one DVI-I & one DVI-D. 

Comes free with some PC monitors & this cable would be a simple/better solution.

---

### Post by 1clue on 2011-03-08
A VGA connector you can only get an analog video signal.  Get your entire signal path to be digital, your picture will be clearer.

I also don't think analog really wants to go to that sort of resolution.  The higher the resolution the better the card needs to be especially for analog.

---

### Post by Noldoaran on 2011-03-12
I added this to my xorg.conf file, but still get the scrolling. I'll order and DVI -> HDMI cable from amazon and see if that helps me.

> **BicyclerBoy said:**
> CVT-RB modeline that exactly matches your TV requirements

# 1920x1080 59.93 Hz (CVT 2.07M9-R) hsync: 66.59 kHz; pclk: 138.50 MHz
Modeline "1920x1080R"  138.50  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync

Just figure out how to stick this into your /etc/X11/xorg.conf

---

### Post by BicyclerBoy on 2011-03-12
Post your 
/var/log/Xorg.0.log
file as an attachment with .txt extension (cos this is a windows site) just to see what is now wrong ..

You may need this as well to stop the existing EDID info from in-validating your new modeline..

Section Screen
    Option         "UseEDID" "FALSE"

Did you put the modeline into your monitor section or a Modes section ?

---

### Post by Noldoaran on 2011-03-20
I put the modeline in the monitor section. Adding 'Option "UseEDID" "FALSE"' didn't work for me either. I'm attaching the logs ([ATTACH]186684[/ATTACH]) and the xorg.conf ([ATTACH]186685[/ATTACH]).

---

### Post by BicyclerBoy on 2011-03-20
Your Xorg.0.log reveals..

nvidia driver ignored the display EDID & it validated & set your 1920x1080R mode..all good..

If the TV is still unhappy it suggests to me the TV specs are incorrect..

Can you run the nvidia-settings GUI program ?
Does it report the correct mode in being used ?

---

### Post by Noldoaran on 2011-03-31
I got an DVI->HDMI converter and it works like a charm!!

---

