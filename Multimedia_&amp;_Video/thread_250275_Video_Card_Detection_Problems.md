---
title: "Video Card Detection Problems"
date: 2006-09-03
forum: Multimedia &amp; Video
---

### Post by Hydroxyl on 2006-09-03
Hey, Ubuntu forums. Here goes my first post!

Anyway, I have two video cards in my computer.

[B]Intel 810e Integrated
ATI RADEON 9200SE PCI 1x[/B]

Here is where my problem arises.

Ubuntu can't select between the two or something, and upon loading into 'live CD' will freeze, no CD music, nothing on screen.

Well, I went ahead and downloaded the DVD, and went through a text-mode install. All went well, and I logged into rescue mode where I did a nice:

```
lspci -X
```

Which showed me that, my Intel 'card' was located at PCI:0:0:0 and my ATI was located at PCI:1:13:0.

I then did:

```
dpkg-reconfigure xserver-xorg
```

And configured it as such, and got X to run.

**My problem lies here...**

Apparently, Ubuntu still thinks I'm using the 810e, and won't allow games and 3D applications to run, even after installing *fglrx*.

How can I trick Ubuntu into thinking there isn't an integrated video card in my computer?

**[COLOR="Red"]NOTE:[/COLOR]** I checked the BIOS, apparently there is a function to disable Onboard Video Memory, but seeing as how the computer is OEM (eMachines), I cann't disable it. The feature has been removed.

](*,) <-- That accurately describes how I feel right now.

---

### Post by meng on 2006-09-03
That BIOS thing blows! Can you firmware-upgrade the BIOS?

---

### Post by Hydroxyl on 2006-09-03
> **meng said:**
> That BIOS thing blows! Can you firmware-upgrade the BIOS?

Found a site that had me submit some info about my BIOS (BIOS string, CPU, OEM Vendor) and should be giving me an email in about 12 - 24 hours (or so they say) about possible upgrades I can apply.

eMachines provides no BIOS downloads/support so, I'm kind of *screwed* in that area.

---

### Post by tseliot on 2006-09-04
Unplug your PCI card and install Ubuntu using your integrated card.

Then follow this guide:
[http://doc.gwos.org/index.php/Nvidia_Intel_Integrated](http://doc.gwos.org/index.php/Nvidia_Intel_Integrated)

There's no need to use Option "NvAGP" "1" in point 4 (but of course you should follow the rest of point 4) and you can skip point 5 (since you don't have an Nvidia card).

The rest of the guide is fine.

---

### Post by Hydroxyl on 2006-09-05
> **tseliot said:**
> Unplug your PCI card and install Ubuntu using your integrated card.

In the guide, it says how to disable the integrated card in the BIOS. That's my main problem, the OEM manufacturer (eMachines) disabled the option.

Right now, I've recieved an e-mail from eSupport, and I'm about to call them up, because they apparently have some question about my computer.

Upon doing so, providing me with a BIOS update and then, BAM.

Maybe I can disable this onboard thing, but we'll have to see.

**EDIT:** It's going to cost me $49.95 for that BIOS upgrade. :mad:

---

