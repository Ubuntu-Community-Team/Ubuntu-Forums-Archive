---
title: "xorg.conf ignored?"
date: 2008-05-18
forum: Multimedia Software
---

### Post by han555 on 2008-05-18
I am trying to set up two screens in my xorg.conf.  I want the same desktop displayed on both, but different resolutions on each.  What I'm trying to achieve is a second screen (my projector which is hooked up to the second out on my ati video card via vga cable) that is used only for fullscreen video, and my primary desktop that is used for everything else.  I originally tried to do this using the fglrx-control ui.  All I could achieve with this was cloned output with the same resolution -- which caused the resolution on the projector to be way too high.  So I disabled clone mode and tried to do this all through xorg.conf.  What I don't understand is that fglrx-control did not seem to modify my xorg.conf to enable/disable clone mode.  Then, when I disabled clone mode via fglrx-control, nothing I did in xorg.conf could enable display on the projector.  When I enabled it, nothing I did in xorg.conf could disable display on the projector.  I eventually completely removed fglrx-control.  At the time I removed it, clone mode was enabled.  Now, nothing I do in xorg.cong seems to have any affect on this -- the display is always cloned and any related xorg.conf setting seem to be completely ignored.  Anybody have any insight?

---

### Post by garyedwardjohnston on 2008-05-18
You are probably more knowledgable than I, but messing with this file is dangerous.

System > Preferences > Screen Resolution

worked for me.

---

### Post by han555 on 2008-05-18
The Screen Resolution dialog does not give me options to change two screens.  It just affects my main desktop.  I'm more concerned with why any changes to xorg.conf are seemingly ignored after setting up cloned desktop via fglrx-control.

---

### Post by han555 on 2008-05-19
I also noticed the same thing if I use the clone setting in System > Preferences > Screen Resolution.  It clones the output but does not actually change my xorg.conf.  Where are these settings being stored?  Is there a way to force only xorg.conf to be used?

---

### Post by aeiah on 2008-05-19
could you post your xorg.conf? im pretty sure its still reading your xorg.conf. i dont know for sure, but i think xorg will just describe what resolutions are available. if more than one is set, or if through guesswork linux things more are available (usually lower resolutions) then it will give you these choices through the change resolution control panel.

anyway. im not on my pc right now but i was messing with resolutions recently. basically i was outputting twice to the same tv in clone mode, one through vga (max is 1024x768) and one through dvi-hdmi (1280x720). in my case, when i viewed the cloned output through the vga, there was a bit to the right that was cropped off, and when i viewed it through hdmi, the bottom was cropped off. its obvious to see why, and this is something that you'll have to deal with in some way or other when setting up your two different outputs if you want it to be cloned.

when i get home ill see what my xorg says. you'll have to delve into using the metamode string in your xorg.conf file. this is an example one for nvidia. there must be an ATI version somewhere:

Section "Device"
        Option "TwinView" "yes"
        Option "TwinViewOrientation" "Clone"
        Option "MetaModes" "1680x1050,1024x768"

Section "Monitor"
        Option "MonitorLayout" "CRT,LFP"

---

### Post by aeiah on 2008-05-19
this might help: [http://gentoo-wiki.com/HOWTO_Dual_Monitors](http://gentoo-wiki.com/HOWTO_Dual_Monitors)

---

### Post by aeiah on 2008-05-19
perhaps something like this will work. backup xorg.conf obviously, and see if and what your control panel has added to xorg.conf and whether it'll conflict or is useless

```

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "DesktopSetup" "clone"
        Option      "PairModes" "1440x900+1280x1024"
EndSection


Section "Screen"
        Identifier "aticonfig-Screen[0]"
        Device     "aticonfig-Device[0]"
        Monitor    "aticonfig-Monitor[0]"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                #This virtual is for 2 monitors, a 1440x900 next
                # to a 1280x1024
                Virtual   1440 1024
                Depth     24
        EndSubSection
EndSection


```

you'll need both of your devices specified as per the gentoo wiki i posted a link to though.

---

### Post by han555 on 2008-05-19
The problem is not so much in the resolutions (although that is a separate problem) it's that if I set clone up in fglrx-control and then uninstall fglrx-control and restart X, my xorg.conf does not define any clone options but the display is still cloned.  So if my xorg.conf isn't setting it, where is it being set?  And the opposite is true.  If I disable clone via fglrx, nothing I do in my xorg.conf will enable cloned output.  It just pays attention to the control panel settings (even after I uninstall it) and not to my xorg.conf.  However, if I set resolutions in the xorg.conf, it does pay attention to those, just not to anything where I define multiple screens or cloned output.  I have to go to work now.  Will chack back later.  Thanks!

---

### Post by aeiah on 2008-05-19
as i dont own an ATI card, im not too sure, but i know that with my card, an nvidia 7800 gt, it shoves out a cloned output by default on all channels (both dvi ports and the composite / tv in style port) just for the hell of it.

i cant really answer your question, but why does it matter? set it to clone and then modify your xorg.conf to pipe the two different resolutions out to your monitor and projector

---

### Post by han555 on 2008-05-19
The only reason I think it matters is because I'd like to have control over this in my xorg.conf so I can make changes to the setup if necessary.  I'll definitely give your suggestions a try when I get home later tonight though.  thanks!

---

### Post by han555 on 2008-05-22
ok, I did get things working using a 2 screen setup.  Meaning, I have 2 screens and two devices defined in my xorg.conf.  I believe this is the setup I want -- should give me a main desktop on my pc monitor and then allow me to put video full-screen on the second while still working on the first.  The only problem I have now is that compiz has been disabled in both (ideally I'd like it disabled on the second screen so it doesn't interfere with the video).  I don't even have window borders or menubars on any of my windows.  They all just open in the upper left hand corner and have no "chrome" and cannot be moved or resized.  Any ideas?

---

