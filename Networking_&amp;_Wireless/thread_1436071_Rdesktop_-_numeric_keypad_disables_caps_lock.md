---
title: "Rdesktop - numeric keypad disables caps lock"
date: 2010-03-22
forum: Networking &amp; Wireless
---

### Post by mizar001 on 2010-03-22
The issue i found is that when i connect from ubuntu to windows 2003 server, through rdesktop, using the numeric keypad disables automatically the caps lock setting.

To reproduce the problem :
- connect to a windows remote pc through rdesktop
- open notepad
- press caps lock to set the capital letters
- digit some capitalized chars
- digit some numbers with numeric keypad
- digit some capitalized chars again

The result is :
ADKLEFL2390309ajkejkjf

The caps lock has been silently deactivated.

Only ubuntu clients are affected by this. I think it's a bug of rdesktop.

---

### Post by drbin on 2011-03-21
I can verify that on a newly updated system with 10.04LTS.
Caps_Lock inhibit is replaced in 'common' for caps to work.
The keypad is giving the problem. Is it the keymap?

---

