---
title: "Help - fglrx driver not working for HD 2900 Pro Video Card - 64 bit"
date: 2008-01-06
forum: Multimedia &amp; Video
---

### Post by tosk1 on 2008-01-06
I'm new to Linux, and I have not been able to get my video card to display at 1440x900.

I have:

- Sapphire Radeo HD2900 Pro Video Card
- AMD Athlon 64x2 x2 5600" Dual Core AM2 CPU.
- Gutsy Kubuntu 7.10
- Acer AL1916W (Widescreen Monitor)

I have installed the fglrx drivers as described on this forum and the driver option now shows up when I execute:

dpk-reconfigure xserver-xorg

When I select  the fglrx driver and set the resolution for 1440x900 my display does not work.

Does anyone have any suggestions?

Thank you for any help.

---

### Post by kimothy1987 on 2008-03-21
Hi. I got the same graphics card. The only way i got it working with fglrx, is with version 7.11 of the amd ati drivers. Then i edit xorg.conf file to change the driver.

Try that.

---

