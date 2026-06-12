---
title: "New monitor - reconfiguring for highter resolution"
date: 2006-08-01
forum: Multimedia &amp; Video
---

### Post by exssnrg on 2006-08-01
I installed ubunto on a HP compaq nc6000 laptop, and the built-in screen works just fine at 1024x768.  

I have a docking station at work and I'm plugging into a Dell 2001FP.  I'd like to configure my laptop to use 1600x1200 in this situation.  Not sure how to do that.

xorg.conf shows my display adapter to be:
"ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
        Driver          "ati"
        BusID           "PCI:1:0:0"

I believe this is correct.

I tried to edit xorg.conf to add a couple of higher resolution displays but that did not seem to work.

I'd appreciate any good advice.  Thanks in advance. :)

---

### Post by it.henrik on 2006-08-01
how do you mean it didnt work?

If you add more resolutions you can usually whitch between them with ctrl + alt + + and ctrl + alt + -.

I dont have any experience with docking stations and linux .. sorry :/

---

### Post by tseliot on 2006-08-01
Try this guide:
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)


OR this one (read where it says "Getting the Right Mode for an LCD monitor"):
[https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration](https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration)

---

