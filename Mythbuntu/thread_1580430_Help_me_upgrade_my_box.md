---
title: "Help me upgrade my box"
date: 2010-09-23
forum: Mythbuntu
---

### Post by Quadari on 2010-09-23
Hi All,

In setting up my Mythbuntu box, I appear to have everything almost working, with the exception of being able to watch HD channels.  I know that the channels are coming through my tuner card correctly, and I think I've just isolated it down to the fact that my machine doesn't have enough horsepower to watch HD channels.  Here are the (what I think are relevant) stats on my machine:

Pentium 4, 2.4 GHz
Hauppauge HVR-1600 tuner card
256 MB RAM
Whatever the built-in graphics card on my motherboard is, running a DVI-out to my LCD TV.
(I'm not at home right now, so can get the exact specs on the type of motherboard later if that's necessary to give advice.)

I'm not doing anything too heavy duty with my machine.  It's going to be a dedicated mythbuntu box, and I don't need to be able to watch 12 shows while recording 37 others at the same time, or anything like that. ;-)   I don't even get cable, so I'm just watching the clearQAM local channels that my cable company sends around for free.  I basically just want to be able to pause, FF, REW live TV, and record and watch a few shows every week.  I also would like to use the box as my DVD player.

So, all of that being said, I'm looking for some advice on the cheapest way to upgrade my machine so that I can watch/record HD content.  My initial thoughts on how to do this are:

1.  Add more memory.  This is cheap, and easy, but I don't know if it will make a difference.
2.  Add a dedicated graphics card.  This is easy, and maybe cheap?  I don't know much about graphics cards so I'm definitely looking for suggestions here if people think this will help.  Would adding a card take enough strain off of the main CPU to make it work?
3.  Replace the motherboard/CPU.  This is probably much harder than the first two suggestions, and potentially more expensive.  So my initial thought is to try and avoid having to do this if possible.

Anyway, curious to hear everyone's thoughts on the matter.

Thanks!

---

### Post by klc5555 on 2010-09-23
HD is all about CPU crunching and graphics card, not so much memory. Your CPU is OK. You need a decent NVidia graphics card, run with the proprietary (not open source) Nvidia drivers. ATI will also usually work, but is less well supported, and who needs the hassle? Nothing else will cut it.

Otherwise, in general, main memory should be at the 1-4 Gig range. 2 Gig is pretty standard. 512 Meg is possible, but is pushing it.

Concerns like disk speed, or keeping OS+swap and recording storage on separate disks will be less of a concern for you with only a single tuner, but remember that SD only consumes 1 Gig of disk space per hour, whereas HD consumes about 6.6 Gigs of disk space per hour, so have some space available.

---

### Post by LowSky on 2010-09-23
you really donthave enough RAM or CPU power for HD.

1. I would recomend 2GB of RAM right off the bat. 4 would be perfect if you can afford it
2.Nvidia graphics card, 85xx series or higher. It will help wit playback and take the load off the CPU... a decent card can b had for under $100
3.If that P4 is only a single core, I would really recommend you upgrade. I'm not sure of what type of PC you have butthink of a computer as a more expensive lego kit. a new CPU and motherboard can be had for about $150 on the cheap side, a decenet mid lever combo will push into $250, and highend starts at about $400.

---

### Post by Quadari on 2010-09-23
> **klc5555 said:**
> HD is all about CPU crunching and graphics card, not so much memory. Your CPU is OK. You need a decent NVidia graphics card, run with the proprietary (not open source) Nvidia drivers. ATI will also usually work, but is less well supported, and who needs the hassle? Nothing else will cut it.


So, as I said, I don't know much about graphics cards, but would something like this both (a) work, and (b) be fairly easy to set up?  (Avoiding lots of driver issues is a good thing.  :-) ).
[http://www.microcenter.com/single_product_results.phtml?product_id=0313872]("http://www.microcenter.com/single_product_results.phtml?product_id=0313872")
There's a microcenter fairly near me so I could just head in there and get the card and some extra RAM all in one shot. 

Although I totally agree, LowSky, that a CPU upgrade would be nice, I think I might try the graphics card route first. but as we all know, these things always tend to get bigger than you first intend.  :-)

