---
title: "24&quot; Apple LED cinema, Z68 Pro3-M, iGPU, 11.04"
date: 2011-07-20
forum: Multimedia Software
---

### Post by asrock-z68 on 2011-07-20
I can't seem to get my system to recognize my 24" Apple LED Cinema Display (DisplayPort) with a ASRock Z68 Pro3-M motherboard (i7 2600k, 1.40 firmware) using the iGPU/DisplayPort running Ubuntu 11.04 2.6.38-10-generic with latest updates. The system boots and runs (can ssh into it) but there is no display. The same system running Windows 7 x64 works fine. A DVI monitor also works fine. Xserver-intel driver sees the display but can't set any modes for it. 

Log files [_dmesg_]("http://www.santacruzoptics.com/tmp/ubuntu/dmesg.txt") [_lshw_]("http://www.santacruzoptics.com/tmp/ubuntu/lshw.txt") [_Xorg.0.log_]("http://www.santacruzoptics.com/tmp/ubuntu/Xorg.0.log.txt")

Anyone have any idea what's going on here?

Here is an excerpt from Xorg.0.log:

[    14.167] (II) intel(0): EDID for output DP2
[    14.167] (II) intel(0): Manufacturer: APP  Model: 9236  Serial#: 34318216
[    14.167] (II) intel(0): Year: 2009  Week: 28
[    14.167] (II) intel(0): EDID Version: 1.4
[    14.167] (II) intel(0): Digital Display Input
[    14.167] (II) intel(0): 8 bits per channel
[    14.167] (II) intel(0): Digital interface is DisplayPort
[    14.167] (II) intel(0): Max Image Size [cm]: horiz.: 52  vert.: 32
[    14.167] (II) intel(0): Gamma: 2.20
[    14.167] (II) intel(0): DPMS capabilities: Off
[    14.167] (II) intel(0): Supported color encodings: RGB 4:4:4 
[    14.167] (II) intel(0): Default color space is primary color space
[    14.167] (II) intel(0): First detailed timing is preferred mode
[    14.167] (II) intel(0): Preferred mode is native pixel format and refresh rate
[    14.167] (II) intel(0): redX: 0.653 redY: 0.334   greenX: 0.300 greenY: 0.615
[    14.167] (II) intel(0): blueX: 0.146 blueY: 0.057   whiteX: 0.312 whiteY: 0.329
[    14.167] (II) intel(0): Manufacturer's mask: 0
[    14.167] (II) intel(0): Supported standard timings:
[    14.167] (II) intel(0): #0: hsize: 1920  vsize 1200  refresh: 60  vid: 209
[    14.167] (II) intel(0): Supported detailed timing:
[    14.167] (II) intel(0): clock: 154.0 MHz   Image Size:  518 x 324 mm
[    14.167] (II) intel(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
[    14.167] (II) intel(0): v_active: 1200  v_sync: 1203  v_sync_end 1209 v_blanking: 1235 v_border: 0
[    14.167] (II) intel(0): Serial No: 2A9281BV0K0
[    14.167] (II) intel(0): Monitor name: LED Cinema
[    14.167] (II) intel(0): Number of EDID sections to follow: 1
[    14.167] (II) intel(0): EDID (in hex):
[    14.167] (II) intel(0): 	00ffffffffffff000610369288a70b02
[    14.167] (II) intel(0): 	1c130104a5342078266ea1a7554c9d25
[    14.167] (II) intel(0): 	0e5054000000d1000101010101010101
[    14.167] (II) intel(0): 	010101010101283c80a070b023403020
[    14.167] (II) intel(0): 	360006442100001a000000ff00324139
[    14.167] (II) intel(0): 	3238314256304b300a20000000fc004c
[    14.167] (II) intel(0): 	45442043696e656d610a202000000000
[    14.167] (II) intel(0): 	00000000000000000000000000000129
[    14.167] (II) intel(0): 	400102000000007e2401a500ffff031a
[    14.167] (II) intel(0): 	1aa80100000000004000000000000000
[    14.167] (II) intel(0): 	00000000000000000000000000000000
[    14.167] (II) intel(0): 	00000000000000000000000000000000
[    14.167] (II) intel(0): 	00000000000000000000000000000000
[    14.167] (II) intel(0): 	00000000000000000000000000000000
[    14.167] (II) intel(0): 	00000000000000000000000000000000
[    14.167] (II) intel(0): 	00000000000000000000000000000057
[    14.167] (II) intel(0): No remaining probed modes for output DP2
[    14.168] (II) intel(0): EDID for output DP3
[    14.168] (II) intel(0): Output VGA1 disconnected
[    14.168] (II) intel(0): Output HDMI1 disconnected
[    14.168] (II) intel(0): Output DP1 disconnected
[    14.168] (II) intel(0): Output HDMI2 disconnected
[    14.168] (II) intel(0): Output HDMI3 disconnected
[    14.168] (II) intel(0): Output DP2 connected
[    14.168] (II) intel(0): Output DP3 disconnected
[    14.168] (WW) intel(0): Unable to find initial modes
[    14.168] (EE) intel(0): Output DP2 enabled but has no modes
[    14.168] (II) intel(0): Kernel page flipping support detected, enabling
[    14.168] (EE) intel(0): No modes.
[    14.168] (II) UnloadModule: "intel"
[    14.168] (II) Unloading intel
[    14.168] (EE) Screen(s) found, but none have a usable configuration.
[    14.168] 
Fatal server error:
[    14.168] no screens found
[    14.168] 
Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[    14.168] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    14.168] 
[    14.169]  ddxSigGiveUp: Closing log

