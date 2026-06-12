---
title: "No jacksense, No sound at all to headphones on Acer w/Connexant"
date: 2011-04-11
forum: Multimedia Software
---

### Post by unc0nn3ct3d on 2011-04-11
Good day everyone I've been having a hell of a time getting my sound card to work properly with this new laptop.  I've spent days going through possible solutions and I've run out of options so I've come hat in hand to see if anyone can help me with this one.

So the laptop is an Acer Aspire 5235-BZ684.  It's a new piece of hardware running AMD's E350 APU technology.  Being only a couple months old I was expecting problems but it wuold seem that this issue is not exclusive to this particular model.

I've tried everything editing the alsa-base.conf, model=auto and every other model I could find that people have said worked
I've manually compiled alsa with support for all models and installed it like that
Purged alsa and installed fresh many times
I've installed the linux-alsa-driver-modules


Here is some info on the card

 0 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xd0544000 irq 43
 1 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xd0540000 irq 16

00:01.1 Audio device: ATI Technologies Inc Device 1314
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)

My alsa info in full can be found here:
[http://www.alsa-project.org/db/?f=87ee0cca91f93bb6a6ab35a1895e9941fee10011](http://www.alsa-project.org/db/?f=87ee0cca91f93bb6a6ab35a1895e9941fee10011)

Thanks so much in advance for any help I really appreciate it

---

### Post by Yellow Pasque on 2011-04-11
Just for reference, 'auto' is not a valid keyword for your codec. The cx20584 is similar to the 5066

```
Conexant 5066
=============
  laptop	Basic Laptop config (default)
  hp-laptop	HP laptops, e g G60
  asus		Asus K52JU, Lenovo G560
  dell-laptop	Dell laptops
  dell-vostro	Dell Vostro
  olpc-xo-1_5	OLPC XO 1.5
  ideapad       Lenovo IdeaPad U150
  thinkpad	Lenovo Thinkpad
```

EDIT: Make sure you try ideapad: [http://tomoyo.sourceforge.jp/cgi-bin/lxr/source/sound/pci/hda/patch_conexant.c#L3015](http://tomoyo.sourceforge.jp/cgi-bin/lxr/source/sound/pci/hda/patch_conexant.c#L3015)

---

### Post by unc0nn3ct3d on 2011-10-21
Looks like this age old problem has been solved.. I can't remember where I found the solution but all you need to do is have this line in your alsa-base.conf

options snd-hda-intel model=,asus

obviously if that line is there but with a different ending you are going to want to change it to this.

---

