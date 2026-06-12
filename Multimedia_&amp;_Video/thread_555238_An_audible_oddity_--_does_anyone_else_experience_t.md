---
title: "An audible oddity -- does anyone else experience this?"
date: 2007-09-19
forum: Multimedia &amp; Video
---

### Post by blr246 on 2007-09-19
I discovered a very strange behavior today while preparing some SATA drives for encryption.

**NOTE: Do not issue the following command unless you understand it.**
It seems that after I enter the following command:
```
sudo dd if=/dev/urandom of=/dev/sdd
```

I hear a strange high-pitch noise like rapid morse code issuing from my system's on-board audio.  It is a very freakish annoyance, but thankfully not a persistent one.

Adjusting the audio level of the mixer does not affect the buzzing, but it is definitely coming from the machine since it stops when I unplug the 1/8" mini jack from the line out.  I can make it louder by adjusting the amplifier on my speakers, and it is at a higher level than strictly noise alone.

The noise does not occur for:
```
sudo dd if=/dev/urandom of=/dev/null
```

So it has something to do with writing the disk and urandom and perhaps alsa.  Does anybody else experience this behavior?



Relevent Hardware:
Abit AB9 Pro Motherboard

Software:
Ubuntu Feisty Fawn w/all latest updates
2.6.20-16-generic

On a side note:
It is great to finally register!  I have been using this forum as a support resource for nearly one year now since it has been almost a year since I have become a daily Ubuntu user.

---

### Post by yabbadabbadont on 2007-09-19
Just sounds (no pun intended) like static interference due to a lack of proper shielding of the on-board audio or too close a proximity between the two chipsets.  (audio and sata controller)

---

### Post by alterpinguin on 2007-09-20
thats not new - maybe for your board and hardware combination - sometimes it helps to mute the line-in, if the main-fault is there - but the only way to get around "faulty" onboard configurations is to use a add-on soundcard (if this has not any faults and the communications channels to the card, pci-bus, usb are ok) - btw. i was using a crt-monitor and got noise from screen-changes too, so it does not need to be the fault of the mainboard, could be other hardware-component too.

---