Thanks for the tips.

In browsing around, I found this page, regarding VDPAU:
[http://www.mythtv.org/wiki/VDPAU](http://www.mythtv.org/wiki/VDPAU)
Is that still up to date, and something that I should do after installing a graphics card?

---

### Post by klc5555 on 2010-09-23
> **Quadari said:**
> So, as I said, I don't know much about graphics cards, but would something like this both (a) work, and (b) be fairly easy to set up?  (Avoiding lots of driver issues is a good thing.  :-) ).
[http://www.microcenter.com/single_product_results.phtml?product_id=0313872]("http://www.microcenter.com/single_product_results.phtml?product_id=0313872")
There's a microcenter fairly near me so I could just head in there and get the card and some extra RAM all in one shot. 

Although I totally agree, LowSky, that a CPU upgrade would be nice, I think I might try the graphics card route first. but as we all know, these things always tend to get bigger than you first intend.  :-)

Thanks for the tips.

In browsing around, I found this page, regarding VDPAU:
[http://www.mythtv.org/wiki/VDPAU](http://www.mythtv.org/wiki/VDPAU)
Is that still up to date, and something that I should do after installing a graphics card?

Your choice of video card will work. You will definitely want to implement VDPAU according to the documentation you found.

The one mild glitch that may briefly bite you is that the first time you boot after installing the NVidia proprietary drivers, you may find yourself booted into "low res" mode. The problem is that the cx18 driver for the HVR-1600 and the NVidia driver are both fighting for the same scraps of virtual memory when the kernel allocates it at boot. Solution will be to set the vmalloc=256m option in the kernel line in Grub, so that more virtual memory will be allocated. Then all goes well.

---

### Post by cascade9 on 2010-09-23
[http://www.microcenter.com/single_product_results.phtml?product_id=0313872](http://www.microcenter.com/single_product_results.phtml?product_id=0313872)

That is a PCIe (PCI express) card, and most of the 2.4GHz P4s I've seen havent got a PCIe slot. Normally, they have AGP...which pretty much rules out nVidia VDPAU. You need a 8XXX or higher card (and not all 8XXX cards do VDPAU) and nVidia stopped making AGP cards at 7XXX. 

You could run a PCI card, there are PCI 8400GS cards around. I'm not sure about how well HD would work via PCI, its got very limited bandwidth. 8400Gs can have problems with 1080p on PCIe, so I wouldnt hold my breath. 

Also, most of the 2.4GHz P4s I've seen have been 533MHz FSB models. Its more likely that you have the ability to use a 800MHz FSB CPU model than PCIe, but that depends on how lucky you are really ;) 

You could post your motherboard type (you would find that in lshw) and I, or somebody else, will tell you just what is capable of being upgraded. ;)

---

### Post by Quadari on 2010-09-23
> **cascade9 said:**
> 
You could post your motherboard type (you would find that in lshw) and I, or somebody else, will tell you just what is capable of being upgraded. ;)

Alright, here's a portion of the output from lshw that describes the motherboard and processor.

```

    description: Desktop Computer
    product: Product Name
    vendor: System Manufacturer
    version: SYS-xxxxxx
    serial: Serial number xxxxxx
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1
  *-core
       description: Motherboard
       product: SAMBA-1845GL
       vendor: First International Computer, Inc.
       physical id: 0
       version: PCB 1.x
       serial: Serial number xxxxxx
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (03/31/2004)
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.40GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.9
          slot: Socket 478
          size: 2400MHz
          capacity: 2400MHz
          width: 32 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr
          configuration: id=0

```


Here's the portion that (I think) talks about the built-in graphics card:
```

     *-pci
          description: Host bridge
          product: 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:c0000000-cfffffff(prefetchable)
        *-display UNCLAIMED
             description: VGA compatible controller
             product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:d0000000-d7ffffff(prefetchable) memory:e0000000-e007ffff

```


There was also something on the [MythTV VDPAU webpage]("http://www.mythtv.org/wiki/VDPAU"), that I found a little confusing:
"No AGP cards support this feature (PCI cards exist but lack the necessary bandwidth for non-VDPAU HD)"

Ok, so I understand that an AGP card won't work at all.  But the logic of that sentence seems to imply that PCI cards exist and while they lack the bandwidth for non-VDPAU HD, does that mean that they could work for VDPAU enabled HD?

---

### Post by tmcgary on 2010-09-23
Quadari,

I have a near identical rig that is HD capable using the 2.4 GHz Celeron and a HVR-1600. Its all housed in an old dell optiplex GX270 (you may laugh now).  

For a GPU I use Sparkle's 8400GS PCI card (like [this card]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814187041") but I believe in 512 GDDR, newegg doesnt appear to carry it anymore). I use 2 GB RAM and also a radioshack in-line cable amplifier between my HVR-1600 and the wall, turned all the way up. 

With VDPAU 'slim' setting it works fine for HD with only occasional artifacts/crap in the picture when viewing live tv. Recordings usually are perfect.

I have been using this rig for over a year and have had virtually no problems with the hardware keeping up.

---

### Post by Quadari on 2010-09-23
> **tmcgary said:**
> Quadari,

I have a near identical rig that is HD capable using the 2.4 GHz Celeron and a HVR-1600. Its all housed in an old dell optiplex GX270 (you may laugh now).  

For a GPU I use Sparkle's 8400GS PCI card (like [this card]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814187041") but I believe in 512 GDDR, newegg doesnt appear to carry it anymore). I use 2 GB RAM and also a radioshack in-line cable amplifier between my HVR-1600 and the wall, turned all the way up. 

With VDPAU 'slim' setting it works fine for HD with only occasional artifacts/crap in the picture when viewing live tv. Recordings usually are perfect.

I have been using this rig for over a year and have had virtually no problems with the hardware keeping up.

Oh no, no laughing going on here.  My rig is just as ghetto.  :-)  I just like to think it's ghetto-fabulous.  :-)

