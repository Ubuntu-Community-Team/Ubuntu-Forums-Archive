---
title: "Any idea if 11.04 will run on my creaky old laptop?"
date: 2011-03-29
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by peyre on 2011-03-29
My laptop is over ten years old, but it's a business model and just chugs along beautifully.  It's slow and limited, but I use it basically like a netbook--it's all I really need in a laptop.  Plus I'm having all kinds of fun keeping it going on *buntu.

It runs 10.04 just fine, but wouldn't run 10.10 reliably, so I have it now on Lubuntu 10.04.  I'd like to take advantage of the improvements in 11.04 when it comes out, especially the speed advantage offered by the new kernel, but my experience with 10.10 suggests I might have trouble.

The Lubuntu Wiki says that "[support for i586 chipsets has been dropped from the kernel for the 10.10 series (These include VIA C3, AMD K6, National Semiconductor and AMD Geode)]("https://wiki.ubuntu.com/Lubuntu#Older%20i586%20class%20CPUs")", and I'm wondering if that's my problem--that my CPU is one of those that's been discontinued.  I don't think so, but I'm not sure, and I'm hoping someone else might have more of a clue about this.

This is a Toshiba Tecra 8100; it's a Pentium III machine (with 512MB of RAM) but I don't know much about the processor.  Detailed specs are available [here (click on the Detailed Specs tab)]("http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/modelContent.jsp?ct=SB&os=&category=&moid=1073769806&rpn=PT810U&modelFilter=&selCategory=2756709&selFamily=1073768664").

---

### Post by mörgæs on 2011-03-29
I don't think there is any speed improvement for a single-core processor, so maybe it is not a bad idea to stick to Lubuntu 10.04. 

This might be of interest:
[http://ubuntuforums.org/showthread.php?t=1712629](http://ubuntuforums.org/showthread.php?t=1712629)

The i586 family is seriously old stuff:
[http://en.wikipedia.org/wiki/I586](http://en.wikipedia.org/wiki/I586)
Your Pentium 3 is not out in the cold...

---

### Post by peyre on 2011-03-29
> **mörgæs said:**
> I don't think there is any speed improvement for a single-core processor, so maybe it is not a bad idea to stick to Lubuntu 10.04. 

Really?  That's disappointing--I thought the famous 200-line edit made some typical desktop I/O operations more efficient, which would presumably give a little boost to any processor.  I must have misread or misunderstood somewhere.  But if that's the case, it would make me feel less like I'm missing out on something if 11.04 doesn't work right on this old thing.

> **mörgæs said:**
> The i586 family is seriously old stuff:
[http://en.wikipedia.org/wiki/I586](http://en.wikipedia.org/wiki/I586)
Your Pentium 3 is not out in the cold...

Oh, that's good to hear.  That's what I thought too, but I wasn't certain.

---

### Post by uRock on 2011-03-29
Moved to NNT&D.

---

### Post by jerrylamos on 2011-03-29
I've got Natty running on an older laptop with 512 MB memory so you might have a shot at it.

It should run "Classic"  I'd recommend "no effects" because "Compiz eye candy" uses up a lot of cycles.

I'm having good luck with Unity 2D on my older pc's, see:

[https://launchpad.net/~unity-2d-team/+archive/unity-2d-daily](https://launchpad.net/~unity-2d-team/+archive/unity-2d-daily)

Took a little fiddling around, not too much.  Looks like Unity 3D but uses less resources and runs on older pc's.  The "eye candy" Unity 3D only runs on the latest pc's.

By the way, the Natty to use is the i386 from:

[http://cdimage.ubuntu.com/cdimage/daily-live/current/](http://cdimage.ubuntu.com/cdimage/daily-live/current/)

which is getting close to Beta, due out 31 March or shortly thereafter.

Good luck, Jerry

---

### Post by IWantFroyo on 2011-03-29
Try it! The beta's coming out soon. I had a lot of problems with 10.10 too (laptop won't boot without pci=noacpi). 11.04 does require edd=on to run unity correctly, but it's a major improvement.
I would, however, recommend that you install a XFCE environment soon after. Unity requires a heck of a lot of power (noveaux [sorry if mispelled] wouldn't work for it.]).

---

### Post by peyre on 2011-03-29
Dudes!  I'm way ahead of you on one point: Compiz on a PIII 600MHz?  I wouldn't even try it.  I don't go for all that eye candy nonsense anyway, frankly.  And no Unity or even Xfce - I'm running **Lubuntu** (LXDE) on this thing!

Thanks for the link.  I'll definitely try it, but I'll probably wait till it's officially released.  I'm not enough of an early adopter to try it in beta on a working laptop.

---

### Post by ronacc on 2011-03-29
compiz is more about your video card than your cpu , but with a laptop of that vintage your gpu probably would really groan under the load .

---

### Post by peyre on 2011-03-30
> **ronacc said:**
> compiz is more about your video card than your cpu , but with a laptop of that vintage your gpu probably would really groan under the load .

Exactly.  I'm trying to put as little load on the system as possible, while still having a full-fledged user environment.  In other words, I want the most lightweight GUI I can run that doesn't make me drop to a terminal all the time.  So I wouldn't go all the way to a really bare-bones GUI like Fluxbox), but I'm glad to go without fancy stuff like desktop effects.

---

### Post by jerrylamos on 2011-03-30
> **IWantFroyo said:**
> Try it! The beta's coming out soon. I had a lot of problems with 10.10 too (laptop won't boot without pci=noacpi). 11.04 does require edd=on to run unity correctly, but it's a major improvement.
I would, however, recommend that you install a XFCE environment soon after. Unity requires a heck of a lot of power (noveaux [sorry if mispelled] wouldn't work for it.]).

Unity 2D from Synaptic appears to run just fine on my older slower pc's.  I run "Classic no effects" just long enough to load Unity 2D and go from there.

Jerry

---