---

### Post by asrock-z68 on 2011-07-21
bump:

Any hints?

---

### Post by BicyclerBoy on 2011-07-21
I'm fairly sure there have been lots of HDMI/Displayport problems recently with the intel driver.
Your problem sounds like the same thing (?).

I guess the apple design does not have a DVI connector..

You could try the more cutting edge drivers from xorg-edgers ppa.
I have found it very reliable last 18 months.

---

### Post by asrock-z68 on 2011-07-22
Thanks for the suggestion BicylerBoy but it didn't work with the latest from ppa: xorg-edgers/ppa either.

Do you know the significance of this warning?

[ xx.xxx] (WW) intel(0): Unable to find initial modes

What is it looking for and where is it looking for it?

---

### Post by asrock-z68 on 2011-07-22
> **BicyclerBoy said:**
> I guess the apple design does not have a DVI connector..

The Apple LED Display is DisplayPort only. It works on another system running 11.04 that has a Nvidia 880M gpu/driver.

---

### Post by brandnamebob on 2011-07-22
I am having this same issue on Gentoo.
I'm using linux-2.6.38-gentoo-r6.
I have tried xf86-video-intel-2.8.1 and xf86-video-intel-2.9.1.
I am now upgrading to linux-2.6.39-gentoo-r2 to see if it helps.

I am on a macbook pro using a 27" Apple LED Cinema display through displayport

Xorg.0.log:
```

[  2835.324] (II) intel(0): EDID for output DP1
[  2835.324] (II) intel(0): Manufacturer: APP  Model: 9236  Serial#: 39754130
[  2835.324] (II) intel(0): Year: 2010  Week: 11
[  2835.324] (II) intel(0): EDID Version: 1.4
[  2835.324] (II) intel(0): Digital Display Input
[  2835.324] (II) intel(0): 8 bits per channel
[  2835.324] (II) intel(0): Digital interface is DisplayPort
[  2835.324] (II) intel(0): Max Image Size [cm]: horiz.: 52  vert.: 32
[  2835.324] (II) intel(0): Gamma: 2.20
[  2835.324] (II) intel(0): DPMS capabilities: Off
[  2835.324] (II) intel(0): Supported color encodings: RGB 4:4:4 
[  2835.324] (II) intel(0): Default color space is primary color space
[  2835.324] (II) intel(0): First detailed timing is preferred mode
[  2835.324] (II) intel(0): Preferred mode is native pixel format and refresh rate
[  2835.324] (II) intel(0): redX: 0.653 redY: 0.334   greenX: 0.300 greenY: 0.615
[  2835.324] (II) intel(0): blueX: 0.146 blueY: 0.057   whiteX: 0.312 whiteY: 0.329
[  2835.324] (II) intel(0): Manufacturer's mask: 0
[  2835.324] (II) intel(0): Supported standard timings:
[  2835.324] (II) intel(0): #0: hsize: 1920  vsize 1200  refresh: 60  vid: 209
[  2835.324] (II) intel(0): Supported detailed timing:
[  2835.325] (II) intel(0): clock: 154.0 MHz   Image Size:  518 x 324 mm
[  2835.325] (II) intel(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
[  2835.325] (II) intel(0): v_active: 1200  v_sync: 1203  v_sync_end 1209 v_blanking: 1235 v_border: 0
[  2835.325] (II) intel(0): Serial No: 2A0110TZ0K0
[  2835.325] (II) intel(0): Monitor name: LED Cinema
[  2835.325] (II) intel(0): Number of EDID sections to follow: 1
[  2835.325] (II) intel(0): EDID (in hex):
[  2835.325] (II) intel(0): 	00ffffffffffff000610369292995e02
[  2835.325] (II) intel(0): 	0b140104a5342078266ea1a7554c9d25
[  2835.325] (II) intel(0): 	0e5054000000d1000101010101010101
[  2835.325] (II) intel(0): 	010101010101283c80a070b023403020
[  2835.325] (II) intel(0): 	360006442100001a000000ff00324130
[  2835.325] (II) intel(0): 	313130545a304b300a20000000fc004c
[  2835.325] (II) intel(0): 	45442043696e656d610a202000000000
[  2835.325] (II) intel(0): 	000000000000000000000000000001e6
[  2835.325] (II) intel(0): 	400102000000007e2401a500ffff031a
[  2835.325] (II) intel(0): 	1aa80100000000004000000000000000
[  2835.325] (II) intel(0): 	00000000000000000000000000000000
[  2835.325] (II) intel(0): 	00000000000000000000000000000000
[  2835.325] (II) intel(0): 	00000000000000000000000000000000
[  2835.325] (II) intel(0): 	00000000000000000000000000000000
[  2835.325] (II) intel(0): 	00000000000000000000000000000000
[  2835.325] (II) intel(0): 	00000000000000000000000000000057
[  2835.325] (II) intel(0): No remaining probed modes for output DP1

```

