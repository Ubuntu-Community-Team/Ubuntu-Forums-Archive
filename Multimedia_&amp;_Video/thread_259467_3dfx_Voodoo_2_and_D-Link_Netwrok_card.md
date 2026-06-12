---
title: "3dfx Voodoo 2 and D-Link Netwrok card"
date: 2006-09-17
forum: Multimedia &amp; Video
---

### Post by tombstone on 2006-09-17
I just finished my installation of xubuntu on an older system, and im having a few problems.

I'm running a K6 233 with 128mb RAM and it has 2 diffrent network cards, one is a D-Link DFE-538TX/R the other is a StarTech STNE2000 BT both are not being recognized. Also on a side note i have a PCI 3DFX Voodoo 2 video card (the one that has the input tot he card coming from your onboard video card and then proccesses it and outputs it to the monitor), and it will not go any higher then 640 X 400.

Any help on either or both would be greatly appreciated.

Preston

---

### Post by tombstone on 2006-09-17
nobody has any ideas?

---

### Post by hangfire on 2006-09-17
Last time I checked (3 years ago) a 3dfx card limited you to XFree86, and most of the Linux world (including Ubuntu) has moved on to XOrg. Workarounds exist, but if you get it to work, you're on your own maintaining it.

Any ethernet card with "2000" in it is probably a Novell NE2000 compatible. There's not much to these cards, and typically you have to tell the kernel just where it is in order for it to recognize. I suggest you go searching for kernel boot parameters... I found a modprobe, if that helps:

```
modprobe ne io=0x300 irq=10
```

Adjust i/o port and irq as necessary, of course. That from an old SuSE 6.3 manual, back when they used to deliver good documentation with their consumer distro's. I don't have anything on the D/Link, sorry.

Good luck with it.
HF

---

