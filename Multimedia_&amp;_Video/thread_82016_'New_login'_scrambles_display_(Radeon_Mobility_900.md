---
title: "'New login' scrambles display (Radeon Mobility 9000 + fglrx)"
date: 2005-10-25
forum: Multimedia &amp; Video
---

### Post by AndyC_772 on 2005-10-25
On my laptop (Dell Inspiron 8200), if I choose Applications > New Login, the display becomes scrambled. The mouse pointer is still OK, and the login screen is clearly working (garbled menus appear and disappear when I click on where the buttons should be), but the structure of the display is broken up. (I'm sure a screenshot would help describe it better!)

Pressing CTRL-ALT-BACKSPACE returns me to my previous session and restores the display to a working state.

I'm using Breezy with the fglrx driver.

---

### Post by tukuyomi on 2005-11-01
I have the same problem here.
My Graphic Card is a Radeon 9250 pluged on a Nforce2-based motherboard.
fglrx seems to work fine with the Option "UseInternalAGPGART" "no"
If I replace my xorg Driver "fglrx" with "ati", this bug does not occur...

---

### Post by AndyC_772 on 2005-11-27
So... nobody has a clue what's wrong? :(

---