---

### Post by brandnamebob on 2011-07-22
oops I meant xf86-video-intel-2.15.0-r1

---

### Post by brandnamebob on 2011-07-22
The upgrade to 2.6.39 didn't help.
I might try cloning the git repository for the intel driver and using the latest.

I decoded the EDID data and created a mode using xrandr. I get an error still.

```

$ xrandr --output DP1 --newmode "1920x1200" 154.0 1920 1968 2000 2080 1200 1203 1209 1235 -HSync +VSync
xrandr: Output DP1 is not disconnected but has no modes
xrandr: Output DP1 is not disconnected but has no modes
$ xrandr --addmode DP1 "1920x1200"
xrandr: Output DP1 is not disconnected but has no modes
$ xrandr --output DP1 --mode "1920x1200" --verbose
screen 0: 1920x1200 506x316 mm  96.30dpi
crtc 1:    1920x1200   60.0 +0+0 "DP1"
xrandr: Configure crtc 1 failed
crtc 0: disable
crtc 1: disable
screen 0: revert
crtc 0: revert
crtc 1: revert


```

---

### Post by BicyclerBoy on 2011-07-22
It may be a 'long shot' but..could try to update the mobo BIOS.
There was a thread of this forum in April about similar problem.

One of my intel mobos has had 14 updates (some minor) in 2 years..
One update fixed the on-board network adapter when it stopped with kernel update.

---

### Post by asrock-z68 on 2011-07-22
> **brandnamebob said:**
> I might try cloning the git repository for the intel driver and using the latest.


I'm assuming you are on a new snb 13" macbook pro that only supports the Intel HD 3000 graphics? Let me know how you make out. My solution was to run down to Best Buy and buy a cheap DVI monitor since I can't use my $1000 one.

---

### Post by brandnamebob on 2011-07-22
> **asrock-z68 said:**
> I'm assuming you are on a new snb 13" macbook pro that only supports the Intel HD 3000 graphics? Let me know how you make out. My solution was to run down to Best Buy and buy a cheap DVI monitor since I can't use my $1000 one.

Yes that is correct.

I was able to get it narrowed down to the kernel modesetting. It seems that the IOCTL is returning a Invalid Argument when the frequency is > 144.0 (154.0 would correspond to 60Hz)
I got it to work once at 77.0 (30Hz), but after restarting I can't get the monitor to recognize that it is on.

---

### Post by asrock-z68 on 2011-07-22
> **brandnamebob said:**
> Yes that is correct.

I was able to get it narrowed down to the kernel modesetting. It seems that the IOCTL is returning a Invalid Argument when the frequency is > 144.0 (154.0 would correspond to 60Hz) I got it to work once at 77.0 (30Hz), but after restarting I can't get the monitor to recognize that it is on.

My new DVI monitor is running at 148.5 MHz "1920x1080"x60.0. Wonder why it doesn't like the Apple DP?

Is this an intel-gfx issue or somewhere else?

---

### Post by BicyclerBoy on 2011-07-22
The OP could just buy a discrete video card with displayport..
A $50 nVidia card will out perform the intel GPU as well.

