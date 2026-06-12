---
title: "HOWTO:  ViewSonic 20.1&quot; LCD with with nVidia drivers"
date: 2006-10-09
forum: Multimedia &amp; Video
---

### Post by htmlguy716 on 2006-10-09
**Scope:**
This guide tells you to configure a ViewSonic wm2025wm to work with the closed source nVidia drivers at the native resolution of 1680x1050. This tutorial is intended for machines running Ubuntu 6.06 LTS (Dapper Drake), Ubuntu 6.10 (Edgy Eft), or Ubuntu 7.04 (Feisty Fawn). This guide is written specifically for the ViewSonic VX2025wm display. However, if you are using a different flat-panel display, a look at this guide could help you to fix your problem.

**Problem:**
Ever since I set up my computer with Ubuntu, my ViewSonic 20.1" LCD has not been friendly with my nVidia graphics card. It works fine at 1280x1024 resolution with the VESA (open source) drivers. However, when I try to configure it for 1680x1050 (the native resolution), the monitor displays a glorious 20.1 inches of black and the text "Out Of Range" in the middle.

**Solution:**
**Step 1:** I *strongly* recommend making a backup of your xorg.conf file before making changes to your monitor settings. This can be done by entering this command in Terminal: ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
If you ever have a problem with the GUI, you can boot up in recovery mode and type ```
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
``` to get your old settings back.

