---
title: "Jaunty, DualScreen, Radeon Drv...screen shifted left"
date: 2009-05-20
forum: Multimedia Software
---

### Post by marvlush on 2009-05-20
Here is the problem:
=========================

I have (2) Dell 2001FP LCD's connected to the external ports of a Thinkpad dock. One to a VGA port and one to a DVI port.

The signal from the LCD connected to the dock's VGA port...is shifted over to the left (and off the screen) by 300-400 pixels or so.

Normally...a Dell 2001FP will auto-adjust itself based on the signal that comes in via the VGA cable...but in this case, the screen is so far off to the left...the LCD's horizontal adjustment is already to the max...so I cant shift it over anymore.

So, how do I shift he screen back to the right?



Here are the setup details:
===========================

  0. clean install of Jaunty w/open source Radeon driver
  1. Thinkpad T60 w/ ATI Mobility X1400
  2. A pair of Dell 2001FP lcd panels
  3. Thinkpad advanced dock


Normally, I would offer an xorg.conf file...but to be honest, I didnt touch it to get this setup working (almost)....*amazingly* in Jaunty, all I had to do was go into the GUI "Display" tool in the menu...and tell it I had (2) 1600x1200 screens, and to turn off my internal laptop screen.


Other details worth noting:
===========================
1. happens in 32 bit and 64 bit

2. when **ONLY** the VGA screen is connected (not just on, but connected) works properly

3. I cant move to the ATI's proprietary fglrx driver because the only versions of fglrx that work on my Thinkpad's X1400....dont work on Januty's xorg 1.6

Any ideas?



thanks,

/mario

---

### Post by marvlush on 2009-06-06
finally fixed this problem after weeks of scratching my head.

go into monitor menu (the one on the VGA port), do "factory reset", and voila!

all sync'd up correctly, dual LCDs, from Thinkpad advanced dock, X1400 mobility on Radeon open source driver.

cheers,
/m

---

