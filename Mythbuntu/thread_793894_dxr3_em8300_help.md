---
title: "dxr3 em8300 help"
date: 2008-05-14
forum: Mythbuntu
---

### Post by Astrolabe on 2008-05-14
Has anyone had any success in installing a Creative dxr3 card and getting it running? I have found post after post of people searching for help with various Linux distros but all in vain. While this is an old card, it has to be said the TV out was always really good.

Ideally I would have a digital TV connected to my Myth box but alas I am going to have to make do with the the old analogue TV for a year or two yet. Unfortunately the TV out (S-video) from various cards (AGP and PCIe) I have tried have all been so bad I just cannot inflict the Myth box on my family. I then remembered I had this old PC-Encore card and after checking to see what Linux support there is, I thought I would give it a go.

In the unlikely event anyone responds to this thread I will happily go into detail with what I have tried so far - but at the moment I cannot get any TV out put at all. I have mislaid the VGA pass-through cable so I can't test the VGA overlay but I make the assumption it isn't required for TV-out only.

Is there anyone out there??

---

### Post by laga on 2008-05-14
MythTV doesn't support the em8300 TV-Out, unfortunately.

What other VGA cards have you tried?

---

### Post by Astrolabe on 2008-05-14
> **laga said:**
> MythTV doesn't support the em8300 TV-Out, unfortunately.

What other VGA cards have you tried?

I think that must be right and certainly would explain the lack of support information. In this case though, I haven't even got as far as trying to stream live TV to it - I have just tried to cat a mpeg file through /dev/em8200_mv-0. em8300setup works and the various modules appear to have loaded correctly but there is no output on the TV-out port. Perhaps I do need that VGA pass-through after all.

I have tried cards based on the ATI 9550 and ATI X1650 (AGP). The same result always, after a bit of fiddling -perfect digital output but absolute crap from the analogue.

I have just had a brief play with an nVidia GeForce PX5300 (PCIe) in a different box and I must say the TV-out looks very promising.

At this time I have resorted to using an XMBC XBOX with built in myth support. The analogue output from the XBOX is perfect. I would still prefer to have the Myth PC working though.

If the dxr3 card is no go, what other cards are available that are know to have (near) perfect TV-out. I don't need (or even want) such a card to provide digital output.

Thanks for your reply!

---

