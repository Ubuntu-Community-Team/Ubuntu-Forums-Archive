---
title: "Decent support for Hp Tm2 laptop (ati switchable graphics + multitouch)"
date: 2011-01-24
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by sneax on 2011-01-24
Hello, I own a HP Tm2 laptop. This is a laptop with ATI switchable graphics (intel HD vs ATI discrete) and wacom digitizer (inlcluding pressure sensitive pen) and a capacitive multitouch touchscreen. Also multitouch touchpad.

None of these work in 10.10, every pointing device is just mouse emulation. Switchable graphics is buggy at best. The touchpad on off button does not work (important for tablet mode).

What I think is very nice with Windows 7 is that it understands the difference between input from the pen, input from the mouse or mousepad and input from the touchscreen and handles accordingly.


Will these things come in 11.04? Or will they ever come? I think tablets (and thus convertibles) are part of the future so maybe it is intresting to think about this?

---

### Post by cariboo on 2011-01-24
Unity, really isn't designed for a touch screen, but multitouch is being worked on this cycle, so things should get better.

Switchable graphics is already possible, if you install, the [Ubuntu Control Center]("http://www.webupd8.org/2010/06/ubuntu-control-center-brings-simplicity.html"), there is an applet to do the switching.

---

### Post by Favux on 2011-01-24
Hi sneax,

Can't help you with the switchable graphics.

It sounds like you do not have the digitizer on the Wacom driver.  You should have the stylus, eraser, and multi-touch working.  You may need either a newer wacom.ko, the usb kernel driver, and/or newer xf86-input-wacom, the X driver.  If the touch switch emits a keycode in xev you should be able to bind it to a toggle touch script.  Find the above at the [Bamboo P & T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").

---

### Post by sneax on 2011-01-31
Ok after some testing the switchable graphics indeed work, but there is a lack of decent drivers for the ATI chipset, the Intel currently works best.

Anyway just an update
I tried kernel 2.6.38rc2 and lots of things are improved, no black screens anymore (downside is that brightness is simply at full all the time), clickpad has now first signs of multitouch (double tap does right click) etc...

Things are going in the right direction.

---

### Post by cariboo on 2011-01-31
New working ATI/AMD drivers don't usually show up until near the end of the development cycle, usually about the time the RC is released.

---

