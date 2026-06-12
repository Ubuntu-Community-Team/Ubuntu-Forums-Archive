---
title: "refresh rate to 60 on lcd"
date: 2006-09-03
forum: Multimedia &amp; Video
---

### Post by wonder1 on 2006-09-03
The refresh rate is 75 Hz.
The display I am using is Dell 1907fp  LCD 
The resolution is correct 1280x1024 but the refresh rate is 75.

The specifications say that the 
Optimum is 1280x1024 @ 60Hz although the max is 1280x1024 @ 75 Hz
So it is going to the max value .
How do I get it to the Optimum value (which is recommended)

The chipset is Intel 82945
and the driver that is being selected is i810

---

### Post by croak77 on 2006-09-03
You can edit /etc/X11/xorg.conf. And try changing to 60Hz. 

```
sudo nano -w /etc/X11/xorg.conf
```

Ctrl-X to save. Or use you favorite text editor.

---

### Post by tseliot on 2006-09-03
Try this guide:
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)


OR this one (read where it says "Getting the Right Mode for an LCD monitor"):
[https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration](https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration)

---

### Post by wonder1 on 2006-09-10
Thanks croak77 and tseliot.
         
         croak77 , Manually changing the vertical refresh rate to 60 in xorg.conf does  not solve the problem.
         Referring to the first link given by tseliot I attempted to reconfigure xorg. I selected the i810 driver from the list. The chipset  is Intel 945 .The i810 driver (latest version that comes with the system supports intel chipsets upto 945). Then after a few steps there was an option of medium and advanced for resolution and refresh rate. I first selected medium and here an option was 1280X1024@60 . I selected this one . When I started and checked the refresh rate it was still 75. Next I again went to the reconfigure stage and selected the advanced option this time . Here I was to enter the horizontal and vertical scan range which I selected as 30 to 81 for horizontal and 56 to76 for vertical ( as given in the specifications for the display ). When I checked after logging in the refresh rate was still 75 . Then I limited the vertical range 56 to 60 . But even this had no effect.
	So I went the second link provided by tseliot . From the gtf command I generated a modeline for 1280 1024 60 . Let this modeline be referred to as ModelineA . And inserted this in the monitor section. This time the refresh rate changed.From system -> preferences ->screen resloution it showed 60 but from the osd it showed 61. This confused me . Although this was very close to the value but still something more was needed.
	
        The following two approaches succeded:

        Approach_1: Then I had a look at the suse xorg.conf file which I have and checked the modeline there . Let this modeline be referred to as ModelineB . After inserting the modeline I got the refresh rate 60. In suse also first it was 75 . It had an option for lcd  in which 1280x1024@60 was there.This made the refresh rate 60 in suse.
	Approach_2: To check this further
I came across this page 
[http://wiki.x.org/wiki/FAQVideoModes](http://wiki.x.org/wiki/FAQVideoModes)
where it says to check the log file /var/log/Xorg.0.log
This file has a wealth of information.
	This file was also referred in the first link given by tseliot but there I made a big mistake of not checking the file.
	Anybody having any problem in this regard must check this file as it has a great deal of information.
	Here I found that the available mode  at 1280 1024 was at 75 and so it went to this mode. Further it gives information on the supported modes from which the modeline can be constructed  refer to this link
[http://wiki.x.org/wiki/FAQVideoModes](http://wiki.x.org/wiki/FAQVideoModes) .Let this modeline be referred to as ModelineC.
	After adding this modeline the refresh rate displayed by system -> preferences ->screen resolution and the osd is 60. 
	When I checked  I found ModelineB and ModelineC to be exactly the same. But these are different from ModelineA. So Approach_1 and Approach_2 both solve the problem.Approach_1 uses suse xorg.conf and thus assumes suse also to be installed.
	Approach_2 requires you to check the /var/log/Xorg.conf file closely and obtain the modeline referring to this link.
[http://wiki.x.org/wiki/FAQVideoModes](http://wiki.x.org/wiki/FAQVideoModes)

Conclusion: 
The first link given by tseliot solves hte problem. I made the mistake of skipping the  log file.
I would like to emphasize that anybody having a similar problem should closely see the /var/log/Xorg file. And use the information given here 
to construct the modeline using this link 
[http://wiki.x.org/wiki/FAQVideoModes](http://wiki.x.org/wiki/FAQVideoModes)

Useful for: Intel integrated graphics using lcd display for refresh rate

---

### Post by mango.muncher on 2006-09-14
Hi Wonder1
I also have a 1907FP, I ran dpkg-reconfigure xserver-xorg and got things looking a whole lot better. I am still stuck on a 75 hz refresh rate, not a problem as far as visual, but it may shorten the life of the LCD??
I visited the suggested posts and  crafted a lovely modeline but things went back to fuzzy fonts.
So I ran the dpkg-reconfigure xserver-xorg again and Im good but on 75hz.
Please post your monitor section from xorg.conf to show where you inserted 60 hz info, then maybe I can see the error of my ways.
Thanks

---

### Post by wonder1 on 2006-09-17
Hi mango.muncher
Look carefully at the var/log/Xorg.O.log for supported modes
(You will see that all the details about your display are there in the Xorg.O.log  file )
I found the following lines:

(II) I810(0): Supported additional Video Mode:
(II) I810(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
(II) I810(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) I810(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0

From this I constructed the following modeline ( referrring to the guideline provided in this link  
[http://wiki.x.org/wiki/FAQVideoModes](http://wiki.x.org/wiki/FAQVideoModes)   )

Modeline 	"1280x1024" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync

I entered this information in xorg
(by 
sudo nano /etc/X11/xorg.conf )

Section "Monitor"
	Identifier	"DELL 1907FP"
	Option		"DPMS"
	DisplaySize     380 300
	HorizSync	30-81
	VertRefresh	56-76
	UseModes        "Modes[0]"
EndSection

Section "Modes"
	Identifier   "Modes[0]"
	Modeline 	"1280x1024" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
EndSection

Make sure the section  screen and subsection display has "1280x1024"
which in my case was as follows in xorg

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 945G Integrated Graphics Controller"
	Monitor		"DELL 1907FP"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection

---

### Post by mango.muncher on 2006-09-25
wonder1, that worked a treat. Not sure what went wrong with my first  attempt, but followed your config and we are now on 60hz.
Thanks.

---

