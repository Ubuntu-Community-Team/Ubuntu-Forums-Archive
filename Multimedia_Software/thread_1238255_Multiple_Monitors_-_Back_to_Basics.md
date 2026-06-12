---
title: "Multiple Monitors - Back to Basics"
date: 2009-08-12
forum: Multimedia Software
---

### Post by AlanRogers on 2009-08-12
There is a great deal of very detailed, and therefore complex, help here on these fora relating to the above topic - I know because I found it all whilst attempting to search for the answer to my question before resorting to posting.

I'm looking to rationalise my computing arrangements, from three boxes and one monitor to one box and three monitors. The box in question already exists but doesn't yet have multiple monitor capability.

I intend to run Ubuntu with VMWare Server or similar on it, so that I can have different virtual machines open on different screens. Before I can achieve this, I need to buy an appropriate graphics card.

Bearing in mind the above stated intent, the first question is therefore which supplier:

[LIST]
[*]ATI
[*]Matrox
[*]nVidea
[/LIST]
I want the least amount of pain but I'm quite happy to get my hands dirty in the CLI or config files. Basically, I want to buy it, set it up and then forget all about it!

I'd prefer cited examples please, rather than hypothesis and opinion. Opinions are great, but I'm going to spend money and time, so real-world advice will count for more.

Thanks in advance

---

### Post by markbuntu on 2009-08-12
I am currently using three monitors (20 wide screen 1680x1050, 24 wide screen 1920x1200, 19 standard 1280x1024) with ati HD3650 and HD3450 PCIE cards running the latest proprietary fglrx driver 9.7. I configured them with the Catalyst Control Center which comes with the driver. No file editing needed. I could easily set up a 4th monitor if I had one and someplace to put it. Apparently this will work with any combination of HD3xxx and HD4xxx cards but not with all integrated gpus.

Each screen is independent and runs at its native resolution and I can drag windows across them all. No desktop effects available with this setup and I do not use VMWare so I can't say if it will work or not. The driver is making use of xinerama since randr1.2 has problems with multiple gpus.

The ati drivers have improved enormously over the last year and I expect that will continue.

Anyway, that is my experience.

I know that nvidia has the capability but I have no idea how easy it is.

---

### Post by AlanRogers on 2009-08-12
This is exactly the kind of information that I'm looking for, and it's even more hopeful than I dared think it might be. No need to edit config files and it just worked? That's what we like to hear! 

It looks like I'll be wanting something like the HD4850 but I'll wait to see what else comes back on this thread first.

---

### Post by AlanRogers on 2009-08-31
Bump

---

