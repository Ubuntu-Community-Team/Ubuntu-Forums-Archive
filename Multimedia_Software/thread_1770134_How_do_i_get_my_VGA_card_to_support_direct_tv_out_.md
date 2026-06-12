---
title: "How do i get my VGA card to support direct tv out through a rca cable?"
date: 2011-05-28
forum: Multimedia Software
---

### Post by evantk on 2011-05-28
[FONT=Arial][COLOR=black] I am new to Ubuntu but[/COLOR][/FONT][FONT=Arial][SIZE=1][COLOR=black] i must say t[/COLOR][/SIZE][/FONT][FONT=Arial][COLOR=black]hat it is absolutely awesome. I just purchased a[SIZE=1] "VGA Adapter to TV S-Video RCA Out Cable for PC Video" but it isn't working. [/SIZE]How do i get my VGA card to support direct tv out through a RCA cable?[/COLOR][/FONT]

---

### Post by BicyclerBoy on 2011-05-28
Need to know what the video card is & what driver you are using...
May help to state the adapter & TV model just for completeness.
(The TV & adapter may support progressive scan etc)

To get this arrangement to work you need to tell the video driver that there is no EDID data & need to state TV format & which wired port to connect to.
Can set the video mode (resolution & refresh & interlace)

Sometimes the adapters are not auto-detected on the wired ports (video card).

The notation for all this depends on the video driver & the direction the wind is blowing.
My personal experience includes nvidia cards only.

---

### Post by papibe on 2011-05-29
I brought and config one those little things for my sister in law. It worked right out of the box.

The only thing I would recommend is to start with a low resolution. Start with 1024x768, and keep going down until works.

If I remember correctly S-Video may work with 1024, but for RCA you may need to go down to 800x600 or even 640x480.

Good Luck!

---

