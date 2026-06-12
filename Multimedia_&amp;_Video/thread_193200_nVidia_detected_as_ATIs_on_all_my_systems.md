---
title: "nVidia detected as ATIs on all my systems"
date: 2006-06-09
forum: Multimedia &amp; Video
---

### Post by blazko on 2006-06-09
Hello,

Dapper is now the thord Ubuntu I use. It works well so far except, that on my systems, nvidia-glx enable always fails.

Reason: it always specifies a wrong BusID so that X will not start - removingi it fixes the error. Additionally, funnily it labels all my cards as ATI cards. I own these nVidia cards:

- ASUS 6600LE
- ASUS 6200
- Gainward 6800GT @ Ultra

It is not really aproblem but also causes that I cannot set resolutions higher than 1024 and no higher refresh rate than 60 Hz except when manually editing xorg.conf.

Could not find similar probs using search here.

Thanks and greetings,
Timo

---

### Post by patrickfromspain on 2006-06-09
you have three computers and on the three happens the same?? Which motherboards do you have??

It's quite "funny" :) Sorry ;)

---

### Post by taurus on 2006-06-09
Are those mobos happen to have onboard video card, ATI?  If you have an onboard video card and you install another video, AGP or what not, you need to go into your BIOS and turn off the onboard video card...

---

### Post by blazko on 2006-06-09
Hello all,

Well, actually these are two computers - one has two PCIe cards. Setup is as follows:

- AMD32 2600 w/ EPoX nForce 2 mobo, no onboard VGA
- AMD64 3800 dual w/ ABIT nForce 4 mobo, no onboard VGA

:-)

Well, with breezy and hoary all went smooth.

Thank you.

Btw.: in breezy there was a test+feedback agent where one could test keyboard, sound, LAN etc. and post on the fly feedback to be posted to ubuntu. Where is this now? In the device database there is only a thingy generating a unique setup/config ID that show a website with very rough info... :-/


Regards,
Timo

---

### Post by Havoc on 2006-06-10
I can confirm this too.

I have a Nvidia 6200, and strangely, in the identifier line in xorg.conf, it's detected as an ATI card.Running "lspci" shows me the normal card alright, and running "sudo dpkg-reconfigure" also detects it alright.Enabling the Nvidia drivers with the correct identifier makes them cause buggy behaviour.Also, "nvidia-xconfig" and "nvidia-glx-config enable" seem to muck up, not only in the identifier line, as I said before, but also in the BusID line, where it puts 0:5:0, instead for the correct 2:0:0.Things worked like a clock on my older Breezy installation.

Aside from those problems, I'm really starting to believe that hardware acceleration support in Dapper is worse, at least on my machine.For instance, epsxe on Breezy would run a specific game *too* fast, whilst on Dapper, the same program, on the same hardware, runs the same game *very* slowly.

These are really strange problems indeed.

---

### Post by blazko on 2006-06-11
Hello,

[QUOTE=Havoc]BusID line, where it puts 0:5:0, instead for the correct 2:0:0[/QUOTE]

Ja, exactly BusID mismatch here, always getting 0:5:0 instead of correct 2:0:0.

Greetings,
Timo

---

### Post by Havoc on 2006-06-11
I'll try installing the older 8156 drivers from Nvidia, and come back with some answers.Oh, and, SDL also seems to be f**ked up.Gives me Segfaults for no reason.But that's another subject. :)

---

