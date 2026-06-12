---
title: "Mythtv Menus are corrupted"
date: 2008-10-17
forum: Multimedia Software
---

### Post by brpadington on 2008-10-17
I installed a fresh copy of mythuntu 8.04 last night and everything went great until i installed the latest driver from ATI. The driver appears to work fine tv out looks great and the desktop is sized perfectly. The problem is whenever i start mythtv either the backend config or frontend config the display is "garbled". The images is unreadable and there appears to be two menus showing up like double vision. To me this sounds like an interalcing issue. Is there anyway i can set the video mode of mythtv back to defaults so maybe i can configure it again to work properly? Any help would be greatly appreciated.

---

### Post by brpadington on 2008-10-17
Jut to clarify the video card is a saphire x1650 pro with the component video out to my hdtv and the vga to another monitor.

---

### Post by uslacker on 2008-12-25
I"m having this same problem.  Any luck in solving it?

Do the templates need to be resized.

\\Greg

---

### Post by pondo on 2008-12-26
Same issue here with ATI graphics card on ASUS M3N Mobo.

---

### Post by whosmatt on 2009-01-10
same here with HD4870 - previously working fine with an nvidia card.

---

### Post by imanumber on 2009-01-11
I'm having the same problem.  Onboard HDMI (asus M3A78-EM motherboard).  

Desktop looks fine, but starting mythtv and the screen is exactly as described above.  

I installed mythbuntu in "safe graphics mode" and then later installed the ATI drivers.  No matter what resolution I set the display to the mythtv program doesn't display correctly.

HOWEVER, when I disable the ATI drivers and use the open source drivers mythtv works fine, only at a low res (640x480).

So, I think it is a problem between mythtv and the ATI drivers.

---

### Post by imanumber on 2009-01-11
I added this to the xorg.conf "Display" section

       Option      "ForceMonitors" "tv,none"
       Option      "NoTV" "no"
       Option      "TexturedVideo" "on"
       Option      "OpenGLOverlay" "off"
       Option      "TVFormat" "NTSC"
       Option      "UseInternalAGPGART" "no"

And I put some modes in the "Screen" section

I'm not sure which of these fixed the problem, but my menus work now!

Of course now when I am watching tv there is a double image (one on top of the other).....

---

### Post by ravay on 2009-01-19
same problem with using ATI HD4650 and a Samsung LA52A650 HDTV connectes throug HDMI.

I tried to add the options suggested by imnumber but is not working. Any idea?

---

### Post by soulless72 on 2009-02-02
Same problem here, in my case (Radeon HD 3300 on Asus M3A78-T with Samsung LE40A656) the following worked:
aticonfig --force-monitor=tmds2i,nocrt1
this adds
Option      "ForceMonitors" "tmds2i,nocrt1"
to xorg.conf in Display-Section.

I think the problem is if you connect VGA and HDMI and Xorg finds 2 Displays. Above disables VGA for ati.

---

