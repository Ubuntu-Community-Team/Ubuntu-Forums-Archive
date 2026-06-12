---
title: "HDMI video output and not keeping settings on an HDMI switch"
date: 2009-01-15
forum: Multimedia Software
---

### Post by kwatts on 2009-01-15
Hi all,

Posting this because I've yet to see anyone with this problem. I've got a laptop (HP Pavilion dv5z with the dedicated ATI Radeon HD 3450) with HDMI out. That part works, even with HDMI audio. The problem is that when I use an HDMI switch (Onkyo TX-SR605). It works, but if I say, switch to another setting (DVD) on the HDMI switch then return to the laptop, the display isn't correct and comes out funky or not at all. Anyone else get this problem or know how to correct it?

I'm using the ATI Catalyst 8.12 Proprietary Linux x86 Display Driver from [http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

Thanks in advance...

-K

---

### Post by markbuntu on 2009-01-15
Have you tried using the detect monitor function in the Catalyst Control Center when you reconnect?
Also, there is a way to force the monitor in the aticonfig options.

aticonfig --help

---

