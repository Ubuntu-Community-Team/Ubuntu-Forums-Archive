---
title: "Issues with the new GTX 260 video card on Hardy"
date: 2008-08-07
forum: Multimedia Software
---

### Post by fang64 on 2008-08-07
Is there any support for the GTX 260 with envy, I noticed the 177 drivers are available seems that it will not detect the card. I would have thought the 177.14 series would include support for them but apparently not. Is there a backport for Nvidia 177.13 with GTX 2xx support?

Or should I go ahead and use the Nvidia blob since the 177.13 will only be on intrepid?

---

### Post by Wild-Storm on 2008-08-11
same problem here but with ubuntu 64bit.
i would be very pleased if somebody could help :)

---

### Post by hkbruvold on 2008-08-11
I have the same problem in Ubuntu 32bit.

---

### Post by Wild-Storm on 2008-08-11
is there any way of getting a screen resolution higher than 800x600 pixels without nvidia-drivers (the native nvidia-new stuff doesn't work either)?

edit:// tried out a lot of stuff (modelines, hsync + vsync rates) but i still can't get it work. my monitor always puts an error message (wrong config. can't use xxx hz with xxx hz)
i had the same problem earlier with an ati-card and ubuntu dapper drake (found an old posting by using google to get my mhz rate ^^). at this time it only helped using the ati-module (that does not work at this time ...)
so if anyone has any advice i would be pleased to hear it

and please excuse my bad/confusing english, but i'm not native and i'm kind of tired

cheers


edit2:// yep, got it. thanks goes out to kde-guidance (somehow the hsync/vsync stuff doesnt work _exactly_ with vesa, cos I get 74.6 hz, not 75hz, but with lower rates it works)

---

