---
title: "Intel i810 performance fix"
date: 2007-08-19
forum: Multimedia &amp; Video
---

### Post by lavinog on 2007-08-19
For those that have the intel i810 chipset, you may or may have noticed the poor performance.
for example firefox seems extremely slow to scroll and CPU loads can average over 1.00 most of the time.

The way I was able to fix this was to change the bbp from the default 24 to 16
I got the hint from intel's website:
[http://support.intel.com/support/graphics/intel810/sb/cs-009118.htm#POS13]("http://support.intel.com/support/graphics/intel810/sb/cs-009118.htm#POS13")
> Does the vesafb frame-buffer module work on the Intel® 810 and Intel® 815 Chipset Families?
No. The vesafb module can only make use of linear VESA modes. The Intel® 810 and Intel 815 chipset families use banked modes and therefore, cannot boot into a frame-buffer. It would be possible to add banked mode support to the vesafb driver, but as of yet there are no plans to do so. The vga 16 color frame-buffer available in recent Linux* kernels does function properly and can be used in place of the vesafb frame-buffer.


To fix this:
```
gksudo gedit /etc/X11/xorg.conf
```

under Section "Screen":
change DefaultDepth to 16


This will give you worse color, but much improved performance

---

### Post by timmay on 2008-01-01
That's not a very good solution to this problem! Graphics performance was fine before upgrading to 7.10 (which I now wish I hadn't bothered doing) so why has the performance depreciated so much with the latest version of Ubuntu?

Are there any better ideas out there?

PS just tried changing to 16 bit and it messed up and was unusable.

---

### Post by lavinog on 2008-01-24
are you using an i810 chipset?
what are your computer specs
the computer i had to do this on was running feisty
it is a hp p3 with integrated 810i video

---

### Post by RiTarDid on 2008-01-25
i agree that changing the color depth is not a very good solution.....my i810 on gutsy really sucks but is theoretically "supported" by the native drivers.....personally, i'm looking for a new driver, not a "turn this off to make that better" solution.

---

### Post by lavinog on 2008-01-25
I think the problem is with the video card though.
note intel's response
I guess using a non-frame buffer driver would be a solution...so as it looks the only solutions would be to go 16bit, don't use the frame buffer driver...or of course replace the card.

your response seems to say that the problem is with gusty though...have you tested your card on other distros?

at least you have the option to use it in 16 bit
A friend of mine had to buy a new video card because their cd burning software in windows refused to run because it wasn't a direct X 9 card...why cd-burning requires directx 9 is beyond me.

---

