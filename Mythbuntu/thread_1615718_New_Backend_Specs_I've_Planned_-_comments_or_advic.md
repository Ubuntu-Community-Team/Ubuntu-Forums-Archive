---
title: "New Backend Specs I've Planned - comments or advice welcome"
date: 2010-11-07
forum: Mythbuntu
---

### Post by rbeer on 2010-11-07
Currently happy with my mythtv setup which involves using an old Dell Optiplex as the backend saving all the files to a 1TB NAS with multiple frontends about the house. However the old dell isn't particularly quiet and does use a lot of energy so I'm planning to build a new server which will negate the need for a separate NAS. 

My main aim is to build a quiet-ish case (will live in a cupboard in the spare room) with low-ish power consumption (appreciate the conflict with processor etc) and to fit two dual DVB-T cards with 4TB now and the option to upgrade to 8TB later. I currently do my transcoding from my macbook pro so would like enough horse power on the backend to do this itself. The machine will also operate as backup for the other macs in the house (timemachine).

It's been years since I've built a machine so would genuinely appreciate any comments or feedback on what I'm proposing. Some of my many queries include should I bother to pay the £10 extra and get the AMD quad core at lower clock speed? Should I save money and just get 2GB of RAM? Am I just better of keeping the system I have and plugging an extra 2TB into my NAS? Should I be spending money on a better case? Are the parts even compatible together?

Proposed spec:
Case £39.98	Zalman Z7 Black Tower Case - Black (No PSU)
<span> http://www.novatech.co.uk/novatech/prods/components/cases/cases/zalman/z7.html</span>
CPU Cooler	14.99	Coolermaster Hyper TX3 CPU Coolerl
<span> http://www.novatech.co.uk/novatech/prods/components/cooling/cpucoolers/coolermaster/hypertx3.html</span>
Hard Drive 1 + 2 £77.98	Western Digital Caviar Green Power 2TB 64MB Cache Hard Disk Drive SATAII 300MB/s <8.9ms - OEM
<span> http://www.novatech.co.uk/novatech/prods/components/harddrives-internal/sataover1tb/westerndigital/wd20ears.html</span>
Motherboard £34.98	Gigabyte G31M-ES2L Intel G31 (Socket 775) Motherboard
<span> http://www.novatech.co.uk/novatech/prods/components/motherboards/intel775allchipsetmotherboards/gigabyte/ga-g31m-es2l.html</span>
RAM £56.99 Novatech 4GB (2x2GB) DDR2 PC2-6400C5 800MHz Dual Channel Kit
<span> http://www.novatech.co.uk/novatech/pråods/components/memory-pc/ddr2-pc2-6400/800mhz/novatech/ram-804gk.html</span>
PSU £32.99	Corsair CX 400W ATX2.2 Power Supply
<span> http://www.novatech.co.uk/novatech/prods/components/powersupplies/corsair/cmpsu-400cxuk.html</span>
Processor £62.98	Intel Dual Core E6600 2 x 3.06Ghz 2MB Cache 1066 FSB Dual Core Processor 
<span> http://www.novatech.co.uk/novatech/prods/components/processors/intelpentiumdualcore/intel/bx80571e6600.html</span>
Tuner Card £34.99	DVB-T PCI Dual tuner
<span> http://www.novatech.co.uk/novatech/prods/components/tvtunercards/PC1602T.html</span>

Total comes to £434

---

### Post by ian dobson on 2010-11-07
Hi,

The box doesn't look too bad. But why do you want a e6600? If the box is only going to be used as a backend and are not transcoding then maybe look at a e5300 45nm dual core cpu, to save abit of power.

You know that the ears drives are 4K sector drives, to get the best performance out of them you need to partition them so the the partition is on a 4k boundry (512byte sector,sector nr 64).

With regards the compatibility always buy everything from the same supplier and when you order just make sure you include a comment that all components will be used in one box.

Regards
Ian Dobson

---

### Post by rbeer on 2010-11-07
Ian, thanks for those comments. Very useful.

45nm processor does seem the sensible option. I did my selections from what was on my local suppliers website and they don't seem to have them listed. Might have to get one from elsewhere which is a shame as I wanted to get everything from one source.

Never thought about sectors and partitioning and must admit I don't really understand the issue. Do I even need to partition?

---

### Post by ian dobson on 2010-11-07
Hi,

Recomend partitioning your drives (with fdisk), leaving abit of space unused at the end of the disk (I do that as I have all my drives are several arrays and when I need to replace one I can garantee it won't be exactly the same size).

Have a look here, [http://www.tomshardware.com/reviews/wd-4k-sector,2554.html](http://www.tomshardware.com/reviews/wd-4k-sector,2554.html) they have a good description about 4k sectors.

Regards
Ian Dobson

---

