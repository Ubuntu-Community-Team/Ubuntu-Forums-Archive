---
title: "Is it getting worse or is it just me?"
date: 2010-06-12
forum: Multimedia Software
---

### Post by argonaut747 on 2010-06-12
Maybe saying Ubuntu is getting worse is unfair. I'm not a big user I have to say. I use it more out of curiosity than anything else. I first used 8 and it was brilliant. I told all my mates about it. Everything work great. I had all desktop effects. I could use a KDE session. Then I upgraded to 9 and lost KDE ability but still had all desktop effects available. Upgraded to 10 a few weeks ago and now no desktop effects.
Non of the above is a problem but I feel like, for me, it's going backwards.
I use an old AMD 2600 machine with  a Radeon 9600. I used to be able to use ATI Catalyst but that didn't work after the upgrade to 10 and I can't seem to find a solution.
Ubuntu is still brilliant but I don't like things being taken away from me.
However, it's free and I really do appreciate all the hard work and time that goes into it. This is not a complaint in any way.

---

### Post by argonaut747 on 2010-06-12
Just read a very clear explanation of my issue from Icarus315 in another thread. It's all down to ATI not supporting my card under the new disro.
Oh well. If I want wobbly windows again I guess I have to get another card. Any suggestions? I'm not a gamer so it doesn't have to be too funky :-)

---

### Post by CharlesA on 2010-06-12
Sounds like you've got an old AGP or PCI card, it wouldn't really be worth upgrading unless you've got a pcie slot.

---

### Post by Mark Phelps on 2010-06-14
> **argonaut747 said:**
> Maybe saying Ubuntu is getting worse is unfair. I'm not a big user I have to say. I use it more out of curiosity than anything else. I first used 8 and it was brilliant. 
Agree -- 8.04 was the best distro version, ever.

>  Upgraded to 10 a few weeks ago and now no desktop effects.
I also have a Legacy ATI card but since it's newer (x1650), it DOES get desktop effects.  Thought the open source drivers supported ALL ATI cards; maybe they don't.

> I use an old AMD 2600 machine with  a Radeon 9600. I used to be able to use ATI Catalyst but that didn't work after the upgrade to 10 and I can't seem to find a solution.
Ubuntu is still brilliant but I don't like things being taken away from me.
Understand your concern ... it affected me too ... but AMD/ATI were the ones that did this, not Canonical. At that time, they dropped support in the MS Windows community as well ... but since then, they've returned to supporting the legacy cards, just not as often as the current cards.

---

### Post by cascade9 on 2010-06-14
> **CharlesA said:**
> Sounds like you've got an old AGP or PCI card, it wouldn't really be worth upgrading unless you've got a pcie slot.

That depends. 

Sure, PCIe has a lot more range of cards avaible, and they are cheaper. But there are some fairly cheap AGP/PCI cards that have current support (Geforce 6200s, ATI 2XXX/3XXX/4XXX). 

Not that I have to buy AGP cards, I've got lots of access to 2nd hand cards. 

> **Mark Phelps said:**
> I also have a Legacy ATI card but since it's newer (x1650), it DOES get desktop effects.  Thought the open source drivers supported ALL ATI cards; maybe they don't.

They do, sort of. There are 2 different open source drivers avaible- xserver-xorg-video-radeon (for all the radeon and fire-xxxx cards) and xserver-xorg-video-ati (for radeon, fire-xxxx, mach64 and rage128 cards).

---

### Post by argonaut747 on 2010-06-14
Thanks for all the response guys :-)
I'm thinking of going back to 8. It all just felt right then.
I really do appreciate it's not the fault of the developers. As I said before they are all doing a great job..
I may even have a compatible card somewhere. I'll have to dig through my old stuff and see.
Be good. If you can't be good be careful ;-)
Jase

---

### Post by doas777 on 2010-06-14
i think it's getting better and better, but at the same time, it's harder and harder to run it on older hardware.

---

### Post by The Flying Penguin on 2010-06-14
I feel your pain regarding the ATI issue. I have two HTPC that are hooked to SD televisions and each uses older ATI legacy cards. Since these are HTPCs I need full card support especially S-video and component out. Sadly, ATI's propriatary drivers for the legacy cards no longer work under newer versions of Ubuntu and they show no interest in releasing updated drivers that will work. Because of this I am forced to run XP on these two machines. Oh well, they are just HTPCs. Maybe I'll try throwing 8.04 on them one day and see how that works.

My last laptop/netbook, a MSI U210, had an ATI Radeon x1270. I was just dabbling in Linux before I bought it and shortly after I decided to really make the plunge and completely switch over (except for games). Sadly, I soon found out that I couldn't use the card to its full potential under Karmic because of the driver issue. Video performance was weak and gaming was just out of the question.

ATI's foolishness not to release an updated driver that supports its legacy cards under newer Linux kernels could potentially cost them customers. Case in point? Me!

Barely six months after buying my MSI u210, I sold it and bought an Asus ul30vt. The main reason for this was because I wanted a laptop with full Linux support and because of ATI, my last MSI failed to meet such a demand. I looked at several different laptops in my search and had to ignore several that I would have purchased if it was not for the ATI legacy cards they came with, specifically the 3200. Now, I am quite happy with my ul30vt, which sports a Hybrid Intel 4500mhd and Nvidia G210M. Sure I can't switch between them with the push of a button like I can in Win 7 but I least the G210 enjoys virtually full support under Lucid, even video acceleration (vdpau) works!

As a businessman and end user, it just irks me that ATI ignores the needs of such a large customer base. With so many users still using legacy cards you would think ATI would have a desire to take care of them. Perhaps ATI reasons that this will force people to go out and buy new ATI cards but what of the people who don't buy ATI this time around in protest? And what of simply taking care of your customers? Just because they are still running older hardware doesn't mean they are any less valuable as those purchasing new hardware.

Furthermore, with all these low cost netbook/laptops that use the 3200, x1270 and other ATI legacy cards, one would think it would be in ATI's interest to support these cards so users like me don't just skip over those products. I think these laptops are potential magnets, so to speak, for Linux because many users may be unhappy with the performance Windows 7 offers on such limited hardware so it just seems natural ATI would recognize this and offer support.

I think the manufacturer's lack of cooperation is what is often to blame for things getting "worse" with new iterations of various Linux distributions. I have generally found, that in most areas, everything seems to get better with each new release of Ubuntu. More hardware works out of the box, stupid problems I couldn't resolve suddenly go away, as the distro grows in popularity more support and software becomes available, etc.


PS. I may never buy another ATI product again.  I have three ATI cards running in my machines, two of which are legacy. I don't know what Nvidia's track record is for keeping up support for older cards but I may just stick with them for now on. I just bought an ATI HD(something or other) this last year for my HD HTPC. I wonder how long that will be supported under Linux. With Nvidia's vdpau and ATI's support issues, I don't see much of a reason to buy another ATI card again.

---

