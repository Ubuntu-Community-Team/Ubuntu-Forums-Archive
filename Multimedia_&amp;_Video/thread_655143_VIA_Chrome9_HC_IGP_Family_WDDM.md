---
title: "VIA Chrome9 HC IGP Family WDDM"
date: 2008-01-01
forum: Multimedia &amp; Video
---

### Post by transporter_ii on 2008-01-01
VIA Chrome 9 HC IGP Family WDDM

I have spent all afternoon on this, with mixed results. I tried compiling my own drivers...didn't work.

Here is a driver that did work and was pretty easy to install:

VIA UniChrome Pro Driver Binary
[http://www.viaarena.com/default.aspx?PageID=420&OSID=45&CatID=3220&SubCatID=189](http://www.viaarena.com/default.aspx?PageID=420&OSID=45&CatID=3220&SubCatID=189)

This was just released Dec. 2007 and is listed for Ubuntu 7.10.

Now I have an Everex gc3502, and it actually has a Chrome 9 HC. The HC driver is listed at viaarena, but only up to Ubuntu 7.04, 

System\Administration\Screens and Graphics now lists my video card driver as:

via - VIA Unichrome (CLE266, KM400/KN40...

I have a much wider range of screen resolutions now, but I do not seem to have video acceleration. I have tried several games and neither work at all, but the same games work on an older system with a good video card in it.

So I guess it is good to have a somewhat easy to install driver that will work with this video card, but I still feel we are being short changed, as something still seems to be a little off. However, being able to change screen resolutions is kind of nice.

Transporter_ii

---

### Post by transporter_ii on 2008-01-01
Ok, I have reverted back to the generic VESA driver, as the system seemed quirky with the official VIA drivers.  Flash video worked with the VIA driver, but Totem player hung up when I tried to play an MP3.

The stupid thing is, this is an Everex gc3502...they sell almost the same model with a Linux distro on it (gOS / google os), so I sure the heck would like to know how they configured the video driver for the chrome 9 hc.

Transporter_ii

---

### Post by kmseven on 2008-01-26
Try compling openchrome from svn: [http://wiki.openchrome.org/tikiwiki/tiki-index.php](http://wiki.openchrome.org/tikiwiki/tiki-index.php)

This worked for me, though I didn't see a lot of improvement over vesa.

---

### Post by albertlash on 2008-02-18
I too would like to know what drivers the Everex gPC and Cloudbook use... I compiled a recent VIA driver from source on their site, and it works better than VESA and openchrome in some ways, but blurs from time to time.

---

### Post by albertlash on 2008-02-18
Also the Zonbu laptop is the Everex NC150x - which has the same chipset.

---

### Post by starcannon on 2008-03-05
Just got a cloudbook delivered to my door this afternoon.
Its got CX700M2 UniChrome PRO II Graphics chipset, and is set up with vesa.
It sucks, I am seriously considering sending it back because of the UniChrome GPU.
VIA just got strike 2 with me, one more and I'll never buy VIA based products again.
Stripping Direct Rendering support from their linux drivers? wtf? The Openchrome driver has mixed results, but nothing of help here on my cloudbook with the oem gutsy 7.10 based gOS that shipped with the laptop.

Wish 8g Eee's weren't sold out all the time.

---

