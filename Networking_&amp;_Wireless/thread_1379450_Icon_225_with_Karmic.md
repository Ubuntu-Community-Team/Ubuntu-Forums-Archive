---
title: "Icon 225 with Karmic?"
date: 2010-01-12
forum: Networking &amp; Wireless
---

### Post by wobs on 2010-01-12
Can anyone suggest a (real) idiot's guide on how to get an Orange Icon 225 mobile 3G modem to work with Karmic?

I get the "dev/ttyHS1 cannot connect" error.

---

### Post by pdc on 2010-01-12
here is a guide using the slightly older Ubuntu

[http://www.up-stream.co.uk/2009/10/option-icon-505-under-ubuntu-9-04](http://www.up-stream.co.uk/2009/10/option-icon-505-under-ubuntu-9-04)

you need to do two things:

1) "flip" the modem, so it is not seen as a CD-ROM device, which is now linux will see it, when it is first plugged in;
2) connect

work your way through the above guide; he guides you through installing ozerocdoff (which turns off the zerocd function!!)

........ so that gets you though step 1)

and then you connect: we can guide you through that

let us know how you get along

___________________

a very simple and quick way to flip is:

1) plug your modem in
2) it should produce an icon on the desktop
3) RIGHT-CLICK on that and select "eject"
4) go to network manager (radio signals top line)

see if this guide to setting up a config helps:

go to "SET UP MOBILE BROADBAND" which is half-way down the page

[http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html](http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html)

---

### Post by wobs on 2010-01-13
Thank you - will try later & let you know

---

