---
title: "Latest Nvidia driver did not solve the resolution problem"
date: 2008-01-31
forum: Multimedia &amp; Video
---

### Post by bharkins on 2008-01-31
I have read just about everything on the Forum on the issue of setting screen resolution with the latest nVidia driver, 169.09. The latest version of ENVY installs the driver and everything goes fine...up until the point of adjusting the screen resolution down from the max of 1680x1050. It is locked at that number in the Preferences menu, the nvidia-settings and in the xorg.conf file. I have sent an nvidia bug report to tech support at nvidia, but I do not have much hope in getting it changed - it is a bug somewhere however IMHO. As I stated in previous posts, I got Compiz running fine on my old Dell 8200 with an ATI Radeon 9000 video card with no adjustments and can run at a comfortable 1260x800 screen - 5 year old hardware!

---

### Post by overdrank on 2008-01-31
> **bharkins said:**
> I have read just about everything on the Forum on the issue of setting screen resolution with the latest nVidia driver, 169.09. The latest version of ENVY installs the driver and everything goes fine...up until the point of adjusting the screen resolution down from the max of 1680x1050. It is locked at that number in the Preferences menu, the nvidia-settings and in the xorg.conf file. I have sent an nvidia bug report to tech support at nvidia, but I do not have much hope in getting it changed - it is a bug somewhere however IMHO. As I stated in previous posts, I got Compiz running fine on my old Dell 8200 with an ATI Radeon 9000 video card with no adjustments and can run at a comfortable 1260x800 screen - 5 year old hardware!

HI and I have seen several users with the 7600 with similar issues. My son's system with the 7300 took some work to install also. If this is the same card we are speaking of listed in your signature. Would you mind post your xorg ```
cat /etc/X11/xorg.conf
```

---

### Post by bharkins on 2008-02-02
> **overdrank said:**
> HI and I have seen several users with the 7600 with similar issues. My son's system with the 7300 took some work to install also. If this is the same card we are speaking of listed in your signature. Would you mind post your xorg ```
cat /etc/X11/xorg.conf
```

I can run the xorg.conf file in Terminal, but I can't save it. How do I post it?

---

### Post by zeusx64 on 2008-02-03
Good day my friend. I have had resolution problems before, which were never really fixed except by hand. To fix by hand, if in fact you are having the issue of too low a resolution or just not as high as you like, you can do this.
1. Open a terminal
2. Type: sudo gedit /etc/X11/xorg.conf
3. Type your password at prompt
4. gedit should open the xorg.conf file for editing with root privilage

Keep in mind that this is at your own risk but as I have found, it is sometimes neccessary. Below is my screen section from my xorg.conf file. Just scroll down through yours and you will find it. You can manually edit it to show the higher resolutions, then click save, and then exit and reboot your PC.
I used the Envy script too and mine works great but try to manually add them into the file with the above method. I have done it before but that is your choice to make.
Goodluck.



Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 AP [Radeon 9600]"
	Monitor		"CM2019"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

---

### Post by bharkins on 2008-02-04
Well, zeusx64, that seemed like a great idea. I edited the xorg.conf exactly as you showed in yours. However, the system didn't budge from the 1680x1050 resolution. Looks like xorg.conf doesn't recognize any changes to the SubSection Display lines. The Nvidia Settings also shows the same situation - one resolution only, and can't be selected by any other resolution. Looks to me like an nVidia driver bug even though 169.09 is installed via ENVY. Thanks for your help.

---

### Post by overdrank on 2008-02-04
> **bharkins said:**
> Well, zeusx64, that seemed like a great idea. I edited the xorg.conf exactly as you showed in yours. However, the system didn't budge from the 1680x1050 resolution. Looks like xorg.conf doesn't recognize any changes to the SubSection Display lines. The Nvidia Settings also shows the same situation - one resolution only, and can't be selected by any other resolution. Looks to me like an nVidia driver bug even though 169.09 is installed via ENVY. Thanks for your help.

HI and you can try and use Envy manually install the older nvidia driver that helped with my son's system this weekend.

---

