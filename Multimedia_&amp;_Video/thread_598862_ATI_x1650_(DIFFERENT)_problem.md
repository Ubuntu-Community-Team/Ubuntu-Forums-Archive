---
title: "ATI x1650 (DIFFERENT) problem"
date: 2007-10-31
forum: Multimedia &amp; Video
---

### Post by ncls on 2007-10-31
Hi,
well there have been a lot of people posting reports about not-working ati cards, and I've read most of them, but I came to the conclusion that my problem is not the same.
GFXCARD: ATI RADEON X1650 PRO

when I try to load ubuntu (either from harddrive or live cd) it just displays a black screen, when it should show the "login" thing.

it doesnt rly display a black screen though, but shows 4 lines of text, each of them ending with [OK], and i can type after its 'done'.

im using an old nvidia card atm and it workes flawless (besides the poor performance ):)

i've installed ubuntu today for the 1st time, what might explain the fact that i have to ask for help here :/


thanks for any help
ncls

---

### Post by Yellow Pasque on 2007-10-31
So, are you at a terminal after this is done? If you're not try hitting Ctrl-C or Ctrl-Alt-F1.

Then, install the driver.
```
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial -f
```

Reboot. Post back.

---

### Post by ncls on 2007-11-01
well in the meantime my problem changed, but actually what u said helped.
i was playing around with the driver settings etc and after i rebooted i was in the terminal (whereas in my intitial post i wouldnt be in the terminal)

thanks :)

---