nVidia seems to be limiting displayport to the quadro cards & top end fermi but there were a few displayport versions of the older 9500 9600GT cards
AMD/ATI seem to have greater support for displayport.

---

### Post by asrock-z68 on 2011-07-23
> **BicyclerBoy said:**
> The OP could just buy a discrete video card with displayport..
A $50 nVidia card will out perform the intel GPU as well.

This is not going to work for brandnamebob. He has a brand spanking new sandy bridge Macbook Pro laptop (Intel HD 3000 iGPU only) with a killer external 27" LED Cinema Display.

I've asked for help over at [email]intel-gfx@lists.freedesktop.org[/email] and have got no response so far.

---

### Post by brandnamebob on 2011-07-26
OK, here is the problem: The EDID only lists one valid mode:
1920x1200 at 60Hz.
Which requires a clock rate of 154 at 24bit color.
The Apple LED Cinema Display also advertises only 2 available DisplayPort lanes at 2.7GHz.
But with 24bit color and only two lanes at 2.7GHz, 144 is the maximum clock rate.
Thus the mode is invalid as specified.

The reason the mode would be valid for Windows computers is that they degrade the display down to 18bit color (6bpc) automatically.

With Mac OSX the theory is that they utilize a proprietary DI-EXT extension to turn on the other two lanes for DisplayPort, thus giving Mac OSX a better experience using the display then other OSes.

To fix it in Linux, I hacked the intel-gfx kernel driver to automatically dither down to 6bpc and list the modes as valid. My fix is a pure hack and is not safe to redistribute, but if you want details I can post them. The reason it works on the other system with a nvidia card is I'm guessing that they automatically dither down to 6bpc.

I had a lot of help from the people in #intel-gfx on FreeNode. Without their help I could have never figured out the problem.

---

### Post by asrock-z68 on 2011-07-27
briandnamebob,

I'm glad the folks over at intel-gfx helped you with this. Not being a developer, I assumed I wasn't asking the right questions. Thanks for chasing this down. I'm assuming bpc = bits per channel. What's the relationship between channels and lanes? Do you think the folks over at intel-gfx will ultimately provide a fix? Or are snb Intel-igpu + Apple LED Cinema Display user's SOL?

I'd like to see the changes in the driver you made to make this work. Like I said I'm not a developer but I have made some changes to intel_display.c (gen6_enable_rps) and successfully recompiled the kernel to solve a gpu power issue. Maybe you could provide a diff or replacement driver for me to try.

I know the intel-gfx folks are working on some other DP issues and I'm happy to help in testing (with a little hand holding). I can also provide some information on how Windows 7 x64 handles this if someone can show me where to look. I'd like to contribute however I can.

---

### Post by e8johan on 2011-09-29
I was just able to solve this in an easier manner. I simply add a new modeline, but with a lower refresh frequency.

```
xrandr --newmode "1920x1200_35.00" 107.02 1920 2008 2208 2496 1200 1201 1204 1225 -HSync +Vsync
xrandr --addmode DP1 "1920x1200_35.00"

```
Then I can pick it from the list of resolutions in the Display Settings dialog (in Kubuntu) and it works.

---

### Post by altercation on 2011-11-25
> **e8johan said:**
> I was just able to solve this in an easier manner. I simply add a new modeline, but with a lower refresh frequency.

```
xrandr --newmode "1920x1200_35.00" 107.02 1920 2008 2208 2496 1200 1201 1204 1225 -HSync +Vsync
xrandr --addmode DP1 "1920x1200_35.00"

```
Then I can pick it from the list of resolutions in the Display Settings dialog (in Kubuntu) and it works.

BRILLIANT. This solved it for me.

For what it's worth a refresh rate of 45 also works. Here's a simple script to generate the modelines for both 35 and 45 and add them for xrandr.

```

for _rate in 35 45
do
    _newmode="$(gtf 1920 1200 $_rate.00 | grep Modeline | sed "s/.*Modeline\s*\(.*\)/\1/")"
    _addmode="$(gtf 1920 1200 $_rate.00 | grep Modeline | sed "s/.*Modeline\s*\(\".*\"\).*/\1/")"
    eval xrandr --newmode $_newmode
    eval xrandr --addmode DP1 $_addmode
done

```

---

### Post by kidneb on 2012-05-14
My 24" reports in fine on my nvidia MacBook(5,1) nvidia-stiettings reports 59,95 Hz. Runs fine, but some flickering in movies. (slightly off i assume).

---

