---
title: "nvidia to ati"
date: 2006-01-28
forum: Multimedia &amp; Video
---

### Post by A-star on 2006-01-28
Hi all,

At the moment I have a crappy geforce2 mx400 installed in my system.
I want to swap it for a Ati Radeon 9600 that I bought very cheap.

Can anyone tell me how to swap the nvidia drivers for the the ATI drivers?

or can I just plop in the ATI card and pray that it works automatically?

Thanks for the help.
A-star

---

### Post by Jason_25 on 2006-01-28
You wouldn't want to just pop it in and hope for the best.

Change the driver section of your xorg file from nv or nvidia to vesa.  That should make x able to boot so you can install the appropriate driver.

---

