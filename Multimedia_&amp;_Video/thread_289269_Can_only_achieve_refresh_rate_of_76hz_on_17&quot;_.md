---
title: "Can only achieve refresh rate of 76hz on 17&quot; TFT"
date: 2006-10-30
forum: Multimedia &amp; Video
---

### Post by bkj03 on 2006-10-30
Hi.

Bit of a first time for me as I've used these forums to find answers to problems but never actually posted in here before :) 

I recently upgraded from Dapper to Edgy and at the same time bought myself a Hyundai X71S 17" TFT to replace my old 15 "Compaq 5010 TFT

I installed the Nvidia glx via synaptic but can only get a refresh rate of 76hz. The nv driver gives me a choice of 60hz or 75hz and so does the Nvidia glx legacy driver. However I can't get 3D on legacy and very poor 3D on nv, (using the screensavers to test)

The recommended screen refresh rate is 60hz to 75hz and I'm concerned I'll tax the monitor like this, as well as the fact that fonts look slightly fuzzy

I have an old Geforce 440MX card. My xorg.conf file is below and the Vertical / Horizontal rates I added myself but with no joy. 

I've copied & pasted the interesting bits out of the xorg file below

Section "Monitor"
    Identifier     "X71S"
    HorizSync      30-80
    VertRefresh    56-75
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV17 [GeForce4 MX 440]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV17 [GeForce4 MX 440]"
    Monitor        "X71S"
    DefaultDepth    24

Any help very gratefully received. I've been on this for 2 days now and it's driving me crazy

---

### Post by John.Michael.Kane on 2006-10-30
Did you have a read over this? The commands carry over to edgy. [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper) 

Run:
```
gksudo gedit /etc/X11/xorg.conf
```

Here's a sample xorg adjust as needed. the items in **bold** should get you going.

Section "Monitor"
	Identifier	"DELL M782"
	Option		"DPMS"
        [B]HorizSync       30.0-80.0
        VertRefresh     56.0-75.0
      # 1280x1024 @ 75.00 Hz (GTF) hsync: 80.17 kHz; pclk: 138.54 MHz
  Modeline "1280x1024_75.00"  138.54  1280 1368 1504 1728  1024 1025 1028 1069  -HSync +Vsync[/B]
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82815 CGC [Chipset Graphics Controller]"
	Monitor		"DELL M782"
	DefaultDepth	24 [COLOR="red"]you may have to change this to 16[/COLOR]
	SubSection "Display"
		Depth		1
		Modes		**"1280x1024_75.00"** "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
	        Modes	      "1280x1024_75.00"	"1024x768" "800x600" "640x480"            
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		      "1280x1024_75.00"	"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		      "1280x1024_75.00"	"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes	      "1280x1024_75.00"	"1024x768" "800x600" "640x480"	
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		      "1280x1024_75.00"	"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Here's a modeline generator [http://www.sh.nu/nvidia/gtf.php](http://www.sh.nu/nvidia/gtf.php) use this if you need to adjust for 1024x768

---

### Post by bkj03 on 2006-10-31
Many thanks SD-Plissken......the mode line generator and your instructions did the trick.

I'm now watching my screen in full 1280 x 1024 @ 60hz glory with Nvidia 3D :-D 

My only small hiccup was when I set it as below

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV17 [GeForce4 MX 440]"
    Monitor        "X71S"
    DefaultDepth    24
		
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024_60" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"

I figured out that because I set DefaultDepth to 24 I had to alter the section

SubSection     "Display"
        Depth       24
        Modes      "1280x1024_60" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"

---

### Post by John.Michael.Kane on 2006-10-31
Your welcome,and enjoy your time with ubuntu take things slow.

---

