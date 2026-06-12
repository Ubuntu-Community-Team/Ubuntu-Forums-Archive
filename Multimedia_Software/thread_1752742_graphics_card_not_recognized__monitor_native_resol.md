---
title: "graphics card not recognized / monitor native resolution not available"
date: 2011-05-08
forum: Multimedia Software
---

### Post by chriswatrous on 2011-05-08
<EDIT> Never mind. I actually do have a GeForce4 MX 460 in this pc. I have a 7950gt in a different pc. Oops. I guess the MX 460 cant do 1600x1200 on the dvi output but somehow it can do it on the vga output? I guess I could just use a vga connection instead of the dvi connection. </EDIT>

The problem I'm having is that my LCD monitor (acer AL2021) can't be used at it's native resolution of 1600x1200. This is probably because my GeForce 7950gt graphics card is not being recognized. Xorg seems to think my card is a GeForce4 M 460. (It's not, really!) I'm using Ubuntu 10.04 LTS.

Here's what I've been doing for the last few hours:

	deleted: /etc/X11/xorg.conf (after making a backup)
	ran: nvidia-xconfig (to regenerate xorg.conf)
	rebooted

This didn't work. 1600x1200 is still not listed.

	in xorg.conf added: '1600x1200 +0+0;' to Option	"metamodes" line in the screen section

no change

	rebooted

no change

	in xorg.conf changed upper number on HorizSync line to 90

now monitor doesn't work at all

	logged in with secure shell, changed it back to 79

monitor works again but still same problem

	changed it to 81 (saw that on some web page)
	restarted x server: sudo /etc/init.d/gdm restart

no change

	tried to run nvidia driver installer:
		sudo bash NVIDIA-Linux-x86-270.41.06.run
	error messages:
		  The NVIDIA GeForce4 MX 460 GPU installed in this system is supported through the    
		  NVIDIA 96.43.xx legacy Linux graphics drivers.  Please visit
		  [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) for more information.  The 270.41.06 NVIDIA  
		  Linux graphics driver will ignore this GPU.

		  You do not appear to have an NVIDIA GPU supported by the 270.41.06 NVIDIA Linux     
		  graphics driver installed in this system.  For further details, please see the      
		  appendix SUPPORTED NVIDIA GRAPHICS CHIPS in the README available on the Linux       
		  driver download page at [www.nvidia.com](www.nvidia.com).

		  You appear to be running an X server; please exit X before installing.  For further   
		  details, please see the section INSTALLING THE NVIDIA DRIVER in the README available  
		  on the Linux driver download page at [www.nvidia.com](www.nvidia.com).

		  Installation has failed.  Please see the file '/var/log/nvidia-installer.log' for     
		  details.  You may find suggestions on fixing installation problems in the README      
		  available on the Linux driver download page at [www.nvidia.com](www.nvidia.com).

I just noticed my graphics card is not being recognised.
The above message says 'NVIDIA GeForce4 MX 460 GPU'
nvidia-settings shows the same thing

	in xorg.conf changed 'GeForce4 MX 460' to 'GeForce 7950GT'
	restarted x server: sudo /etc/init.d/gdm restart

monitor not working

	logged in with secure shell and changed it back

monitor still not working

	restored xorg.config from a backup

monitor still not working
	
	hooked up CRT monitor

only VGA output is working and only in 640x480

	regenerated xorg.conf with nvidia-xconfig

now CRT is working at its old resolution of  1600x1200

	played with settings in nvidia-settings

now LCD is working as a second monitor but with low resolution
still thinks the graphics card is 'GeForce4 MX 460'

	edited xorg.conf: changed BoardName in 2 lines to 'GeForce 7950 GT'

no effect but they still work

	edited xorg.conf: changed driver from "nvidia" to "nv" (saw that somewhere)

no longer using the nvidia driver, LCD not working at all
still not recognising the graphics card

	restored xorg.conf

both monitors working, LCD still at low resolution

tried this procedure:
	[http://www.linuxjournal.com/content/guerrilla-tactics-force-screen-mode-ubuntu](http://www.linuxjournal.com/content/guerrilla-tactics-force-screen-mode-ubuntu)

	cvt 1600 1200 60
	xrandr --newmode "1600x1200_60.00"  161.00  1600 1712 1880 2160  1200 1203 1207 1245 -hsync +vsync
	xrandr --addmode default 1600x1200_60.00
	xrandr --output default --mode 1600x1200_60.00
	error message:
		xrandr: screen cannot be larger than 1024x768 (desired size 1600x1200)

	resolution was on 1024x768, changed to 1280x1024 with nvidia-settings
	xrandr --output default --mode 1600x1200_60.00
	error message:
		xrandr: Configure crtc 0 failed

	tried nv driver again, setting BoardName to 'Generic Geforce 7800'

same result as before when I used the nv driver

	went to System->Administration->Hardware Drivers
	switched to the recomended driver
	rebooted

back to square 1
	
	can't seem to install envy, possibly because my Ubuntu version is to recent?

	tried sudo dpkg-reconfigure xserver-xorg
	restarted x server

now both monitors don't work

	ran nvidia-xconfig

both monitors back, same problem


Here's the output of xranr:
```

Screen 1: minimum 320 x 240, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       50.0*    51.0     52.0  
   960x600        53.0  
   960x540        54.0  
   840x525        55.0     56.0     57.0  
   832x624        58.0  
   800x600        59.0     60.0     61.0     62.0     63.0  
   800x512        64.0  
   720x450        65.0  
   680x384        66.0     67.0  
   640x512        68.0  
   640x480        69.0     70.0     71.0     72.0  
   640x400        73.0     74.0  
   576x432        75.0     76.0     77.0     78.0  
   512x384        79.0     80.0     81.0  
   416x312        82.0  
   400x300        83.0     84.0     85.0     86.0  
   320x240        87.0     88.0     89.0  


```

Here's my xorg.conf:
```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder75)  Thu Apr 15 05:52:31 PDT 2010

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@palmer)  Fri Apr  9 10:35:18 UTC 2010

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

	# generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "SONY CPD-E400"
    HorizSync       30.0 - 96.0
    VertRefresh     48.0 - 120.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Acer AL2021"
    HorizSync       26.0 - 79.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Generic Geforce 7800"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Generic Geforce 7800"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT: 1600x1200 +0+0; CRT: 1280x1024 +0+0; CRT: 1024x768 +0+0; CRT: 800x600 +0+0; CRT: 640x480 +0+0"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: nvidia-auto-select +0+0"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

The attached image was taken after doing all of this stuff.

---

### Post by Seinfeld on 2011-05-11
Hi.. 

My problem is somehow similar. I am using 2 Nvidia 9600 and 8600 cards. I have two monitors running in TwinView with no problem on the first card. 
When I added a third monitor to use as a separate x screen, connected to the second card, it worked but the Twin View switches to Xinerama. The  first card sees the first two screens as one spreads the view on two monitors. Isn't that Xinerama?? I did disable xinerma from nvidia settings, restarted xserver but, no way. 
I Just need two monitors working in a TwinView on the first card and the third one connected to the second card as a separate screen.. 
Any help please is much appreciated..

Thank you very much

---

