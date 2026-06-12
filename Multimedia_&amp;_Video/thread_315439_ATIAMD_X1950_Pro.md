---
title: "ATI/AMD X1950 Pro"
date: 2006-12-09
forum: Multimedia &amp; Video
---

### Post by bo2k10 on 2006-12-09
Current ATI/AMD release drivers at version 8.31.5 are supposed to work with X1900 series cards, does that include X1950?

Am I correct in understanding that none of the open source drivers work with the X1000 series ?

Any info is appreciated

Early Happy New Year to ALL.

---

### Post by slackern on 2006-12-17
I'll have one to try out in about a week.
The card im getting is a Gecube X1950Pro for the AGP slot with 256Mb ram.
Will let you know how it works here, if i forget it please send me a message.

---

### Post by 360skier on 2006-12-19
I have the same card (ATI x1950 pro for PCI-Express), and the same question. Stats are [here]("http://ati.amd.com/products/RadeonX1950/x1950pro_specs.html"). I'm going to check out the drivers as soon as I build my computer (in a few days). I'll send another reply then.

---

### Post by slackern on 2006-12-23
I just installed my card but i haven't had so much time to fiddle with it.

It did not start kdm/gdm/X properly default, tried the opensource driver and with fglrx and it just locked up for me, running with VESA drivers right now and then it booted up properly

Output from lspci

02:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 7280
02:00.1 Display controller: ATI Technologies Inc Unknown device 72a0

---

### Post by WalmartSniperLX on 2006-12-23
I have a X1600pro AGP and the open source drivers do not work at all (infact, they dont work with the X1K at all)

FGLRX (ati/amd) drivers claim to have support for X1K now but its horrible. Any radeon 9xx series seems to run faster than my X1600 (my mobile and friends computer).

But hopefully there will be a change, however I do not count on it being soon since ati hasnt been fixing much with their monthly releases. Im a little upset with their driver team, since they think that monthley drivers help, when they should be focusing more on quality rather than service speed. 

Just my 2 cents

---

### Post by Black-Byte on 2007-01-14
Sorry for pushing up an old thread ;)

Ati has released the 8.33.6 drivers.
they have support for the  Radeon X1950 Series (RV570 XT 7280)

and they work with the AIGLX option, but not with the composite extension :/

```
black-byte@Odysseus:~/Download$ beryl
XGL Absent, checking for NVIDIA
Nvidia Absent, checking for texture_from_pixmap
texture_from_pixmap Present
beryl: No composite extension
```

---

### Post by slackern on 2007-01-14
> **Black-Byte said:**
> Sorry for pushing up an old thread ;)

Ati has released the 8.33.6 drivers.
they have support for the  Radeon X1950 Series (RV570 XT 7280)

and they work with the AIGLX option, but not with the composite extension :/

```
black-byte@Odysseus:~/Download$ beryl
XGL Absent, checking for NVIDIA
Nvidia Absent, checking for texture_from_pixmap
texture_from_pixmap Present
beryl: No composite extension
```

Ahh thanks for the info, was subscribing to this thread to see if something happend.
I saw that new drivers had come out but they only said x1900 in the readme whilst the windows drivers said x1950 so i thought they hadn't added the support yet for X1950.

Atleast i can get it up and running again then without running with the vesa driver.

---

### Post by 360skier on 2007-01-25
Does anybody know why my graphics get screwed up when I try to run Ubuntu? The boot menu comes up fine but even in graphics safe mode I get completely screwed up graphics. My cursor is a parallelogram and my Ubuntu logo is gray. Any ideas?

---

### Post by 360skier on 2007-01-25
Oh yeah, BTW I have an X1950 pro PCI-e card.

---

### Post by m1ke323 on 2007-01-27
I also have a PCI-E x1950PR0 and can not for the life of me get the ati fglrx drivers to work.  My system won't load at the boot screen and a weird blue dotted line goes across the screen.  I have pretty much given up becuase I can't find a working driver for my card.

This was on a fresh computer build and fresh Ubuntu install as well.

---

### Post by Tommy S on 2007-01-29
> **m1ke323 said:**
> I also have a PCI-E x1950PR0 and can not for the life of me get the ati fglrx drivers to work.  My system won't load at the boot screen and a weird blue dotted line goes across the screen.  I have pretty much given up becuase I can't find a working driver for my card.

This was on a fresh computer build and fresh Ubuntu install as well.

I have the same card (X1950pro) and I managed to install the latest 8.33.6. ATI drivers ok using this guide - [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide) 

Use method 2 and it should install them fine.

The only problem now is that whenever I try to play a movie file ubuntu crashes to the login screen, if you have any ideas whats going on could you post in my thread - 
[http://www.ubuntuforums.org/showthread.php?t=347599](http://www.ubuntuforums.org/showthread.php?t=347599)
 
cheers

---

