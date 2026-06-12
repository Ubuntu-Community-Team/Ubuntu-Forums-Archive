---
title: "Xonar DX support?"
date: 2008-05-03
forum: Multimedia Software
---

### Post by Dolphin on 2008-05-03
How's the Xonar DX (Not D2X) working on a fresh 8.04 install?
Does it work?  If not, does it work if you update ALSA?

---

### Post by cdw38 on 2008-05-04
Looks like [all of the Xonar cards were [hardware] feature-complete in ALSA]("http://www.alsa-project.org/main/index.php/User:ClemensLadisch") as of 04-15-2008, so you should be all set.  I am planning on replacing my X-Fi with one of these as soon as next week.

---

### Post by syxbit on 2008-05-10
let us know how it goes.
i'm not risking buying one until someone confirms it works flawlessly in 8.04 (preferably with no recompiling ALSA 1.0.16)

---

### Post by symbiont on 2008-05-13
I bought one two weeks ago.  Could not get it to work in Ubuntu 8.04.  If someone can I'd like to know how also.  In the meantime, it works wonderfully in XP and my XFI is enjoying its place in a landfill somewhere.

Edit:  didnt read the above post totally, I guess I'll have to try to update alsa, but it doesnt not work on a fresh install.

---

### Post by cdw38 on 2008-05-17
Doesn't work on fresh install for sure.

I am using the beta driver found in my previous link (4/15/2008 one) and following the directions [here]("http://www.alsa-project.org/main/index.php/Matrix:Module-virtuoso") , but get this error at "make":

> xxxx@xxxxxxxxxxxxx:/usr/src/alsa/alsa-driver-20080415# make
if [ ! -d include/sound -a ! -L include/sound ]; then \
	  ln -sf ../alsa-kernel/include include/sound ; \
	fi
cp -puvf include/version.h include/sound/version.h
`include/version.h' -> `include/sound/version.h'
make dep
make[1]: Entering directory `/usr/src/alsa/alsa-driver-20080415'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-20080415/acore'
copying file alsa-kernel/core/info.c
/usr/src/alsa/alsa-driver-20080415/utils/patch-alsa: 24: patch: not found
make[2]: *** [info.c] Error 1
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-20080415/acore'
make[1]: *** [dep] Error 1
make[1]: Leaving directory `/usr/src/alsa/alsa-driver-20080415'
make: *** [include/sndversions.h] Error 2


I am pretty much a newb, so does anyone have any ideas there?  Could it be a kernel problem, it says in the SUPPORTED_KERNELS file (when you unzip the drivers) that it has only been tested on vanilla 2.6.23 or earlier?  I will try compiling a new 2.6.23 kernel tomorrow and report back unless anyone has a better idea...

Thanks for any help

---

### Post by YogiPaolo on 2008-05-28
I can confirm that the Xonar DX does NOT WORK.

It's non-functional using every method described in the "comprehensive sound problems guide". This includes compiling the latest alsa drivers from the alsa site.

[http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound)

All modules compile cleanly and the card is seen using lspci. The module loads, but no dice.

---

### Post by orlfman on 2008-07-06
Has anyone been able to get it to work in Ubuntu? I have it working perfectly fine in Gentoo, but been wanting to switch over to Ubuntu.

---

