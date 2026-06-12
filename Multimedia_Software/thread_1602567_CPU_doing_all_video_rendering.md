---
title: "CPU doing all video rendering"
date: 2010-10-21
forum: Multimedia Software
---

### Post by daphatgrant on 2010-10-21
Hello, I am completely new to Ubuntu and so far am pretty happy. I am running into an issue playing web videos, youtube (flash) as well as html5.

What is happening is that the CPU is doing all the work instead of the GPU causing the video to skip/stutter, here are the system specs.

MSI K7N2 Delta 2 LSR (latest bios)
AMD Athlon XP 3000+ (Barton) 
2GB's PC3200
nVidia 6800GT (AGP)
Ubuntu 10.10 32bit (fresh Install
nVidia driver 260.19.06

When video is played the CPU's useage climbs to 100% and video lags. Again I am completely new to Ubuntu as well as Linux but I am trying, lol.

If anyone has any info I'd gratefully appreciate it, thanks :).

---

### Post by SeijiSensei on 2010-10-21
Only NVIDIA cards in the 8xxx and higher series can support hardware video decoding via the VDPAU interface.  Even with qualifying cards, Adobe Flash does not use VDPAU when playing videos, though media players like SMPlayer can.  

Something like [this]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814187114") or [this](http://www.newegg.com/Product/Product.aspx?Item=N82E16814150322) would help.

---

### Post by daphatgrant on 2010-10-21
Thanks for the quick response!:)

I've got an ATI Radeon 8500 and a Sapphire X1550 laying around, are either of these good alternatives? If not I have no problem buying a different card, maybe something like [this]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814161152") or [this]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814102862") but it has to be either AGP or PCI, thanks again for the quick response :).

Another note is that is is primarily an email and internet machine, there won't be any games on this other than solitaire.

---

### Post by cchhrriiss121212 on 2010-10-21
With that system you could try switching to a lighter OS like Lubuntu which would save on resources. An easier trick is to try this out:
[https://addons.mozilla.org/en-US/firefox/addon/161869/](https://addons.mozilla.org/en-US/firefox/addon/161869/)

---

### Post by Yellow Pasque on 2010-10-21
> **daphatgrant said:**
> I've got an ATI Radeon 8500 and a Sapphire X1550 laying around, are either of these good alternatives?

They won't speed up your Flash video, but the X1550 should use significantly less power than the 6800GT (and has the potential to be quieter). The 3D won't be as good, but if you're just playing solitaire..

---

### Post by daphatgrant on 2010-10-21
> **Temüjin said:**
> They won't speed up your Flash video, but the X1550 should use significantly less power than the 6800GT (and has the potential to be quieter). The 3D won't be as good, but if you're just playing solitaire..

Might be worth getting that Radeon 9250 then. My main goal is to get a card that will process the video instead of the the CPU doing it, it's a shame that 6800GT isn't supported.

---

### Post by Yellow Pasque on 2010-10-21
A Radeon 9250 is worse than an X1550 and a waste of money. If you're going to spend money, you should try to find the GeForce 8400GS (G98 chip) PCI edition. At least this will support VDPAU playback if you use the plugin that cchhrriis linked to. You could also use an open-source Flash alternative like Lightspark which supports decode acceleration through va-api (and the vpdau-video backend found here: [http://www.splitted-desktop.com/~gbeauchesne/](http://www.splitted-desktop.com/~gbeauchesne/) ), though you should note that lightspark isn't release-quality yet.

EDIT: Something like this: [http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=4104561&CatId=1603](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=4104561&CatId=1603)
You can probably find it used and/or cheaper if you look hard enough.

---

