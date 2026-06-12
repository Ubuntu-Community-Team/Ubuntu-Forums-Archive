---
title: "multiple monitor configurations"
date: 2009-02-18
forum: Multimedia Software
---

### Post by period3 on 2009-02-18
I'm running Intrepid on my thinkpad T60 laptop (ATI X1300, Radeon driver).  I use two main configurations.

At work, I have a 1280x1024 external LCD, which I use in combination with the laptop's built in 1400x1050 LCD.  To do this, I have added the following to the 'screen' section of xorg.conf:
	SubSection "Display"
		Virtual 2800 1050
	EndSubSection

At home, I have a 1920x1200 external LCD.  When I use it, I disable the laptop LCD.  To use this configuration, I have to delete the above lines from xorg.conf, and logout and back in again.  

How can I use both of these configurations without having to constantly change my xorg.conf?

(If I use the xorg.conf with the Virtual line, the resolution for my external monitor only goes as high as 1680x1050.  If I use the xorg.conf without the virtual line, the dual screen setup doesn't work properly)

---

### Post by period3 on 2009-03-04
Does anyone have any tips on this?

> **period3 said:**
> I'm running Intrepid on my thinkpad T60 laptop (ATI X1300, Radeon driver).  I use two main configurations.

At work, I have a 1280x1024 external LCD, which I use in combination with the laptop's built in 1400x1050 LCD.  To do this, I have added the following to the 'screen' section of xorg.conf:
	SubSection "Display"
		Virtual 2800 1050
	EndSubSection

At home, I have a 1920x1200 external LCD.  When I use it, I disable the laptop LCD.  To use this configuration, I have to delete the above lines from xorg.conf, and logout and back in again.  

How can I use both of these configurations without having to constantly change my xorg.conf?

(If I use the xorg.conf with the Virtual line, the resolution for my external monitor only goes as high as 1680x1050.  If I use the xorg.conf without the virtual line, the dual screen setup doesn't work properly)

---

### Post by skotos on 2009-03-04
> **period3 said:**
> How can I use both of these configurations without having to constantly change my xorg.conf?
It is the problem I have asked for some info in a post of mine - see [http://ubuntuforums.org/showthread.php?t=1081296](http://ubuntuforums.org/showthread.php?t=1081296) - but, just not to delete the configuration and simply "unrem" the profile you want to run, you might simply try something like this[php]Section "ServerLayout"
    Identifier     "LayoutOfLCDandElectron19BlueIII"
    Screen      0  "ScreenOf9815WKMI" 0 0
    Screen      1  "ScreenOfElectron19BlueIII" RightOf "ScreenOf9815WKMI"
EndSection

Section "ServerLayout"
    Identifier     "LayoutOfLCDandSonyTV"
    Screen      0  "ScreenOf9815WKMI" 0 600
    Screen      1  "ScreenOfSonyTV" Above "ScreenOf9815WKMI"
EndSection

Section "ServerFlags"
#    Option         "DefaultServerLayout" "LayoutOfLCDandElectron19BlueIII"
    Option         "DefaultServerLayout" "LayoutOfLCDandSonyTV"
    Option         "Xinerama" "0"
EndSection[/php]That is, store 2 layouts in the same xorg.conf and set the default server layout inside the **ServerFlags** section. This way you will not need to remember all the different parameters and sections, nor you will not duplicate any file.

If you want or need it, you may have a look at my full xorg.conf by going to the above mentioned post.

Unfortunately, I am running an Nvidia proprietary driver and I do not know how to check, just before running X, what kind of second device is present (or not), so at the moment I cannot write a shell script to automatically set the expected layout.

I think that this might be the real problem: _is there any info under **/proc** on how many display devices and what hardware settings they are found to run with?_

If this info were available just before X (eg. in the previous runlevel) a simple script - run as a service - might silently accomplish the task: see smani's suggestion.

HTH

---