It's very heartening to hear that everything appears to be working for you.  I think I will make a trip to pick up some more RAM and a graphics card and hopefully things will all be up and running then.

Is this the card you speak of?
[http://www.microcenter.com/single_product_results.phtml?product_id=0307761](http://www.microcenter.com/single_product_results.phtml?product_id=0307761)

Anyone see any obvious problems with this one?
[http://www.microcenter.com/single_product_results.phtml?product_id=0314887](http://www.microcenter.com/single_product_results.phtml?product_id=0314887)
It's $25 cheaper, so I'm just wondering if there's a big difference.

---

### Post by tmcgary on 2010-09-24
That appears to be the right card! I didnt see a note on the second GPU if it is fanned or passively cooled. If the former, I would consider that the sparkle is passively cooled a big plus, but that is just my personal preference.

You may find you will need an inline amp for your cable run. The HVR-1600 is notorious for its clearQAM reception being finicky. Motorola makes a few models that are on amazon.com and the one I have from rad-shack works well. Without it I was not able to receive clearQAM with the HVR-1600.

---

### Post by Quadari on 2010-09-27
Just to update/put a cap on this thread.  I ended up getting the Sparkle 8400GS PCI card with 512MB of RAM (the other one was gone by the time I went to buy things), and I got another 1GB stick of RAM, bringing my total in the machine up to 1.25GB.  For now things seem to be working 8-).  (It actually took me about 10 hours of work to get the graphics card working as first there was a bunch of technical stuff that had to be done to blacklist lost of other drivers in order to even get the NVidia drivers to install, and then there were issues with the NVidia driver conflicting with the CX18 driver that runs the Hauppauge tuner card.  So that was quite a fun time trying to figure that one out, but I digress...)

It's working now and I actually have it running in VDPAU normal mode as I didn't see any difference between the normal and the slim mode.  There is some digital artifacting, so if I was a real stickler for picture quality I would be annoyed, but for my usage it's just fine.

So far I haven't needed an inline amp as the signal appears to be coming through just fine.

Thanks for the help/advice.

---

