---
title: "Best video card for ubuntu?"
date: 2006-07-10
forum: Multimedia &amp; Video
---

### Post by findus on 2006-07-10
Hi,
This is my first post on this excellent forum, although I have been browsing for some time now.  

I have a Packard Bell PC which comes with an ATI Radeon 9100 IGP graphics card built into the motherboard.  From what I have read, there is no 3D acceleration possible with this card which although is a shame, I am prepared to upgrade my video card to be able to use XGL / Compiz (and Google Earth at a decent speed!).  IS there any particular card that people would recommend?  ATI or Nvidia?

I hope this isn't a duplicate post, I did do a search but couldn't find anything, don't mean to annoy anybody though if somebody has answered this question already.

Very grateful for any help

Fin

---

### Post by Master_J on 2006-07-10
I have ATI installed now, and from what I've learned is that to install the correct driver for ATI is like hell. I've heard that ATI doesn't release offisial drivers for Linux, whic Nvidia does.

So I would go for Nvidia. And I will, sometimes later this autumn :)

---

### Post by findus on 2006-07-10
Thanks for the quick reply, I think you are right with nvidia from what I have read. Is there a particular card that anyone can recommend as working well?

---

### Post by Miguel on 2006-07-10
Actually, ATi does provide official drivers for Linux. I am currently writing from a Xgl desktop running with an ATi Mobility 9600 Pro Turbo. Good enough for gnome-mines, Morrowind (win only) and Baldur's Gate 2 (both OS thanks to wine).

However, these are buggier than nVidia's and perform worse. As a level of performance, in Linux a 6600GT outperforms (or at least it used to) an X800. What's more, there hasn't been support for the ATi X1000 series for something like 6 or 7 months (it started a few fglrx releases ago). 

The issue with these drivers is that, being propietary, not only are they a pain to install but also might force you one day to older kernel-gcc combo.

Quick answers to quick questions:

Fastest linux card?
nVidia 7900GTX

Fastest open source linux card?
Intel GMA 950 (I think it outperforms the Radeon 9200)

As a final note, never ever buy the latest and greatest if you want to use it under linux. And never ever buy ATi.

---

### Post by findus on 2006-07-11
Thanks Miguel,

Been looking at prices for the nvidia card you recommended and think it might be out of my price range for the immdiate future, but I was looking at a NVidia Geforce 6 6600 LE that only costs £70.  Can anyone recommend this card as working properly with 3D acceleration?

Cheers!

---

### Post by Miguel on 2006-07-12
Hi again findus,

First of all, that card appears as supported for linux. You shouldn't have many troubles. Anyway, what are your plans for that video card? Are you interested in heavy gaming (quake4, doom3)? Light gaming (scorched3d, planet penguin racer)? Xscreensaver and Xgl only?

If you are interested on intensive gaming, you should consider getting a 660GT at least. But of course these cost more than 70 quid. For anything else, a 6600LE should be more than OK. I mean, the only other GPU-intensive game that will struggle on a 6600LE should be nexuiz.

Anyway, have a look at 6600GT prices. If they are around 15 quid more but you can afford it, go for them. They are some 50% faster so it would be a good deal.

---

### Post by streetmagix on 2006-07-12
hi,
i recommend the new 7-series graphics cards. I have a 7600GS although if your on a budget try a 7300GS, its fast, quiet and works well with linux. If you can afford a 7600GS/GT then i recommend them, 7600GS is passive (no fan) and cheaper.
If your on AGP then the 6600GT is a good card.
If you don't have a AGP or PCI-e slot (it does happen) then if you can find it, a 6200 PCI (not pci-express) is a good card, it is a stripped down 6600 and performs ok and is excellent in a media centre as it is doesn't have a fan. Becarfuly because my old 6200TC ran very hot, over 50c idle and 75c while gaming.
Hope this helps

---

