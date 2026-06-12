---
title: "DVI doesn't work with ATI cards??"
date: 2006-06-15
forum: Multimedia &amp; Video
---

### Post by dangeroushoals on 2006-06-15
Hey all-
I love my new LCD, but it only works on VGA!?!?:confused: 
I get terrible screen flicker at 1680x1050, but only when I'm using my Radeon 9200's DVI out, *not* the VGA.  

Here's my story:
As soon as I got my new viewsonic 20.1" a few days back I finally did away with breezy and went for dapper.  I expected some install problems (and indeed the live CD wouldn't work even on safe graphics mode), so i used the alternate CD.  Armed with the abundance of info on getting ATI cards to work I figured i'd be just fine.  Man was I wrong...
After following the first method in this popular link,
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)
the computer would boot but flicker madly when my screen was at native res.  What's more, glxgears and fglrxinfo would both spit errors like "[fglrx] API ERROR: could not register entrypoint for...", but about 2 screenfulls of them, and I had no opengl info in the ATI control panel.  

Then I looked at my xorg.conf and found no mention of "fglrx", and even more confusingly _the screen section had no resolution listed higher than 1024x768, but I was clearly at 1680x1050_ (believe me).  

I can mention all the stuff I tried if anyone thinks they can help, but in short, every xorg.conf that I tried would crash X.  I did manage to use this link to revert my driver and get openGL, but the missing 1680x1024resolutions still baffles me.  

[http://www.ubuntuforums.org/showpost.php?p=1108696&postcount=26](http://www.ubuntuforums.org/showpost.php?p=1108696&postcount=26)

I'd love some advice here on my "first cup", if anyone has an idea of something to try.

---

### Post by dangeroushoals on 2006-06-16
I forgot to include this earlier:
The resolution section is -
Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    28.0 - 51.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

and the xorg.conf "monitor" section looks like this-
Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    28.0 - 51.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection


Adding to my confusion, using glxgears With a 9200se, doesn't 870 fps seems a bit weak?

---

