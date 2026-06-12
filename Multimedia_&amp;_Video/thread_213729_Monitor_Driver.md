---
title: "Monitor Driver?"
date: 2006-07-11
forum: Multimedia &amp; Video
---

### Post by mjpatey on 2006-07-11
I have a Dell 1801FP monitor, and have just installed Ubuntu.  Things are looking a little fuzzy, mostly in the area of text.

I realize that the font set in Ubuntu is different than in Windows, so I've downloaded the MS TrueType font pack, and am  using those fonts, which I do prefer so far.

But still, text is fuzzy, not quite as sharp as in Windows.

I was wondering if it could be the monitor driver.  When I go into Device Manager, there is a listing for my ATI video card (Radeon 9200), but no way to go in and tweak it as in Windows, and no way to select a particular monitor.

Anybody know what I need to do to improve my screen output?

Thanks!

-Mark

---

### Post by scxtt on 2006-07-11
have you got the drivers working for your 9200? -- do you know which driver it's currently using?

---

### Post by mjpatey on 2006-07-11
Honestly, I'm not sure how to tell.  In the Device Manager, it doesn't give me much info, unless I'm missing something.

Where do I go to find driver info?

-Mark

---

### Post by scxtt on 2006-07-11
check your /etc/X11/xorg.conf file - there should be a line that says "Driver" under the "Device" section ... for example:```
Section "Device"
        Identifier  "ATI Graphics Adapter 0"
[color=red]        Driver      "fglrx"[/color]
        Option      "(null)"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        Option      "DesktopSetup" "horizontal"
        Option      "UseInternalAGPGART" "off"
        BusID       "PCI:1:0:0"
EndSection
```that's what i have for my ATI X850Pro ...

---

### Post by mjpatey on 2006-07-11
Thanks for that info!  Here's what mine says...

Section "Device"
	Identifier	"ATI Technologies, Inc. RV280 [Radeon 9200]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

...and below that is actually a bunch of stuff about the Dell 1801FP monitor, too.  So it looks like things are as they should be, right?  It still looks smeared, though.

I wonder if this isn't a hardware or driver issue at all, but rather a lack of thoroughness on my part (in tweaking the font settings)...

-Mark

---

### Post by scxtt on 2006-07-11
i think the ati driver is pretty generic (since ATI isn't to helpful in supplying drivers for linux [they're getting better]) ... AFAIK, you should be able to get fglrx working w/ your card (same driver that i use for my X850Pro) ... i notice marked improvement in clarity when i install (defaults to using vesa/ati) as compared to after i get fglrx working ... it's worth a shot - it'll also give you 3D acceleration ...

---

### Post by mjpatey on 2006-07-11
Scxtt-

Thanks for all the info!  I'll try installing fglrx and see how it goes.

-Mark

---

