---
title: "Wireless Radio Issue"
date: 2009-07-13
forum: Networking &amp; Wireless
---

### Post by Sum Guy on 2009-07-13
A short while ago I managed to fix a problem with my wireless card (3945abg) by automating a script that manually rebooted the antenna, which didn't turn on automatically. However, I had to reinstall the computer recently due to some power failures compromising system stability, and although I copied the script, for some reason it never got saved to my external hard disk, and I can't remember the script itself. If someone knows the terminal code that performs this could you post here? Thanks.

---

### Post by Sum Guy on 2009-07-13
Anyone?

---

### Post by Sum Guy on 2009-07-14
I'm sorry if I'm bothering anyone with this, but I really need this code. I remember it included antenna=1 in one of the lines, but no matter what code I try, the card won't start running properly.

---

### Post by martinbaselier on 2009-07-14
I can guess, but I don't have the 3945. I have the 2915 and I had to create an option to turn on the wireless led, which did not go on automatically by creating a file /etc/modprobe.d/ipw2200.conf (ipw2200 is the name of the kernel module) and put in it:
options ipw2200 led=1

use lsmod to find the correct kernel module for your card.

Maybe you need to do something similar? But it's just a wild guess. I'd advice you to google for info. :)

---

### Post by Sum Guy on 2009-07-15
Thanks for the reply, I tried using my kernel module (iwl3945) and replacing led with antenna, but the antenna remained off. I remember that the original code involved several lines, that turned the card off, set the antenna on, and then rebooted it, without affecting the rest of the computer.

---

