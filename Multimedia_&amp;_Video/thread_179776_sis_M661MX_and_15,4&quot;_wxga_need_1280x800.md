---
title: "sis M661MX and 15,4&quot; wxga need 1280x800"
date: 2006-05-20
forum: Multimedia &amp; Video
---

### Post by awakatanka on 2006-05-20
I got a acer aspire 3633lc that has a sis M661MX vga and a 15,4" wxga tft screen.

It has the possibilty to have a 1280x800 resolution but i can't get it at that resolution.

How to get it at that resolution. 

Under KDE i can select sis driver but not that type it isn't in the list. As screen i can select a 1280x800 screen but have no option to set it to that resolution because no sis driver in the list have that option.

---

### Post by garwind on 2006-05-30
Hi !
I have an acer laptop, (3002) and i had the same problem as you.
You must go in your /etc/X11/xorg.conf file and edit this like mine :
> 
Section "Screen"
	Identifier	"Default Screen"
	Device		"Carte vidéo générique"
	Monitor		"Ã‰cran gÃ©nÃ©rique"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

you can reduce the entire "screen section" like the upper one. 
And you'll be able to select 1280x800 resolution !

---

