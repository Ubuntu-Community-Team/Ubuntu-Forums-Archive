---
title: "xerox 6510 driver woes"
date: 2019-03-01
forum: Multimedia Software
---

### Post by isetome on 2019-03-01
Hi
Recently bought a Xerox phaser 6510 color laser, one of the reasons being that xerox provides linux drivers. 

I installed the printer through the system settings dialog, choosing the driver that Ubuntu recommended (Xerox Phaser 6360DX Foomatic/Postscript, 6510 wasn't on the list). 
Works excellent except for some reason the cyan turns out kind of greenish when i print, EXCEPT for on the test page printed through the printer options dialog. So i know that Ubuntu can tell the printer to print pure cyan.  

Then i downloaded the phaser 6510 driver from the Xerox website, and installed the .deb 
Which did absolutely nothing at all. 
There is no .ppd inside the package, i have no idea where the driver even was installed, and it's not added to the list of possible printers to choose from when installing the printer driver through the dialog. 

I also downloaded the windows drivers to pick them apart looking for a .ppd but no luck so far. 

When reading about color problems i read someone suggesting changing the printer color mode to CMYK in printer properties > options. 
The Xerox Phaser 6360DX Foomatic/Postscript driver does not have this option, so i tried the Xerox Phaser 6360DX - CUPS+Gutenprint v5.2.11 driver instead.
This does have color mode options, but the only options as grayscale & reversed grayscale, like a dystiopan french indy movie... 

To summarize my questions: 
1) where did that driver from the xerox website go after i installed it? 
2) why does the CUPS+Gutenprint only have grayscale options? 
3) does anyone have a .ppd for the phaser 6510 laying around gathering dust? 

Thanks in advance!

---

### Post by cdrkeen on 2019-10-01
If you still need this...Here you go.

IIRC I pulled these from the Windows driver package provided on the Xerox support site. As I recall, the original 6510 PPD was unusable due to a minor syntax error or two. :roll: I fixed those; this is the corrected copy. (I don't recall whether the 6515 file was edited, OK as-is, or neither; *caveat emptor*.)

In regular use about six months now...haven't noticed any problems yet. Hope it helps.

---

### Post by hjo2 on 2020-07-23
Thank you very much, that also helped me a lot!

---

