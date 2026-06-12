---
title: "[SOLVED] Need Help Outputting To Composite Via DVI"
date: 2007-12-27
forum: Mythbuntu
---

### Post by ctpaterson on 2007-12-27
I've got my MythBuntu running, using an XFX nVidia GeForce 8400GS card.  I want the video to go out the DVI port, then using the DVI-to-Composite adapter I had for my Mac Mini, connect it to the composite video input of my television.  I've been playing with the xorg  settings I've seen about, and while I am seeing changes, I'm ultimately left with a black screen.

Here's my xorg.conf; can anyone provide some advice?

> Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
    Option         "DPI" "100x100"
    Option         "UseEvents" "1"
    Option         "AddARGBVisuals" "1"
    Option         "AddARGBGLXVisuals" "1"
    Option         "NoLogo" "1"
    Option         "UseDisplayDevice" "TV"
    Option         "ConnectedMonitor" "CRT,TV"
    Option         "TVOutFormat" "COMPOSITE"
    Option         "TVStandard" "NTSC-M"
    Option         "TVOverScan" "0.6"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select" "1920x1080" "1280x720" "1024x768" "720x480" "800x600" "640x480"
    EndSubSection
EndSection



---

### Post by theacoustician on 2007-12-27
> **ctpaterson said:**
> I've got my MythBuntu running, using an XFX nVidia GeForce 8400GS card.  I want the video to go out the DVI port, then using the DVI-to-Composite adapter I had for my Mac Mini, connect it to the composite video input of my television.  I've been playing with the xorg  settings I've seen about, and while I am seeing changes, I'm ultimately left with a black screen.

Here's my xorg.conf; can anyone provide some advice?

DVI to composite(single yellow RCA plug)?  Are you sure you don't mean component (3 RCA plugs colored red, green, blue)?

If you mean composite, then the answer is simple.  Assuming that the converter will take the analog portion of DVI-I and mux it together to a single signal, you'll only get picture on the screen when the output is set to 640x480.  Depending on how fussy the monitor is, you might even have to set the signal for interlacing or at 30Hz to help trick the display into showing video.

However, I wouldn't assume that the adapter would work at all.  Apple states its only for use with computers with a ATI X1900 XT graphics card, so I assume there's a reason for that.  All the 8400GS series already have a s-video port out.  Its quite easy to convert s-video to composite.  Why don't you try that instead?

---

### Post by ctpaterson on 2007-12-27
> DVI to composite(single yellow RCA plug)? Are you sure you don't mean component (3 RCA plugs colored red, green, blue)?

It's composite...single yellow.

It's an inherited Television requiring composite inputs because the coax connection flakes out.  I'm not sure component was invented when it went on the market.  ;>

> If you mean composite, then the answer is simple. Assuming that the converter will take the analog portion of DVI-I and mux it together to a single signal, you'll only get picture on the screen when the output is set to 640x480. Depending on how fussy the monitor is, you might even have to set the signal for interlacing or at 30Hz to help trick the display into showing video.

I think that's what my resolution is at - but I'll go double check.

> However, I wouldn't assume that the adapter would work at all. Apple states its only for use with computers with a ATI X1900 XT graphics card, so I assume there's a reason for that.

Fair point about whether it would work.  I remember now that that was a note when I bought it - but my mind has disregarded it in the mean time.

>  All the 8400GS series already have a s-video port out. Its quite easy to convert s-video to composite. Why don't you try that instead?

Lack of an adapter, and I haven't dressed to go out yet.  ;>  If I can find a relatively cheap adapter at circuit city or something before I can tweak things to work here, then I'll grab it.  For now, I'm just looking for a solution with the hardware I have.

Thanks **very** much for such a quick reply.  I'll try the resolution and let you know.

Cheers.

---

### Post by ctpaterson on 2007-12-27
Setting the resolution to 640x480 (making it the only Mode in xorg) doesn't seem to have done the trick.

---

### Post by ctpaterson on 2007-12-28
I picked up an svideo to composite adapter (actually, I picked up a composite to svideo adapter - but reasoned that it would work both ways), and adjusted my xorg accordingly...

> 
Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
    Option         "DPI" "100x100"
    Option         "UseEvents" "1"
    Option         "AddARGBVisuals" "1"
    Option         "AddARGBGLXVisuals" "1"
    Option         "NoLogo" "1"
    Option         "UseDisplayDevice" "TV"
    Option         "TVOutFormat" "SVIDEO"
    Option         "TVStandard" "NTSC-M"
    Option         "TVOverScan" "0.6"
EndSection


The result; success -- or at least something really damn close.  The myth screen seems to be slightly larger than the real estate on my television -- when I'm reconfiguring things the Cancel, Back, and Next buttons are frequently off-screen.  Also, there's some refresh scrolling on the screen -- but this is much better than the black screen/garbled mess I was getting otherwise.

Thanks very much for the help.

---

### Post by theacoustician on 2007-12-29
> **ctpaterson said:**
> I picked up an svideo to composite adapter (actually, I picked up a composite to svideo adapter - but reasoned that it would work both ways), and adjusted my xorg accordingly...



The result; success -- or at least something really damn close.  The myth screen seems to be slightly larger than the real estate on my television -- when I'm reconfiguring things the Cancel, Back, and Next buttons are frequently off-screen.  Also, there's some refresh scrolling on the screen -- but this is much better than the black screen/garbled mess I was getting otherwise.

Thanks very much for the help.
This is because analog TVs have some overscan.  If you want to get the image to perfectly fit on your screen, try a resolution like 525x394.  That's typically much closer to what a TV actually displays, but there's variance model to model.  Congrats on getting it running.

---

### Post by ctpaterson on 2008-01-01
> **theacoustician said:**
> This is because analog TVs have some overscan.  If you want to get the image to perfectly fit on your screen, try a resolution like 525x394.  That's typically much closer to what a TV actually displays, but there's variance model to model.  Congrats on getting it running.

Well, I tried setting the resolution to that - but it didn't seem to help.  After some more googling about, and being open to the kind of silliness that one only attempts at nearly 2am - I decided to start playing with the settings in the Utilities/Setup -> Setup -> Appearances menu.

I tweaked and tweaked, and now have a GUI width of 900px, a height of 675px, an X offset of 77 and a Y offset of 50.  This makes no sense to me - but does result in a screen with everything on it.  This is either very clever, or (more likely) I have seriously pooched the resolution and this is some crappy coping mechanism.

For now, to bed - though of course any further wisdom would be appreciated.  I'm just happy I can now see what channel I'm changing to.

---

