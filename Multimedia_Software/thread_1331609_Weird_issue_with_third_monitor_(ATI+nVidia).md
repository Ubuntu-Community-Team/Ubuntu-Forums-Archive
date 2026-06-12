---
title: "Weird issue with third monitor (ATI+nVidia)"
date: 2009-11-19
forum: Multimedia Software
---

### Post by userfriendly on 2009-11-19
Hello there,

I finally managed to get a functional desktop across three monitors on my work machine (running Ubuntu 9.10 at the moment). There are just two minor issues, one of them being a rather weird one.

The first two screens are hooked up to an nVidia GeForce PCI card, configured with TwinView, and the third screen is hooked up to the ATI Radeon PCIe card. At first I tried hooking two screens up to the ATI and only one to the nVidia, but that was no joy.

Now... the third screen seems to have a quadratic resolution, i.e. 1680x1680 (of course it only displays the first 1050 lines of it, thank the gods). I did set the mode in xorg.conf explicitly to 1680x1050 at first. Then removed that line. In both cases the resolution remained square-like. <.<

It looks like this on a screen shot: [[IMG]http://img691.imageshack.us/img691/8130/weirdtriplehead.th.jpg[/IMG]](http://img691.imageshack.us/i/weirdtriplehead.jpg/)

The other issue I have is with TwinView... maximising only works over both screens? Really? That's kinda sucky. <.< I'm sure I'm overlooking something, right? How can I get windows to maximise to only one of the two screens on the nVidia card?

Other than that... three screens == teh pure awesome! :p

---

### Post by userfriendly on 2009-11-26
A wee little bump here. Does anyone have an idea what is wrong with that third screen?

---

### Post by userfriendly on 2009-12-16
Still need help with this. :(

---

### Post by userfriendly on 2010-02-09
I managed to solve the resolution issue by adding the "Virtual" option to the "Display" sub-sections of two of the "Screen" sections. The displayed resolution now matches the resolution of the monitors. I'm also using the VGA out of the ATI card instead of the one on the nVidia card. So it's like this at the moment: screen 1 on nVidia DVI out, screen 2 on ATI DVI out, screen 3 on ATI VGA out.

However, this still leaves me with the problem that I can maximise only on the first of the three screens - maximising a window on either of the other two will result in the window resizing across both of them. Do not want.

I did manage to work around that (by giving all three "Screen" sections the same "Virtual" value), but that solution left me with a weird issue. It doesn't show up on screen shots, so I had to use Gimp to sort of recreate what is displayed:

[[IMG]http://img214.imageshack.us/img214/2364/screenshotul.th.jpg[/IMG]](http://img214.imageshack.us/i/screenshotul.jpg/)

Please note that it doesn't look exactly like the observed effect, I'm not a Gimp master. However, it should be sufficient to illustrate the issue, which seems to be that every odd row of parts of the second screen (ATI DVI out) is mirrored on the third screen (ATI VGA out), and vice versa. The red line indicates the border between screen 2 & screen 3.

I'm providing the xorg.conf files that I'm using or have used with varied degrees of success. Lines that are commented out didn't seem to make any difference.

1. My current xorg.conf - no stripes issue, but maximising works correctly only on the first screen, maximising a window on either of the other two will result in the window resizing across both of them.

[http://pastie.org/816334](http://pastie.org/816334)

2. The xorg.conf with correctly working maximising on all screens but with the weird stripes issue. Since I suspected that it would be something related to how the monitors are driven by the outputs, I've tried specifying the "ModeLine" options, but that only changed slightly what was being mirrored where (stripes column a bit higher or lower, or two stripes columns slightly apart from each other), it did not do away with the issue.

[http://pastie.org/816331](http://pastie.org/816331)

---

