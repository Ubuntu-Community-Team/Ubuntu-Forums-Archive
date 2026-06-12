---
title: "Laptop screen below external monitor"
date: 2010-02-05
forum: Multimedia Software
---

### Post by nphoffman on 2010-02-05
Hi guys. Using a large virtual screen and xrandr, I've got my external monitor configured above my laptop screen. Here's how I'm configured:
* Screen is 1680x1950
* DVI-0 is 1680x1050, positioned at 0x0
* LVDS  is 1440x900,  positioned at 0x1050.
[http://pastie.org/810576](http://pastie.org/810576)

However, when I disable DVI-0, the position of LVDS moves from 0x1050 to 0x0 , and the screen shrinks to 1440x900 :
  [http://pastie.org/810579](http://pastie.org/810579)

It's easy to grow the screen back to 1680x1950:
  [http://pastie.org/810581](http://pastie.org/810581)

However, if I try to move LVDS down to 0x1050, it stays at 0x0 :
  [http://pastie.org/810585](http://pastie.org/810585)

Do you have any idea how to get LVDS down to position 0x1050 ?

I'm trying to do this because that's where my KDE panels are. At the moment, when I disable DVI-0, my KDE panels are no longer visible.

Thanks!
Nick

---

