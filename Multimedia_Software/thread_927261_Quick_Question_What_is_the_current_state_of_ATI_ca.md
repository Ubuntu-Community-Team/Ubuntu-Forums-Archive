---
title: "Quick Question: What is the current state of ATI cards in ubuntu?"
date: 2008-09-22
forum: Multimedia Software
---

### Post by mandrakethepenguin on 2008-09-22
Hi!

I was considering an ATI card, I don't have an AGP nor a PCIe slot, so I had to settle for a standard PCI card. ATI seemed to have the latest features packed into their Radeon HD cards, I didn't want to go back to an nVidia 6200, so I found and liked this one.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814161238](http://www.newegg.com/Product/Product.aspx?Item=N82E16814161238)

[B]So Basically:
[/B]
[LIST]
[*]I've heard some bad stuff about ATI cards. Will this one work? (I use compiz, watch HD videos and would like to play some native Linux games like UT2004)
[*]And if it applies, what can't I do with this card?
[*]Intel i915G is KILLING ME!
[/LIST]
Any of your help is greatly appreciated.:smile:

---

### Post by driven1 on 2008-09-23
I run ATI graphics with no problems using the restricted (non-free) driver from ATI. HD3200 on board graphics work fine for me, and I have a Radeon 3450 coming in a couple of days (I need s-video out). From what I read on Phoronix, ATI has made up ground on their drivers, though they aren't open yet :(

Works good on my machine. Of course, ymmv.

---

### Post by mandrakethepenguin on 2008-09-24
Thanks, I heard that 2D graphics, like those provided by the Cairo library, has some problems on ATI cards. Is this true?

---

### Post by erlguta on 2008-10-01
> **driven1 said:**
> I have a Radeon 3450 coming in a couple of days

Hi driven1, how the ATI Radeon HD 3450 256 MB works in ubuntu?..3D?
Any help would be appreciate.

---

### Post by markbuntu on 2008-10-01
HD3450, HD2400 should be no problem. Just be sure to follow this guide to install the latest driver:


[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

---

### Post by Yellow Pasque on 2008-10-01
I always have problems building the latest Catalyst driver on Debian/Ubuntu and the one in the Hardy repo isn't recent enough for my Radeon 3200 IGP. For some reason, the kernel module never builds, and since it's closed-source, it outputs an extremely unhelpful build log that says something like "didn't build". This leaves me with Mesa software acceleration, which is what I currently have with the open-source radeonhd driver (that should change soon).

---

### Post by driven1 on 2008-10-02
I've had my new Radeon 3450 installed for a week now with no problems at all. The ATI Catalyst driver and control panel work fine. It worked with digital and vga displays, and it even worked with my plasma tv out of the box. I had the same results with the IG from my mobo.

I have compiz set for major eye candy, and video is sharp and smooth.

---

### Post by binbash on 2008-10-02
you will easily install drivers, get everything working probably.But the drivers SUCK, open an application like blender or game while compiz is on and you will see what i meant :)

---

### Post by markbuntu on 2008-10-02
> **Temüjin said:**
> I always have problems building the latest Catalyst driver on Debian/Ubuntu and the one in the Hardy repo isn't recent enough for my Radeon 3200 IGP. For some reason, the kernel module never builds, and since it's closed-source, it outputs an extremely unhelpful build log that says something like "didn't build". This leaves me with Mesa software acceleration, which is what I currently have with the open-source radeonhd driver (that should change soon).

The Ubuntu How to is wrong. The only guide I ever found that worked properly for installing the ati driver was this one:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

---

### Post by sloggerkhan on 2008-10-02
yeah, currently ati how-tos are usually wrong.
Make sure you have the correct dependancies for building the ubuntu packages from the installer and you're good, basically.

---

### Post by Yellow Pasque on 2008-10-02
> **markbuntu said:**
> The Ubuntu How to is wrong. The only guide I ever found that worked properly for installing the ati driver was this one:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)
That's the one I followed. I believe the issue involves my customized kernel and dkms.....

---

### Post by erlguta on 2008-10-03
> **driven1 said:**
> I've had my new Radeon 3450 installed for a week now with no problems at all. The ATI Catalyst driver and control panel work fine. It worked with digital and vga displays, and it even worked with my plasma tv out of the box. I had the same results with the IG from my mobo.

I have compiz set for major eye candy, and video is sharp and smooth.

Thank you Driven1 !

---

### Post by c4tly5t on 2008-10-03
i use a Radeon HD 3200 and it works fine for all the compiz effects and gaming i do (mostly Oblivion and Spore) havent tried HD movies on it.

---

### Post by markbuntu on 2008-10-03
> **Temüjin said:**
> That's the one I followed. I believe the issue involves my customized kernel and dkms.....

No doubt because ati drivers from 8.6 on I think use dkms. I know 8.8 and 8.9 do for sure.

---

### Post by sloggerkhan on 2008-10-04
Yeah,they use DKMS. Honestly, I'm glad it uses DKMS, makes installing and updating so much easier.

---

