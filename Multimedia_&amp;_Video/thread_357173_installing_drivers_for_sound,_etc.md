---
title: "installing drivers for sound, etc"
date: 2007-02-09
forum: Multimedia &amp; Video
---

### Post by drumkitcat on 2007-02-09
I have 2 computers recently set up; one is a ubuntu 6.06 system, and one is a xubuntu 6.1 system.. both have old Soundblaster sound cards, and both have a set of cheese-ball speakers attached.

How do I load a driver for the sound cards in each case, so that I can hear sound?  currently neither computer will play sound and the Ubuntu computer (because it has more features in the software) says "the volume control did not find any hardware to control" - so that leads me to believe that it didn't load a driver....  The Xubuntu system has fewer options, but I imagine if it could, it would tell me the same thing.

In the Ubuntu system, I see this thing called "device manager" - but I don't see how I can add a driver for anything there... and ubuntu clearly does not recognize the sound card.

Any ideas?

---

### Post by Greg2 on 2007-02-09
> **drumkitcat said:**
> both have old Soundblaster sound cards
Are they ISA 16-bit or PCI cards?

---

### Post by drumkitcat on 2007-02-09
In both cases they are PCI cards.. sorry for not clarifying that originally.

They do both work as they were previously operational under a windows environment.

---

### Post by Zimmer on 2007-02-09
[https://help.ubuntu.com/community/HowToSetupSoundCards](https://help.ubuntu.com/community/HowToSetupSoundCards)

This may be the info you are looking for....

---

### Post by Greg2 on 2007-02-09
> **drumkitcat said:**
> In both cases they are PCI cards 
OK, if you are still having problems after the How-to that Zimmer has linked for you... we need the output from the terminal of:```
lspci |grep audio
```and```
cat /proc/asound/cards
```

---

