---
title: "PuTTY  -- Special Command menu for linux?  How to Break-Key for Cisco?"
date: 2010-01-06
forum: Networking &amp; Wireless
---

### Post by EJeanmaire on 2010-01-06
Hi all,

With PuTTY in Windows I can access the special commands menu by right-clicking on the window top border... not so much in by Ubuntu-Gnome environment.  Does this menu exist in the Ubuntu version?

Secondly, how can I send the break command through PuTTY without this special command window... my Serial-to-USB converter will not seem to pass through the traditional ctrl+break key...  I have tried:
Ctrl+C
Ctrl+Brk
Brk
Ctrl+A .. Ctrl+B
Ctrl+shift+6+X
and on... and on..

A little help here?

---

### Post by Hellmark on 2010-03-22
Having the same issue here.

---

### Post by amadon on 2010-07-09
For any OS, assuming the Cisco console settings are default (9600, 8N1) you should be able to set your console software to 1200 and then hold down the space-bar for about 10 seconds to get the same impact as sending break. Then reset the console software to 9600 and you should be at a rommon prompt (assuming you were at the correct point in the boot process when you held down space).
 
I'd really like to find access to the putty "system" menu in Linux. I found via another forum that CTRL-RIGHT CLICK should give access to that menu, however the question was with xfce window manager, and the person who asked the question never replied to say whether or not it worked for them. I haven't been able to get that to work with the default window manager for Ubuntu 10.04.

---

### Post by Pork Chops on 2011-03-20
FWIW, Ctrl-right-click does work with the default window manager for Ubuntu 10.04, but unlike when running PuTTY under MS Windows, the mouse pointer has to be in the "screen" area of the PuTTY window instead of the title bar.

---

### Post by v.osnovnom.bezvreden on 2011-12-29
> **Pork Chops said:**
> FWIW, Ctrl-right-click does work with the default window manager for Ubuntu 10.04, but unlike when running PuTTY under MS Windows, the mouse pointer has to be in the "screen" area of the PuTTY window instead of the title bar.

Thanks! That helped!

---