### Post by findus on 2006-07-12
Thanks again for the really helpful replies.  My motherboard has an 8x AGP slot.  I am not really interested in playing games, I would just like to be able to have 3d acceleration supported (as it is not on the ATI 9100 IGP) and be able to run XGL etc.  Will look into the cards you guys mentioned and hopefully get one come pay day!  Thanks again for all your help guys,

Fin

PS There is no BIOS option to disable the onboard video card, but I assume that plugging a card into my AGP socket will disable the onboard graphics card?  Or will I be able to configure this through ubuntu?

---

### Post by streetmagix on 2006-07-25
hi,
i i recommend the nvidia 6200 AGP then, its avalble for £32 from here ([http://www.ebuyer.com/UK/product/104734)](http://www.ebuyer.com/UK/product/104734)). I had the PCI-e version for a while and it was great, then upgraded to the 7600GS (beast of a card). The 6200 is based on the 6600 and has a passive (no fan) heatsink, it thus gets quite hot, i have seen 70C+, too hot to touch so be a bit careful.
Hope this helps.

---

### Post by findus on 2006-07-25
Thanks for that, it looks ideal for what I need it for. Will let you know how I get on!

Fin

---

### Post by Frawg on 2006-08-02
nevermind, i found the answer to my question already =]

---

### Post by E-werd on 2006-08-02
GeForce 6600 has been the ticket for me.  It is not GT, LE, etc--just 6600.  I only paid like $90 USD in December 2005 for it from mwave.com.  Good card, runs everything really well and works in linux flawlessly for me, I have never had a driver problem (I went to this card for linux in the first place).

Check this out at newegg.com:
[http://www.newegg.com/Product/ProductList.asp?Order=PRICE&Page=1&N=2010380048&Submit=ENE&Nty=1&Subcategory=48&Description=6600&Ntk=all]("http://www.newegg.com/Product/ProductList.asp?Order=PRICE&Page=1&N=2010380048&Submit=ENE&Nty=1&Subcategory=48&Description=6600&Ntk=all")

Not sure if they ship to the UK, though.


ALWAYS REMEMBER: ATi is terrible with linux, ESPECIALLY with the Radeon 9000 Pro GPU.

---

### Post by findus on 2006-10-14
Finally decided to get a new card, but before I do, is it easy enough to disable the onboard ATI video card?  I'm not sure whether I can do it through the bios, so can Ubuntu disable the onboard graphics?  Would be grateful for any advice,

Thanks

Fin

---

### Post by xmastree on 2006-10-14
All recent boards I've had with onboard video will detect something in the AGP slot and disable the onboard.

---

### Post by nalmeth on 2006-10-14
@Miguel or anyone else who knows:
>  Fastest linux card?
nVidia 7900GTX

Fastest open source linux card?
Intel GMA 950 (I think it outperforms the Radeon 9200)
How well supported is that 7900GTX? It was released just in March/April was it not? A few searches bring up uncertain results.

I want to make the jump to more high-end video, currently frustrated with MX440.

---

### Post by MetalMusicAddict on 2006-10-14
> **nalmeth said:**
> @Miguel or anyone else who knows:

How well supported is that 7900GTX? It was released just in March/April was it not? A few searches bring up uncertain results.

I want to make the jump to more high-end video, currently frustrated with MX440.

The GTX should be fine if your using Edgy. Otherwise you need to use the drivers right from nVidia. I have a 7900GT.

---

### Post by nalmeth on 2006-10-14
> The GTX should be fine if your using Edgy. Otherwise you need to use the drivers right from nVidia. I have a 7900GT.
Cool, I'm not looking at upgrading *right* now, but by the time I have, I'll likely be using edgy full-time. Man, that card must just fly. My card works, but it's old, and just a cut under what I would really like to have.

Thanks for the input

---

### Post by MetalMusicAddict on 2006-10-15
> **nalmeth said:**
> Cool, I'm not looking at upgrading *right* now, but by the time I have, I'll likely be using edgy full-time. Man, that card must just fly. My card works, but it's old, and just a cut under what I would really like to have.

Thanks for the input

Yea. Its sick. I have it on my Dell 2405. ;)

I see you joined our team. [Ubuntu Studio]("http://ubuntustudio.org/"). :)