**Step 2:** Next, you want to make sure that you have the latest versions of xserver-xorg and nvidia-glx. If you do not have nvidia-glx, you can get it by [enabling the Univserse and Multiverse repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#head-a86dddc6826cec4a3847d8441b24051d07b8dc64), and then typing "sudo apt-get install nvidia-glx" in Terminal. To make sure you have the latest version of everything, run Update Manager from the System menu.

**Step 3:** Now you need to open a new text-only console. With the default configuration of Ubuntu, this is done by pressing [CTRL]+[ALT]+[F1]. You can switch back to the regular GUI by pressing [CTRL]+[ALT]+[F7] or restarting your computer.
Enter your username and password and run the following command to configure the display and graphics card:```
sudo dpkg-reconfigure xserver-xorg
```
The only thing that is really that important here is when it asks you which driver to use. Be sure to select "nvidia" and not any other option. If you are unsure about anything else, it is a safe bet to leave it at the default.

After you have gone through the bazillion or so questions to configure xorg, run the following command: ```
sudo nvidia-xconfig
```

**Step 4:** Next you need to make a few tweaks to the file you just created. Type "sudo nano /etc/X11/xorg.conf" to bring up a simple command-line text editor. The native resolution of your monitor is 1680x1050, but what Xorg doesn't know is that this setting will only work at a frequency of 60 Hz. To fix this, find the section that looks like this: ```
Section "Screen"
	...
	SubSecton "Display"
		Depth		1
		Modes		"1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection

	SubSecton "Display"
		Depth		2
		Modes		"1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection

	SubSecton "Display"
		Depth		4
		Modes		"1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection

	SubSecton "Display"
		Depth		8
		Modes		"1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection

	SubSecton "Display"
		Depth		16
		Modes		"1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection

	SubSecton "Display"
		Depth		24
		Modes		"1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
``` Wherever it says "1680x1050", replace that with "1680x1050_60". It should now look like this: ```
Section "Screen"
	...
	SubSecton "Display"
		Depth		1
		Modes		"1680x1050_60" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection

	SubSecton "Display"
		Depth		2
		Modes		"1680x1050_60" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection

	SubSecton "Display"
		Depth		4
		Modes		"1680x1050_60" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection

	SubSecton "Display"
		Depth		8
		Modes		"1680x1050_60" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection

	SubSecton "Display"
		Depth		16
		Modes		"1680x1050_60" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection

	SubSecton "Display"
		Depth		24
		Modes		"1680x1050_60" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```Press [CTRL]-x to exit out of nano and press y to save the file.

**Step 5:** Now for the moment of truth. Run in the console:```
sudo /etc/init.d/gdm restart
```
If the result is "OK", press [CTRL]-[ALT]-[F7] to switch to your new widescreen setup.

**Problems:**
If you are using Edgy Eft, you may also need to change your horizontal and vertical sync rates in the Xorg.conf file (step 4). Replace the two corresponding lines in your "Monitor" section with this: ```
HorizSync	30-82
VertRefresh	50-75
```

If you get an out of range message or an error starting the GNOME Display Manager (step 5), you can congratulate yourself for making a backup and type ```
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
sudo /etc/init.d/gdm restart
``` to get your old configuration back.

**Conclusion:**
I hope this helps all the people who are experiencing similar problems with their monitor. This is my first howto, so feel free to leave comments on my instructions, or tell me what I could have done differently.

---

### Post by tseliot on 2006-10-09
> **htmlguy716 said:**
> First, you want to make sure that you have the latest versions of xserver-xorg and nvidia-glx. If you do not have nvidia-glx, you can get it by [enabling the Univserse and Multiverse repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#head-a86dddc6826cec4a3847d8441b24051d07b8dc64), and then typing "sudo apt-get nvidia-glx" in Terminal. To make sure you have the latest version of everything, run Update Manager from the System menu.

the right command is:
```
sudo apt-get install nvidia-glx
```

and you will also need to type:
```
sudo nvidia-xconfig
```

---

### Post by htmlguy716 on 2006-10-09
Thank you for the advice, Alberto.

> **tseliot said:**
> the right command is:
```
sudo apt-get install nvidia-glx
```
I always forget that part ](*,) 

> **tseliot said:**
> and you will also need to type:
```
sudo nvidia-xconfig
```
I've tried it both ways, and for me it tends to work fine just letting dpkg configure the xorg.conf file, and not having nvidia-xconfig mess with it. However, I can't see how adding that command would hurt, so I'll put it in the instructions.

---

### Post by Paulr-55 on 2006-12-10
Thanks for this info. I had to give up getting my widescreen going under the free drivers. I installed the invidia drivers (SEE ABOVE) edited /etc/X11/xorg.conf  adding "1440x900_75" to each display section in the "Screen" section. I did not change or add anything else.

```
Section "Monitor"
    Identifier     "DELL E770s"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
    Monitor        "DELL E770s"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1440x900_75" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1440x900_75" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1440x900_75" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1440x900_75" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1440x900_75" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1440x900_75" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

```

Then I did ctrl+alt+bckspc to restart X and it works fine.

Thanks for the help!

---

### Post by htmlguy716 on 2006-12-10
I'm glad that I could help, Paulr-55.

P.S. If anyone wants to make a generic version of this HowTo that applies to more than just the ViewSonic LCD's, feel free to plagiarize my text.

---

### Post by Paulr-55 on 2006-12-12
I note that the code block (first post) to make a backup of xorg.conf is missing the ".bak"

Should be:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf[COLOR="Red"].bak[/COLOR]
```

Thanks again.

---

### Post by prankst3r on 2007-04-17
This problem with the Viewsonic vx2025wm monitor still exists in Feisty. Except that the only step that is needed is simply to append the "_60" to the end of the 1680x1050 in the xorg.conf file.

---

### Post by htmlguy716 on 2007-04-17
> **prankst3r said:**
> This problem with the Viewsonic vx2025wm monitor still exists in Feisty. Except that the only step that is needed is simply to append the "_60" to the end of the 1680x1050 in the xorg.conf file.

Thank you. I've updated the guide to apply to Edgy and Feisty

---

### Post by kabuchin on 2008-05-26
Will this work on ubuntu 8.04 ? I've got the resolution problem on a fresh install. Please help, i'm driving crazy with this. Thanks.

---

### Post by Anlace on 2008-06-23
Sorry but no, it doesn't.  At least it did not for me.

What does work is to use the nv driver provided by Xorg and configure your display as a generic LCD 1680x1050 (widescreen) resolution.

---

### Post by htmlguy716 on 2008-06-23
I had to use the VGA to get my ViewSonic LCD to work with 8.04. Basically, nvidia-glx-new overrides most of what you put in the xorg.conf with rules sent by the monitor. To worsen the problem, ViewSonic LCD's will broadcast incorrect video settings. If anyone comes up with a solution to this, I will mark them as awesome in my book.

---

