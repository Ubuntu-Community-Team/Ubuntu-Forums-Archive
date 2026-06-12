---
title: "VGA monitor doesn't work with dongle"
date: 2010-02-18
forum: Multimedia Software
---

### Post by sparky8251 on 2010-02-18
I am experiencing a strange problem. I have two vga monitors and a ATI Radeon HD 3300 embedded on my motherboard. My embedded graphics card has a vga and dvi output. When I plug my monitors in (one uses a dvi to vga dongle) only the one with out the dongle gets a signal. I can swap which monitor uses the dongle and still only the one that does not use the dongle gets a signal (both monitors work, only if they are not using a dongle). Both Ubuntu and Windows are having trouble displaying video, but no trouble detecting the monitors (display settings show both monitors but do not tell me good resolutions for them). My friend has a different dvi to vga dongle, his only has about half of the dvi pins while mine has all the pins. Could the problem be that my dongle has all the dvi pins, or is it something else? Any help would be appreciated.

---

### Post by sparky8251 on 2010-02-21
Bump. Anyone? I tried the dongle with one of my monitors on his computer and it worked. Any ideas?

---

### Post by me13221 on 2010-02-21
I am in a similar situation-- I have an embedded Radeon 3200, also with DVI and VGA.  I have 2 video devices and I want them both to display the same thing (i.e. "mirrored", not xinerama).  My monitor has both VGA and DVI in.  When I plug a VGA cable into the VGA port, the display works.  When I plug the DVI cable into the DVI port, it does not work-- the monitor doesn't find a signal.

I'm using the 'vesa' driver, since the radeon driver overheats my board, and fglrx doesn't work.

Is there some way to 'activate' the port or to choose which port is activated?

@sparky 8251 -- What kind of dongle is it?  VGA-to-DVI converter?  does it have female-VGA and male-DVI or the other way around?

---

### Post by sparky8251 on 2010-03-09
The part of the cable that plugs into the computer is VGA and converted by the dongle to DVI. The weird thing is that this also happens on my Windows partition with the manufacturers driver.

---

### Post by me13221 on 2010-03-15
> **sparky8251 said:**
> The part of the cable that plugs into the computer is VGA and converted by the dongle to DVI. The weird thing is that this also happens on my Windows partition with the manufacturers driver.


I can't quite tell what works and what doesn't from your posts.  It sounds like your dongle goes with the VGA port on your motherboard, and that either monitor plugged into the DVI port works, but either monitor plugged into the VGA port (via the dongle) does not work.  This suggests that your VGA port does not work.

Does the Monitor report the source of the signal that it's receiving?  i.e. 'Digital' or 'Analog'?  The DVI connector can include both digital and analog signals, but the VGA connector is only analog.

---

### Post by me13221 on 2010-03-15
> **me13221 said:**
> I am in a similar situation-- I have an embedded Radeon 3200, also with DVI and VGA.  I have 2 video devices and I want them both to display the same thing (i.e. "mirrored", not xinerama).  My monitor has both VGA and DVI in.  When I plug a VGA cable into the VGA port, the display works.  When I plug the DVI cable into the DVI port, it does not work-- the monitor doesn't find a signal.

I'm using the 'vesa' driver, since the radeon driver overheats my board, and fglrx doesn't work.


By the way, I figured out that the vesa driver does not support DVI out.  So it sounds like the Radeon 3200 is not supported by the opensource driver.  Either way, I'm just using vesa with a VGA splitter cable and no graphics acceleration.  sad.  but at 800x600, satisfactory.

---

