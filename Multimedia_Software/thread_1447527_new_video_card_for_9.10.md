---
title: "new video card for 9.10"
date: 2010-04-05
forum: Multimedia Software
---

### Post by albert s on 2010-04-05
hi, I running 32 bit 9.10 on a dual core PC,
my current video card is an Nvidia GEforce 7500,
Id like to upgrade this for when I install Lucid, my motherboard is maxxed out at 1G of RAM so hopefully I can get something that can handle the graphics without using my RAM.
Im in the UK and ideally budget of £40/£50 tops. (about $80US ?)
my PC isnt really worth spending much more on.
any ideas on what I could get for this sort of money?
Im pretty new to stuff like this so please be gentle.  :)
thanks.

---

### Post by gordintoronto on 2010-04-05
Can I make an assumption that the video card must go in a PCI slot?  Something like this:
[http://www.newegg.ca/Product/Product.aspx?Item=N82E16814133245](http://www.newegg.ca/Product/Product.aspx?Item=N82E16814133245) 
would do.
It's not wonderful, but it won't use the motherboard RAM.

You didn't mention what applications you use, which is an important factor in choosing a video card. The one I mentioned is fine for web and office applications, not so great for high-end games.

---

### Post by albert s on 2010-04-05
sorry gordintoronto, my error.
I dont do any gaming, just a few videos from youtube etc and the like.
my current card seems ok for my use, just it seems to hammer the cpu/ram a bit at times and the video snags on occasion,(same downloaded video will at other times play fine if Im doing nothing else needing graphics).
looks good and well within my budget too.
how can I tell(short off opening the case and looking) if I have a pci-e or an AGP slot?

   *-pci:2
             description: PCI bridge
             product: P4M890 PCI to PCI Bridge Controller
             vendor: VIA Technologies, Inc.
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress pm msi ht bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:49 ioport:a000(size=4096) memory:dfb00000-dfbfffff ioport:dfe00000(size=1048576)


^^^ is this PCI-E  slot.?


      *-display
                description: VGA compatible controller
                product: G72 [GeForce 7500 LE]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:24 memory:dc000000-dcffffff memory:c0000000-cfffffff(prefetchable) memory:dd000000-ddffffff memory:de000000-de01ffff(prefetchable)


^^^ my current graphics.

thanks.

---

### Post by gordintoronto on 2010-04-05
I am not sure how you could be certain what kind of slot your video card is in without opening the case. I would open the case! Then I wouldn't be surprised if it's a PCI express slot, based on what is listed under "resources".

You could also consider shopping on eBay. People who upgrade are often happy to see the old unit go to a good home for 10 of the local currency.

If the video card was original equipment in a name-brand computer, the manual would probably say. Most (old) computer manuals are downloadable.

Good luck!

---

### Post by albert s on 2010-04-06
thanks gordintoronto.
I'll open her up at the weekend then e.bay it shall be.  :D

---

