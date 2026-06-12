---
title: "Anyway I can install Ubuntu on my phone ?"
date: 2013-12-16
forum: Mobile Technology Discussions (CLOSED)
---

### Post by linuxyogi on 2013-12-16
Hi,

Recently I have purchased [this phone]("http://www.gsmarena.com/nokia_asha_501-5445.php").

By any chance is it posible to install Ubuntu on this phone ? 

If not, are there any future plans of realeasing a version of Ubuntu for this kind of hardware ?

---

### Post by raja.genupula on 2013-12-16
No you can not.

[https://wiki.ubuntu.com/Touch/Devices](https://wiki.ubuntu.com/Touch/Devices)

---

### Post by darkcarnage01 on 2013-12-19
raja.genupula, So is this the latest dev info on builds? Doesn't look like much dev work to date.. Is that because of Ubuntu's One Touch hardware platform?

---

### Post by Sparrow40k1 on 2014-01-14
Why can't they make Ubuntu Phone OS like the desktop Ubuntu, where you can install the one image on any machine and plug and play drivers work until you download drivers?
I am not very experienced with this detailed stuff and I'm sure there must be a reason, but would be a great idea!

---

### Post by 3rdalbum on 2014-01-15
> **Sparrow40k1 said:**
> Why can't they make Ubuntu Phone OS like the desktop Ubuntu, where you can install the one image on any machine and plug and play drivers work until you download drivers?
I am not very experienced with this detailed stuff and I'm sure there must be a reason, but would be a great idea!

It would be a great idea, and there's a great reason why it's not done.

PCs are an open architecture; many of the important bits can communicate using industry standards, and it's easy to actually boot your computer from something other than your hard drive because so much of your computer is based around standards - either ratified standards or "de-facto standards" (things that aren't really standards, but everyone does things the same way on purpose).

Mobile phones and tablets are so incredibly different. They are only designed to run the operating system that's baked into flash memory, and the bootloaders of those operating systems are usually locked so they will only boot the approved operating system. The internal components all require special drivers to do anything at all; it's not like the internal video hardware of a phone can operate in VESA mode, it REQUIRES the right driver. If you're lucky you might be able to get text to display without a specific driver. And don't get me started on radios or touchscreens. You can't just plug in a PS/2 keyboard and mouse either.

In addition, there are several different binary-incompatible types of ARM CPU. Binaries compiled for one will not work on another. Of course, the kinds of components used in phones are very different to PC components, so you can't just take the source code for your desktop wifi card and use it to drive a mobile wifi chip.

Android phones have a completely different bootup sequence and method of communication than Windows Phones, iOS, Blackberries or Symbian phones; unlike the PC where they all use BIOS or EFI and the bootup sequence on a Dell is exactly the same as on an HP or a homebuilt PC.

That's why it's virtually impossible to do what you say. And that's why Ubuntu can only be installed on SOME Android phones, but NO non-Android phones. Getting Ubuntu to run on Android phones is a massive-enough challenge without trying to tackle the mechanics of a completely different type of phone like an Asha. And that's assuming that a Nokia Asha has enough CPU power and RAM to run anything like Ubuntu.

---

### Post by Don_Stahl on 2014-01-15
Nice explanation, 3rdalbum! 

D'you think phones will --

1. Become standardized internally in the way PCs are -- processor, screen, transceiver all using standard protocols and drivers?
2. Or will phones migrate to being tiny PCs with core compatibility with Intel/AMD chipsets and drivers?

Or neither?

---

### Post by 3rdalbum on 2014-01-16
> **Don_Stahl said:**
> Nice explanation, 3rdalbum! 

D'you think phones will --

1. Become standardized internally in the way PCs are -- processor, screen, transceiver all using standard protocols and drivers?
2. Or will phones migrate to being tiny PCs with core compatibility with Intel/AMD chipsets and drivers?

Or neither?

Neither. I think the reason the PC was fairly well open was because computers were still for tweakers, and the IBM clone manufacturers needed to copy eachother and IBM to remain compatible. Diverging from IBM whenever it was too costly or too proprietary and troublesome to copy. Neither of those factors apply with phones and there is no percieved benefit to standardising amongst manufacturers.

And currently, Intel's Atom mobile CPUs cannot match what a good ARM CPU can do. AMD's are even worse. There is also no percieved benefit to x86 in mobile phones. The collection of software for x86 PCs was a big reason to keep using x86 on PCs, but that collection of software is impractical on a phone anyway regardless of CPU. If Microsoft developed a convergence Superphone, I'm sure Intel would be there. Otherwise, normal phones will use ARM CPUs for a long, long time yet.

---

### Post by sanderj on 2014-01-20
> **3rdalbum said:**
> Neither. I think the reason the PC was fairly well open was because computers were still for tweakers, and the IBM clone manufacturers needed to copy eachother and IBM to remain compatible. Diverging from IBM whenever it was too costly or too proprietary and troublesome to copy. 

Maybe you're already implying this: and *because* DOS was closed source. So a PC manufacturer just had to make the hardware compatible with the original IBM PC standard hardware, or it couldn't run DOS (and thus the DOS programs) at all.

Hmmm ... interesting. An advantage of closed source. So a **disadvantage** of open source is that you can change the underlying hardware (and modify the operating system to your needs), resulting in no standard hardware.

So the near-monopoly of Microsoft in the past 25 years has had its advantages: no need for discussions what standard to use: just the Wintel standard. ;-)

Please make no mistake; I don't like Microsoft too much and I've switched to Linux and OSS in 2000, but I'm just trying to make an analysis here.

---

### Post by leclerc65 on 2014-01-20
>  just the Wintel standard.
Their downfall is power consumption.
A mobile device which cannot last for a day will auto destruct.

---

### Post by mimilovell on 2014-02-21
shame. I was looking forward to downloading it on my phone

---

