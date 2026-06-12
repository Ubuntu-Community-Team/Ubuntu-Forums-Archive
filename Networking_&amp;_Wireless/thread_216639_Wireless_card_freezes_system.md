---
title: "Wireless card freezes system"
date: 2006-07-15
forum: Networking &amp; Wireless
---

### Post by abexy on 2006-07-15
Hello
I just installed Ubuntu on my Averatec 3270 AMD 2800+. Whenever I try accessing the Networking options for my wireless network card the system freezes. The card is a RaLink 2500. I've read that there's probably an IRQ conflict with the monitor. If that's the case, how do I solve that issue? If not, what are my other options?

---

### Post by LoafingLotus on 2006-07-20
I am having the same difficulty on my Averatec 2200, same graphics card. I tried configuring the wireless by editting /etc/networking/interfaces and through the GUI, no luck, just crashes.

---

### Post by BenWilson on 2006-07-21
I have an Averatec 3250 with RT2500, and I got it to work.

In your grub/menu.lst, add "irqpoll" on the kernel line thus:

```

kernel      /vmlinuz-2.6.15-26-386 root=/dev/hda6 ro **irqpoll** quiet splash
```

If that does not work, add "Option DisableIRQ" like this:

```
Section "Device"
    Identifier  "VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video"
    Driver      "via"
    BusID       "PCI:1:0:0"
    **Option      "DisableIRQ"**
EndSection
```

I did both and it works. I should have tried each, but right now I'm dealing with a CDROM that locks the system.

---

### Post by beemer on 2006-07-21
What does disabling the IRQ do (aside from preventing conflicts)?  I use an Nvidia gfx card - would I lose performance if I disabled the IRQ?

Thanks,

Beemer

---

### Post by BenWilson on 2006-07-21
> What does disabling the IRQ do (aside from preventing conflicts)?

I honestly don't know. A quick google find links that suggest this option when the integrated video and integrated wireless chips conflict. No mention of loss of performance. I don't use my laptop for anything requiring the full power of the laptop (I believe we have the same video chip). I've only been using Ubuntu for a couple of weeks, but I've not encountered a video problem with this (I have noticed a CDROM/webcam problem, but that may not be related). (I previously used Gentoo for 3 years.)

But, you should try 'irqpoll' as a kernel option first. If that works, no need to find out. :-)

---

### Post by insyte2 on 2006-07-22
@BenWilson - thank you very much for your post, got my wireless working because of those options :)

---

### Post by RicardusSacerdos on 2006-08-23
> **BenWilson said:**
> I have an Averatec 3250 with RT2500, and I got it to work.

In your grub/menu.lst, add "irqpoll" on the kernel line thus:

```

kernel      /vmlinuz-2.6.15-26-386 root=/dev/hda6 ro **irqpoll** quiet splash
```

If that does not work, add "Option DisableIRQ" like this:

```
Section "Device"
    Identifier  "VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video"
    Driver      "via"
    BusID       "PCI:1:0:0"
    **Option      "DisableIRQ"**
EndSection
```

I did both and it works. I should have tried each, but right now I'm dealing with a CDROM that locks the system.


I also have the same problem with my Averatec laptop.  I tried the first solution (after an hour or so of stumbling around trying to figure out where the file was and how to save to that folder and eventually doing so).  No luck, though: as soon as I enabled the wireless, the system froze.

I'd like to try the second solution but don't know what file to edit or where to put it when I find it...take pity on a Windows pro but Linux very-newby?  Use little words.  :confused:

---

### Post by Bil-E-daKid on 2006-08-26
Ricardus,  the second file looks like it's /etc/X11/xorg.conf

---

### Post by RicardusSacerdos on 2006-09-04
Bil-E, that was it!  Many thanks!

---

### Post by Bil-E-daKid on 2006-09-04
No worries! :-D

---

