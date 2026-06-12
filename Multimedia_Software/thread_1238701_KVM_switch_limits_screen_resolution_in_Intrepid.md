---
title: "KVM switch limits screen resolution in Intrepid"
date: 2009-08-12
forum: Multimedia Software
---

### Post by truetech08 on 2009-08-12
Accidentally posted this in the wrong forum, so trying again here:

I've just installed a Belkin Flip VGA USB w/audio KVM switch. I run Intrepid on my laptop and desktop. After booting my desktop cleanly through the KVM, (and many reboots), I only have a max res of 1024x768. The monitor abilities don't seem to be detected anymore. I run Nvidia drivers, and the Nvidia X Server settings in System - Admin allows me to assign a wacky 1152 x 864 resolution, but it doesn't look right. I was running 1280 x 1024 @ 75hz just fine without the KVM. Another weird thing is when I start Firefox, I can't minimize or switch to desktop, or copy/paste from that window to anything else, there's no title bar at the top.

I think that I need to force Ubuntu to allow a higher res than it thinks the monitor can handle. I've tried editing my xorg.conf file by following some other posts, but mine doesn't look like anyone else's, and I'm not even sure if that's what I need to do. Has anyone else solved this kind of problem? Code from xorg.conf file below, typed manually on my laptop because can't copy from file into Firefox:

Section "Monitor"
             Identifier                   "Configured Monitor"
EndSection

Section "Screen"
            Identifier                  "Default Screen"
           Monitor                    "Configured Monitor"
            Device                   "Configured Video Device"
            DefaultDepth          24
EndSection

Section "Module"
             Load           "glx"
EndSection

Section "Device"
             Identifier               "Configured Video Device"
             Driver                   "nvidia"
            Option                   "NoLogo"                "True"
EndSection
 		                   		  		  		  		  		  	   	 		 [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]  		 		 		[[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=7723420") 		 		  	 	 	 	 		  		 			[IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG] 			[[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=7723420")

---

### Post by AKADAP on 2009-08-13
You need to explicitly tell Ubuntu what your monitor is capable of if you don't want to buy new hardware (sorry I don't know how to do that).

Alternatively, you could get a KVM that echoes what the monitor tells it. I have a IOGear GCS1204 KVM that I am very happy with. It is dual link DVI, so probably not appropriate for your set up, but it remembers what the monitor tells it and pretends to be the monitor when the PC requests info from the monitor. I have it running at 2560x1600 with no problems.

---

### Post by truetech08 on 2009-08-13
I'd actually like to keep the KVM I have if I can, it's a simple setup and easy to use, so I'll wait for a bit to see if anyone else knows how to tell Ubuntu what the monitor is capable of.  If not, I'll have to return the KVM and get another.  Thanks for the info on your KVM though, I'll look into it!

---

### Post by marfal on 2009-08-28
I'm still having the same problem, here's a section of the the output when running  
"sudo get-edid | parse-edid" 
from the monitor plugged directly into the pc. Followed by the same section when plugged into the KVM switch. It appears the switch isn't passing the EDID through.
I have had the switch replaced but it has made no difference.

Is there any way to fix the monitor resolution in Ubuntu so that it will boot to that resolution with the monitor unplugged? I really need that!

**Plugged into PC**

Performing real mode VBE call
	Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
	Function supported
	Call successful

parse-edid: EDID checksum passed.

	# EDID version 1 revision 3
Section "Monitor"
	# Block type: 2:0 3:ff
	# Block type: 2:0 3:fd
	# Block type: 2:0 3:fc
	Identifier "38B2"
	VendorName "FUS"
	ModelName "38B2"
	# Block type: 2:0 3:ff
	# Block type: 2:0 3:fd
	HorizSync 30-63
	VertRefresh 55-75
	# Max dot clock (video bandwidth) 80 MHz
	# Block type: 2:0 3:fc
	# DPMS capabilities: Active off:yes  Suspend:yes  Standby:yes

	Mode 	"1024x768"	# vfreq 60.004Hz, hfreq 48.363kHz
		DotClock	65.000000
		HTimings	1024 1048 1184 1344
		VTimings	768 771 777 806
		Flags	"-HSync" "-VSync"
	EndMode
	# Block type: 2:0 3:ff
	# Block type: 2:0 3:fd
	# Block type: 2:0 3:fc
