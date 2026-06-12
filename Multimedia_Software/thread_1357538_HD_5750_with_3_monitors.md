---
title: "HD 5750 with 3 monitors"
date: 2009-12-17
forum: Multimedia Software
---

### Post by userfriendly on 2009-12-17
I'm considering to buy a HD 5750, specifically for running 3 monitors at home (at work I have 3 monitors hooked up to 2 cards, which was a pain in the ar**se to set up and it still doesn't work quite right: [http://ubuntuforums.org/showthread.php?p=8349285](http://ubuntuforums.org/showthread.php?p=8349285) ...well, it works, sort of, but I'd really like to avoid such hassle next time).

My question is, do I have to wait for AMD to release the Catalyst driver with Eyefinitiy support for Linux? I don't plan on using the Single Large Surface thingy anyway, I'd like my windows to maximise to only the screen they're on. A simple extended desktop setup across 3 monitors is what I want - is that possible with this card on Linux already?

---

### Post by markbuntu on 2009-12-17
I think a big part of your previous problem was mixing nvidia and ati. I have had 3 monitors working with two ati cards with no problems except no compiz due to having to use xinerama because randr1.2 is incapable of multi-gpu ,but I hear others have gotten compiz working.

That said, since this would be just one gpu running three monitors it would depend entirely on the ati fglrx driver. ATI has been a little slow supporting their latest cards in linux so you should maybe ask the ati devs at the phoronix forums to make sure before spending all that money.

[http://www.phoronix.com/forums/forumdisplay.php?f=19](http://www.phoronix.com/forums/forumdisplay.php?f=19)

---

### Post by userfriendly on 2009-12-17
Thank you.

I guess the easiest (and cheapest) way then would be to simply get a 2nd PCIe card that is also from ATI, right?

My home machine has an ATI HD 2600 as its graphics adapter, so slipping in a cheap HD 3450, or something like that, might just be the way to go. I don't play games much, all I care about is screen real estate. Thought that the 5xxx cards would be the most hassle-free way, but you're probably right about ATI drivers for Linux - not always hassle-free, especially when the cards are new.

---

### Post by markbuntu on 2009-12-18
I have a HD3650 and a HD3450 and they work just fine for three monitors, very easy to set up with the latest drivers. I suspect that by the time lucid id released the new randr will be adopted so it can be used instead of xinerama for multi gpus.

I did not wish to put you off about the 5750, I am thinking of getting one myself in my next round of hardware upgrades. I am sure the driver will be totally working very soon if it is not now, besides, the 3xxx series will not work with the XvBA video acceleration that is finally becoming available, one reason I am looking at the 5xxx series.

---

### Post by markbuntu on 2009-12-18
Well, I have just bee looking in the Phoronix forums and apparently Ati has released a hotfix for the 9.12 driver that includes eyefinity support for the 5750 among other stuff. That means the January driver will have it for sure.

---

### Post by userfriendly on 2009-12-19
Thanks, mate. But impatient as I am, I already ordered the HD 4350 and three new screens. I wanted to have it, like, *yesterday*. :D

I guess I can still upgrade should I feel at some point that the HD 2600 / HD 4350 combo is insufficient for my needs in some way.

---

### Post by userfriendly on 2009-12-23
It all works nicely with two ATI cards.

1. Removed existing xorg.conf

2. run: ```
sudo aticonfig --adapter=all --initial=dual-head
```(this creates a new xorg.conf, no need to touch it at all)

3. run: ```
sudo amdcccle
```and under Display Options, enable xinerama. Restart X.

Sorted! Teh Awesomeness!

---

