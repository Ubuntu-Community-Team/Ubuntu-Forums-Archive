---
title: "DVI to HDMI overscan woes"
date: 2009-08-16
forum: Multimedia Software
---

### Post by Chireru on 2009-08-16
I've been upgrading my home theatre setup.  It is now:

Panasonic TC-P50S1 Screen <=HDMI=> Denon AVR789 Receiver <=HDMI-to-DVI=> Ubuntu boxes (nVidia graphics cards; ubuntu, mythbuntu).

The problem is that I'm getting overscan; the top, bottom and side pixels are being cut off.  Not exactly sure how many, say, 25-30.  Enough that I can't see panels anymore, and half-icons.

It appears that there is a nice easy tool in Windows to fix this in the nvidia control panel, but sadly, this option doesn't exist in the Linux nvidia-settings app.

Problems:
- Overscan
- EDID info not being reported properly [Solved]


Solutions:
- I dumped the EDID info to file via the nvidia-settings tool, and added a CustomEDID option to xorg so it sees it properly now. (Solved)

- Use a windows tool (Phoenix EDID editor) to change the EDID data to allow you to use a smaller resolution.  (The tool didn't think my EDID data file was valid; parse-edid says otherwise).

- Plug directly into the TV.  (EDID data still wasn't detected by X, ddcprobe, or get-edid; still overscanned).

- Told the Denon to pass through the connection without upconversion.  (No change).  Told the Denon to pass the connection upconverted but leaving the format alone.  (No change).

- Tell the TV to use "Full" (or "Just Scan" or similar). (Done. Setting to any format other than "Full" just cut more off).

- Use Modelines to hand the TV less data (I've tried a bunch of this...  my latest attempt is running fine (confirmed using `xrandr -q --verbose -display :0.0`) at 1208x679@60, but the picture looks the same as 1280x720.. I assume the TV is stretching it somehow.  Directly plugged into the TV, it's reporting 720p connection / FULL format [tried other format options too]).

- Other xorg options: Modevalidation, ExactmodeTimingsDVI, UseEDID, UseEDIDFreqs, etc.

As I understand it, the problem is that the TV shows less pixels than advertised, which is an industry-common activity, and the nVidia driver doesn't have a method to compensate for this.

Does anyone have another idea that I can try?  Miracle cures?  Incantations?  Insults that the xorg.conf parser will accept?  I'm running out of ideas here, and a little ticked that it's a 10 second fix in Windows.

EDIT: I should also note that it's not just X that's cut off... BIOS, loading screens, virtual consoles, etc are all overscanned/cut off.

---

### Post by xyphur on 2009-08-17
Specifically, what type/family of nVidia graphics cards are being used? Some aren't capable of HDTV output, even when using DVI->HDMI cables (I've dealt with this on a previous system - it's what prompted me to upgrade the card)

I think it has something to do with the TV's expected resolution not matching any entires in the card's onboard table of valid resolutions, so the card just drops back to the next closest valid one (which is usually in the wrong aspect ratio as well)

---

### Post by Chireru on 2009-08-17
My most up to date card is a nVidia 6600GT. It detects and uses 1920x1080 just fine, when given a dumped EDID.

The other card is a FX5200, and it detects and uses 1280x720 just fine (again, when given a dumped EDID).

However, they both overscan by quite a bit all the way through the boot process to X.  One has a dual boot to windows, where I can change it in the nvidia driver settings (but of course, the boot is still overscanned).

Am I to understand that upgrading graphics the cards will either make the overscan compensation option appear in nvidia-settings?  Or will it somehow just make everything work?  Or ?

I should also note that these systems are AGP-based, so an upgrade to new card basically means buying two new systems.

---

### Post by mcduck on 2009-08-17
The correct resolution for that display would be 1920x1080. Using non-standard (or pretty much any other than the native) resolutions will often cause badly aligned or otherwise wrong results with LCD displays. And being mainly a TV, not a computer monitor, the display will most likely have very limited support from scaling different resolutions.

> As I understand it, the problem is that the TV shows less pixels than advertised, which is an industry-common activity, and the nVidia driver doesn't have a method to compensate for this.

Actually it's quite the opposite, most TV's sold as HD-ready (meaning 720P resolution, 1080x720) actually use 1366x768 panels since that's what the panel manufacturers get when they cut the panels, using the correct (smaller) resolution would produce leftover pieces. The nasty thing about this is that even the resolution these TV's will most of the time use has to be scaled instead of being able to use the panel's native resolution..

Anyway, try using the 1920x1080 resolution, with the pixel-perfect display mode ("Full" or whatever your TV manufacturer calls it). Getting bad picture during bootup is quite normal, TV's weren't made to display that kind of resolutions, some will support them, some won't.

(Overscan in it's true meaning doesn't really happen on LCD displays. What you are seeing is simply your displays inability to display the resolution you are using or to scale it to the full screen size correctly. Remember that every time you feed the display any other resolution than the panel's native resolution, the display has to scale the image..)

---

### Post by Chireru on 2009-08-17
> **mcduck said:**
> Actually it's quite the opposite, most TV's sold as HD-ready (meaning 720P resolution, 1080x720) actually use 1366x768 panels since that's what the panel manufacturers get when they cut the panels, using the correct (smaller) resolution would produce leftover pieces. The nasty thing about this is that even the resolution these TV's will most of the time use has to be scaled instead of being able to use the panel's native resolution..
Interesting.

> Anyway, try using the 1920x1080 resolution, with the pixel-perfect display mode ("Full" or whatever your TV manufacturer calls it). Getting bad picture during bootup is quite normal, TV's weren't made to display that kind of resolutions, some will support them, some won't.

(Overscan in it's true meaning doesn't really happen on LCD displays. What you are seeing is simply your displays inability to display the resolution you are using or to scale it to the full screen size correctly. Remember that every time you feed the display any other resolution than the panel's native resolution, the display has to scale the image..)
I have tried 1920x1080 on one of the cards, it was still cut off.  Flipping through the different format modes, "Full" shows the most, but still cuts off pixels near the screen edges.

Since it was still cut off when I send it a lower, 1208x679 resolution, directly to the TV.  This confirms that the TV is scaling it on me (so regardless of the modelines I use, nothing will work, it will all be resized by the TV).  (Should really test this on 1080p instead of 720p, but I think I'll get the same result).

So this means that I need to send it blank pixels around the border..  when I get home, I'll have to toy with Xorg's Virtual and ViewPort options, see if they will accept a smaller resolution than the Mode, effectively causing a 1920x1080 signal to be sent, but the actual desktop size to be smaller.  The man pages don't mention any "virtual size > resolution" restriction.  Fingers crossed.

(The other video card doesn't support 1080p, instead it shows at 1280x720, which the receiver upconverts to 1080p and sends to the TV).

---

### Post by Chireru on 2009-08-17
Hang on, I may be an idiot.  Apparently my TV has an option obscurely named "HD Mode", which, by default is at "HD Mode 1", which does a ~5% overscan.  If I change this to "HD Mode 2", it does a 0% overscan.

It was greyed out in the menu when I initially configured the TV, so I'll have to RTFM and figure it out how to change it, but it looks like I've found my culprit.  We'll see tonight.  Either way, thanks for the help.

---

### Post by mcduck on 2009-08-17
> **Chireru said:**
> Hang on, I may be an idiot.  Apparently my TV has an option obscurely named "HD Mode", which, by default is at "HD Mode 1", which does a ~5% overscan.  If I change this to "HD Mode 2", it does a 0% overscan.

It was greyed out in the menu when I initially configured the TV, so I'll have to RTFM and figure it out how to change it, but it looks like I've found my culprit.  We'll see tonight.  Either way, thanks for the help.

Yes, that sounds like the reason for your problem, as, like I said, LCD displays don't have any actual overscan (it's feature of CRT displays) and sending 1920x1080 picture to 1920x1080 panel should produce perfect picture.

---

### Post by Chireru on 2009-08-17
Yup, that did it.  Unfortuntely, this TV will only allow that mode to be set for 1080p input...  720p is stuck chopped off.

---