EndSection

**Plugged into KVM**

Performing real mode VBE call
	Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
	Function supported
	Call failed

The EDID data should not be trusted as the VBE call failed
Error: output block unchanged
parse-edid: IO error reading EDID

---

### Post by AKADAP on 2009-08-28
It used to be done in a X configuration file, but it has been moved to HAL Try some googling on HAL.

---

### Post by truetech08 on 2009-08-30
Thanks AKADAP,I did some looking into HAL, and it looks like it's only for input devices?   I don't see anything that ties it to screen resolution issues.  If you're sure that HAL is now the place to edit display config settings, can you post a link to some documentation so I can check it out?  There MUST be a way to force a screen resolution.

---

### Post by bearsomg on 2009-08-30
> **truetech08 said:**
> Thanks AKADAP,I did some looking into HAL, and it looks like it's only for input devices?   I don't see anything that ties it to screen resolution issues.  If you're sure that HAL is now the place to edit display config settings, can you post a link to some documentation so I can check it out?  There MUST be a way to force a screen resolution.


Yes, there is a way to force a screen resolution. First, go into the Terminal and type 
```
gtf horizontal-size vertical-size refresh-rate
```replacing the three options i gave with the correct info. So for example if you wanted 1024x768 at 60 refresh rate, you would type:

```
gtf 1280 1024 75
```It will output the correct modeline for you with that resolution at the provided refresh rate. Using the resolution you say you can run without the KVM:

```
# 1280x1024 @ 75.00 Hz (GTF) hsync: 80.17 kHz; pclk: 138.54 MHz
  Modeline "1280x1024_75.00"  138.54  1280 1368 1504 1728  1024 1025 1028 1069  -HSync +Vsync
```Highlight the 

 Modeline "1280x1024_75.00"  138.54  1280 1368 1504 1728  1024 1025 1028 1069  -HSync +Vsync

part, copy it, and paste it in a text editor like Gedit. In the "1280x1024_75.00" part, delete the _75.00 part so it looks like "1280x1024". Hightlight the entire line, copy it and then in the Terminal type 

```
sudo gedit /etc/X11/xorg.conf
```When xorg.conf opens, find the Monitors section. Put in these two lines
HorizSync       31.47 - 48.36
    VertRefresh     56.0 - 75.0

replacing the numbers with the correct horizontal sync and vertical refresh rates for your monitor. Then paste in the text that you copied from the text editor as another line.

Now go down to the Screen section and add:

```
SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "800x600" "640x480"
    EndSubSection
```Restart the X server and you should be able to choose your resolution. Remember to change 1024x768 to the resolution you want.


If you use this technique, you will NOT need to remove the KVM switch. Add as many Modelines to the Monitors section as you want using this method for different resolutions you want to use.

---

### Post by truetech08 on 2009-08-30
Thanks Bear, I actually did find that exact article and followed it to the letter mulitple times, but upon restarting X I am greeted with an error message that the xorg.conf file was unable to be parsed.  I can't tell what I'm doing wrong.  Would it help to post my code so someone could see my exact code placement?

---

### Post by Brian M on 2010-03-11
bearsong,

I'm currently running Karmic 9.10 and I'm having the same problem concerning screen resolution settings while using a KVM switch.  I thought I would give your solution a try, but you lost me when you said to find the "Monitors section" when xorg.conf opens.  When I open xorg.conf it's a blank screen & when I search for the Monitors section I come up empty.  

Please excuse my lack of knowledge, I'm kind of feeling my way around and getting my hands dirty here.  Also, thanks for the otherwise clear and well laid out instructions, it makes it much easier for noob's like me!:rolleyes:

---