---

### Post by igknighted on 2006-10-15
The out of box support for ATI isn't great, but I feel like the fglrx drivers are way easier to deal with than the nvidia ones.  My ATI drivers were installed automatically with three terminal commands (while x was running even) and nvidia you have to quit out of X and go through their menus... not a big deal, just a pain really.  From what I can tell they require less nonsense when updating the kernel as well.  Perhaps I am an exception, the the FX-5500 I upgraded from was more finicky with linux than my x800

---

### Post by mattyj on 2006-10-15
Hello,

I have a nvidia 7900 GTX running the nvidia driver that comes in Dapper installed using the ubuntu guide  in a dual opteron machine driving two 20 inch monitors using Twinview.  I use it for scientific visualization  and it works very well. It took about 2 minutes to setup the driver, and a bit longer for me to figure out twinview.

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

At home I have one of the nvidia 7300 LE card and it also works well, although it is only driving one monitor, and doesn't move things around as fast.

I have not had good experience with ATI cards, but they are prevalent in laptops and folks are saying the newer drivers 8-29-6 are quite a bit better.  I am more of an end user so when I asked our developers they universally said nvidia was the way to go, but alot of that may be historically.

---

### Post by Miguel on 2006-10-18
I would strongly advice against ATi. How would I put it? I'm currently running edgy, and apart from a couple of car models for TORCS, java and flash it's mostly free. This means my ATi 9600 Mobility is running the open r300 driver instead of fglrx. Why?

Currently, r300 offers me:[list]
[*] Seamless integration and painless installation
[*] Supports latest kernel and X.org
[*] Hibernates perfectly
[*] Suspends perfectly
[*] It has dynamic clocking
[*] Even if it is in experimental state, it is more stable
[/list]

While fglrx would give me:[list]
[*] Twice the performance.
[*] TV-out if I learned how to config it.
[*] Statick clocking (I think powerplay is still not supported)
[*] Way more troubles
[/list]

I think it is pretty clear why I use r300 on a laptop. About performance, TORCS runs OK on my laptop. I know that it runs soooooo much faster in windows, and that it would run somewhere in between with fglrx, but I don't think it's worth the trouble.

IMHO, the only thing that could put me using fglrx again is crystallograph, a java3d API whose display is buggy under r300 but not under fglrx.

Ah! and under linux a 6600GT might give a X1900XTX a run for its money.

---

### Post by emax on 2007-04-05
> **Miguel said:**
> I would strongly advice against ATi. How would I put it? I'm currently running edgy, and apart from a couple of car models for TORCS, java and flash it's mostly free. This means my ATi 9600 Mobility is running the open r300 driver instead of fglrx. Why?

Currently, r300 offers me:[list]
[*] Seamless integration and painless installation
[*] Supports latest kernel and X.org
[*] Hibernates perfectly
[*] Suspends perfectly
[*] It has dynamic clocking
[*] Even if it is in experimental state, it is more stable
[/list]


Hi Miguel,

I'm looking to buy a laptop that comes with a 9600 and am keen to use the open r300 driver with it.

Is it possible to get AIGLX/[Compiz|Beryl] running with this card and the OSS drivers?

Thanks

---

### Post by Miguel on 2007-04-05
Hi emax,

Acutally, as of today, the open source r300 driver is your only way to get AIGLX to work. It is possible to get a compositing wm to work with the proprietary fglrx drivers, though, but it involves a bit of hacking to use Xgl. 

I must note that I'm not very impressed with the performance of compiz under r300. But on the other side I'm one of those "3d desktop doesn't convince me" kind of guys. You know, if I maximize or minimize the window, I want it to be *now*. However, it has improve a lot from dapper to edgy/feisty (I never tried compiz or beryl with Arch)

---

