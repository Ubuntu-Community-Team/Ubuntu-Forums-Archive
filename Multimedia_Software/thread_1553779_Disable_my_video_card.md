---
title: "Disable my video card?"
date: 2010-08-15
forum: Multimedia Software
---

### Post by jhills2 on 2010-08-15
Hey,

I just got rid of vista and am running Ubuntu 10.04 perfectly! 

I love how my screen can now dim to save battery life, but now i am curious with ubuntu if i can disable my dedicated nvidia card on my laptop and just run off of onboard graphics? i know my buddies alienware has a button for this but is there a terminal command so i can do this as well.


thanks!

- Joseph

---

### Post by lidex on 2010-08-15
On a laptop? You sure you have 2 graphic display adapters?

---

### Post by jhills2 on 2010-08-15
> **lidex said:**
> On a laptop? You sure you have 2 graphic display adapters?

i'm sorry i misspoke, i know they are integrated on laptops, i have a nvidia geforce 8400m gs in mine.
'

i should have worded it in a way that i can turn down the power on it if you will so it doesn't suck up all my battery....i could have sworn on my buddies alienware had a option where he could turn it down to save battery. im on crack i think....

thanks

---

### Post by lidex on 2010-08-15
Do you mean to turn down the screen brightness or backlight? You can access settings in 'System>Preferences>Power Management' 
What model do you have? [http://www.linlap.com/](http://www.linlap.com/)

---

### Post by khelben1979 on 2010-08-16
To be sure that you have both integrated graphics from nVidia + maybe intel graphics, do the following:
```
lspci
```

The configuration of the [X server]("http://en.wikipedia.org/wiki/X_server") decides what graphics driver is going to be used, so there's the place if you want to manually change [the graphics configuration]("http://en.wikipedia.org/wiki/Xorg.conf").

Other than that you can always downclock your nVidia graphics chip to save power. Don't ask me how. :) The nVidia software preferences might allow you to do it or you might search for another tool to do it.

---