### Post by Trollslayer on 2008-07-13
I have a D2 (not D2X but there shouldn't be any difference). Analogue outputs work **but** the SPDIF doesn't.
Using ALSA 1.0.16/Mythbuntu 8.04 digital always shows in 'aplay -l' and sometimes in 'aplay -L' but the optical output never switches on.
I tried install ALSA 1.0.17rc3 but it didn't compile properly.

---

### Post by live2sk8 on 2008-09-01
> **orlfman said:**
> Has anyone been able to get it to work in Ubuntu? I have it working perfectly fine in Gentoo, but been wanting to switch over to Ubuntu.

Sorry for such a long delay, but I finally upgraded my kernel today from 2.6.25.4 to 2.6.26.3, and my DX now works perfectly on the analog outputs (without anything special, just popped in the new kernel and !! it sounds great).

I sounds great compared to the integrated audio I was using while being too lazy to upgrade kernels.  I moved to this card from an X-Fi Platinum, but it's honestly been ~8 months since I've used the X-Fi and Windows, so its hard to compare.  I can say with 100% certainty it sounds 100x better than the X-Fi on the original beta 64-bit drivers (100x easier to set up too now that ALSA supports it).  The bass is unbelievable on these, though.  I remember the X-Fi first blowing me away due to how crisp it was, but I don't think the X-Fi sounded this good on the lows (I don't really listen to rap, so I'm talking about big thumps, but saying that you can really hear the bass from this card).

[I am using a set of Logitech X-2300s with these]

If anyone has questions, let me know.

---

### Post by cdw38 on 2008-09-01
> **live2sk8 said:**
> Sorry for such a long delay, but I finally upgraded my kernel today from 2.6.25.4 to 2.6.26.3, and my DX now works perfectly on the analog outputs (without anything special, just popped in the new kernel and !! it sounds great).

I sounds great compared to the integrated audio I was using while being too lazy to upgrade kernels.  I moved to this card from an X-Fi Platinum, but it's honestly been ~8 months since I've used the X-Fi and Windows, so its hard to compare.  I can say with 100% certainty it sounds 100x better than the X-Fi on the original beta 64-bit drivers (100x easier to set up too now that ALSA supports it).  The bass is unbelievable on these, though.  I remember the X-Fi first blowing me away due to how crisp it was, but I don't think the X-Fi sounded this good on the lows (I don't really listen to rap, so I'm talking about big thumps, but saying that you can really hear the bass from this card).

[I am using a set of Logitech X-2300s with these]

If anyone has questions, let me know.
This was me, didn't realize I had more than one account :lolflag:

---

### Post by syxbit on 2008-09-05
i'd like to buy the D2X.
but it's PCIe. maybe i'll risk it :)

---

### Post by dmy on 2008-09-08
Asus D2X Xonar PCIe here on hardy 64 bits.
Analog & Digital work perfectly.

I use a custom 2.6.26.3 (Sound only enabled without drivers) and Alsa drivers from :
[http://www.alsa-project.org/main/index.php/User:ClemensLadisch](http://www.alsa-project.org/main/index.php/User:ClemensLadisch).

It should however work with any kernel >= 2.6.26.
I did not test with hardy included 2.6.24 kernel (had the card latter).

---

### Post by Sean4000 on 2008-09-09
I am toying with the idea of purchasing the Xonar D1 but my Kernel version is only 2.6.24-19-generic. I do not want to compile a custom kernel so what is the workaround?

---

### Post by syxbit on 2008-09-12
wait 6 weeks until intrepid. then it should work

i just found out it needs an additional floppy power connector (it's just a pci to pcie bridge, so i no longer want one)
seriously external FLOPPY power connect!!
i don't even have one on my PSU, and i can't be bothered with stupid adapters

---

### Post by dmy on 2008-09-29
You're right, this floppy connector is quite disappointing.

It's also a trap as forgetting to plug it makes the sound card seems to work perfectly (detected), but without any output...

But modular PSU generally have one, and an adaptator is almost costless.
Moreover, despite the appearances, the D2X has much improved over the D2 (I did not compared myself):

[http://www.elitebastards.com/cms/index.php?option=com_content&task=view&id=496&Itemid=27&limit=1&limitstart=2](http://www.elitebastards.com/cms/index.php?option=com_content&task=view&id=496&Itemid=27&limit=1&limitstart=2)
[http://www.elitebastards.com/cms/index.php?option=com_content&task=view&id=496&Itemid=27&limit=1&limitstart=5](http://www.elitebastards.com/cms/index.php?option=com_content&task=view&id=496&Itemid=27&limit=1&limitstart=5)

At the end, I'm very satisfied with this sound card, and there are not so much good alternatives in PCIe.

With a 2.6.24, only adding recent ALSA drivers should likely be enough.

---

### Post by aditirex on 2008-10-23
Xonar DX in Intrepid beta works out-of-box for me :)

---

### Post by Dewni on 2010-01-21
Okay okay, I know this is a really late reply, but I thought it would be good to let anyone that comes across this forum know that on Ubuntu 9.10 x86-64 the Xonar DX (the pci-e version) works brilliantly.
lspci says

```
02:00.0 PCI bridge: PLX Technology, Inc. PEX8112 x1 Lane PCI Express-to-PCI Bridge (rev aa)
03:04.0 Multimedia audio controller: C-Media Electronics Inc CMI8788 [Oxygen HD Audio]
```

And before I forget: the sound quality beats my onboard Realtek ALC888, hands down!

---

### Post by slimsido on 2010-02-01
Hello I'm using ubuntu jaunty, i have a xonar dx,  I installed latest Alsa drivers and spdif works now, but I'm not able to regulate the volume, it remain always the same also using alsamixer....There is a way to configure pulseaudio for work with latest alsadrivers?
thank you and sorry for my bad english...

---

