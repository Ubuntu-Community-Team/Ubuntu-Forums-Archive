---
title: "Asus P7131 card remote problems..."
date: 2007-11-14
forum: Multimedia &amp; Video
---

### Post by Juha Hjulgre on 2007-11-14
Hello. 

This is not crucial or in any means important, but i can't seem to get any response from my remote except for numerical keys an up/down/left/right :-S I've got 7.10 going with kernel 2.6.22, the remote being main reason for me to update... I've been doing searches in google for the last few days but have not found anythin useful. Anyone have an idea where to start from or have the remote going?

---

### Post by Juha Hjulgre on 2007-11-15
I got this figured out, classic case of PEBKAC(Problem Exists Between Keyboard And Chair). All buttons worked but the keys were unassigned. So first i used xev to determine the codes for buttons, and added them to .xmodmap file, then did xmodmap /home/user/.xmodmap. Now it works ok.

---

