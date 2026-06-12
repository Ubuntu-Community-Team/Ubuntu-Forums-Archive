---
title: "ATI vs. nVidia: Current Thinking?"
date: 2013-03-21
forum: Multimedia Software
---

### Post by JSeymour on 2013-03-21
Most recent discussion I found was over two years ago, so here it comes again :)

I've got a Dell OptiPlex 780/SMT, 1x Core 2 Duo, 3GHz on the way.  I'll be wanting to install an *economical* dual-DVI graphics card in it.  By "economical" I mean under $100 or so.  (Used from a reliable source would be fine.)

The ATI in my machine here at home, with the open source driver, has worked well for me.  Meanwhile, another Dell machine at work has an nVidia card in it.  (Running WinXP Pro.)  (It's a Quadro <something>.  I recall not which.)

I'll be running Ubuntu 12.04 LTS.  Probably XUbuntu, for the xfce WM/Desktop, as I've heard nothing but negatives about Gnome 3.

So: nVidia or ATI, this time?  Any particular recommendations?

TIA,
Jim

---

### Post by Yellow Pasque on 2013-03-21
I'd go after a GT630 (the 128-bit variant that's actually a rebadged GT440). Something like: [http://www.newegg.com/Product/Product.aspx?Item=N82E16814130792](http://www.newegg.com/Product/Product.aspx?Item=N82E16814130792)
That will do the job and give you VDPAU as a bonus.

If I wanted more 3D power, I'd try to scrounge together more money for a GTX 650Ti or a RadeonHD 7750.

---

### Post by JSeymour on 2013-03-22
> **Temüjin said:**
> I'd go after a GT630 (the 128-bit variant that's actually a rebadged GT440). Something like: [http://www.newegg.com/Product/Product.aspx?Item=N82E16814130792](http://www.newegg.com/Product/Product.aspx?Item=N82E16814130792)
That will do the job and give you VDPAU as a bonus.
Price is right, too.  Thanks.

> **Temüjin said:**
> 
If I wanted more 3D power, I'd try to scrounge together more money for a GTX 650Ti or a RadeonHD 7750.
The 650Ti is a bit over budget.  The RadeonHD has only a single DVI connection.  Is there an equivalent to the 7750 with two DVI connections, like the nVidia GT630 has?

Thanks,
Jim

---

### Post by Yellow Pasque on 2013-03-22
Well, there are plenty of 7750's with 2 DVI. Example: 
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814125453](http://www.newegg.com/Product/Product.aspx?Item=N82E16814125453)
Also, I'm not a multi-monitor user, but I think you can use something like this if you find a good card/price and it only has one DVI: [http://www.newegg.com/Product/Product.aspx?Item=N82E16812225036](http://www.newegg.com/Product/Product.aspx?Item=N82E16812225036)

Hopefully, some multi-monitor users will comment on whether an HDMI adapter works and whether fglrx/Catalyst does okay with multi-monitor. Open source radeon drivers aren't really an option right now for the RadeonHD 77x0 cards (3D accel still under development).

---

### Post by JSeymour on 2013-03-23
Hmmm... Once you get into the 7xxx series, it looks like dual-DVI cards are all double-width, higher power consumption cards?  Looks like the 6670 has nearly the performance, w/less heat, power consumption and noise?

Jim

---

### Post by bazsound on 2013-03-23
keep in mind that any ati cards that require the legacy fglrx driver (2000,3000,4000, possibly 5000 series aswell) wont run on 12.10 versions of ubuntu without downgrading the x server . atis legacy driver doesnt support the new x server in ubuntu 12.10

---

### Post by JSeymour on 2013-03-24
> **bazsound said:**
> keep in mind that any ati cards that require the legacy fglrx driver (2000,3000,4000, possibly 5000 series aswell) wont run on 12.10 versions of ubuntu without downgrading the x server . atis legacy driver doesnt support the new x server in ubuntu 12.10
Heck, I've got an HD 2400 Pro on this machine (the one at home) and it's running the open source driver.  So I doubt this will be an issue with a card that's four years newer :)

But thanks for the heads up, nonetheless!

Jim

---

