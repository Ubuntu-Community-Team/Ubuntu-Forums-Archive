---
title: "Recent Intrepid install and ATI"
date: 2009-02-03
forum: Multimedia Software
---

### Post by crho85 on 2009-02-03
I recently installed Intrepid onto my HP ZE4300 laptop.*I am running an XP Intrepid dual boot (intrepid was installed 02-02-09)* All went smoothly until I started up. The screen resolution was too high and I could not see the whole screen. Nothing was listed under screen resolutions. I knew right away that this was caused by the dreaded ATI Radeon Mobilty IGP 320M (AKA U1). In order to do anything I installed the ATI driver with EnvyNG. Now I am running but in low graphics mode.

Here is the xorg file.

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

As you see it is not saying much. the lspci -nn | grep VGA reports the correct card. 

I found [COLOR="Red"]_[this page]("https://help.ubuntu.com/community/RadeonDriver") _[/COLOR]

Will this work for me. If not could someone please help me out, I am still pretty new to the ubu .

---

### Post by anv on 2009-02-03
I used this site successfully with my card (3300) 

[http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide)

but because all cards are not so well supported I can't promise. I used the manual method. It can be good option that you would copy original xorg somewhere where you can easily rescue xorg, if you accidentally do something wrong and drop in to command line mode. I understood that you had already modified your xorg, so one place how to obtain original files is copy them after live boot from boot able intrepid cd, or doing:

sudo dpkg-reconfigure xserver-xorg

but just in case something goes wrongly, which doesn't need to happen. good luck.

---

### Post by crho85 on 2009-02-03
> **anv said:**
> I used this site successfully with my card (3300) 

[http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide)

but because all cards are not so well supported I can't promise. I used the manual method. It can be good option that you would copy original xorg somewhere where you can easily rescue xorg, if you accidentally do something wrong and drop in to command line mode. I understood that you had already modified your xorg, so one place how to obtain original files is copy them after live boot from boot able intrepid cd, or doing:

sudo dpkg-reconfigure xserver-xorg

but just in case something goes wrongly, which doesn't need to happen. good luck.
 
how can i get xorg to display the info instead of "configured". should i uninstall envyng? and where and how do you recommend I back up the xorg.conf

---

### Post by anv on 2009-02-03
Yes...I forget have you done this?

sudo aticonfig  

it configures your xorg.conf for the installed card and driver

but do the backup before:

backup:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

(in case you need) restore:

sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf

then restart. and the driver which envyng installed should be active.

but if the driver isn't working and you are forced to go through the earlier method which I gave link to you I believe the best thing is to remove envyng first.

---

### Post by markbuntu on 2009-02-03
Envy....meh. Envy does not install the latest ati drivers or even recent ones and often fails to load the kernel modules. No kernel modules, no usable driver. Low graphics mode means envy did not install the driver properly.

When installing Intrepid use the safe graphics mode (F4 on the initial menu screen for options.) After the install is up and running and you have a desktop either run Hardware Manager to get the 8.11 driver or go to ati and get the latest driver,9.1, download it and run the installer.

sudo sh./ati-driver-installer........

**DO NOT USE ENVY FOR ATI DRIVERS WITH INTREPID**

If it is too late and you are having problems. When the grub menu screen comes up choose recovery mode. Choose the fix x option and then resume. When you get to the desktop if Envy has already misinstalled a driver, use envy to completely remove it. 

Then  you can use hardware manager or get the latest driver from ati. If you do get the driver from ati and install it keep the package somewhere handy because you will need to fix-x and reinstall the driver after kernel updates, a 2 minute process now that you know how.

---

### Post by crho85 on 2009-02-04
Thank you to everyone for your help. I tried the methods listed above but to no avail. So I reverted to the initial conf (listed above) and I had everything working BUT the res. Then I had this idea:


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
       [B] SubSection "Display"
               Modes             "1024x768"
        EndSubSection[/B]
EndSection
```

Results:
```
glxinfo 
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Tungsten Graphics, Inc.
direct rendering: Yes
```

I don't know why I didn't think of this before. Again Thank you all for your help

Now my system impresses the windows crowd who thought it was "minimalist":p

---

