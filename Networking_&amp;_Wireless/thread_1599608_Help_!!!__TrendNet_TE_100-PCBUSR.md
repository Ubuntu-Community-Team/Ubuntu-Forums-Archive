---
title: "Help !!!  TrendNet TE 100-PCBUSR"
date: 2010-10-18
forum: Networking &amp; Wireless
---

### Post by seedainvisible737 on 2010-10-18
Ok, I'm still new to hardware driver installs.

I have purchased a TrendNet TE 100-PCBUSR card for my thinkpad t-22. The Lan port on the back of the system just quit and is not working. My expectation was to get a ethernet pc-card adapter and use that instead since all else works. I checked the card make sure it would work. there are drivers for Linux on the cd....But nothing sound looks like the instructions in the txt file. other users have qouted that it works but I having a hard time. Just to make sure I also plugged into a winxp system to make sure it was working. lights come on. drivers installed and it connected.....but I don't like Windows at all and my windows machine has a lan port .  heree's what i did:
 
i ran "lspci"
inserted the card gave a few seconds....
"lspci" again
noticed that it picked up a RealTek RTL8139. 

"ifconfig" only shows lo. In the past is has shown eth0 for dsl before is fried.

It apears as if the system sees it, but doesn't know to use as an ethernet or see is as eth0 device please. help. 

or show me how to compile drivers for ubuntu. Part of the instructions tell  you to compile the drivers in directories that are not on my system. here's where im lost. I have installed gcc version 3.3.5 . that all i know so far.

Please help.  I hope to learn from this but im stuck for now.:!:

---

### Post by dineshs on 2010-10-18
Can you restart and try ```
sudo lshw -C network
```

---

### Post by seedainvisible737 on 2010-10-20
I put in this command:

sudo lshw -C network

I get this:

lc@linuxBlak:~$ sudo lshw -C network

Harware Lister (lshw) - A.01.03
usage: lshw [-options ...]
        -version      print program version
        -html         output hardware tree as HTML
        -xml          output hardware tree as XML
        -short        output hardware paths

I don't think my version of lshw supports that option. However if i run it straight it looks lik this:
lc@linuxBlak:~$ sudo lshw

linuxblak

   description: Computer

    product: 2647SFM

    vendor: IBM

    version: Not Available

    serial: xxxxxxx

    capabilities: smbios-2.3 dmi-2.3

  *-core

       description: Motherboard

       product: 2647SFM

       vendor: IBM

       physical id: 0

       version: Not Available

       serial: xxxxxxxxxxx

     *-firmware

          description: BIOS

          vendor: IBM

          physical id: 0

          version: 16ET29WW (1.09 ) (02/28/2002)

          size: 144KB

          capacity: 448KB

          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd cdboot bootselect pcmciaboot edd int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi agp ls120boot biosbootspecification

     *-cpu

          description: CPU

          product: Pentium III (Coppermine)

          vendor: Intel Corp.

          physical id: 6

          version: 6.8.6

          slot: None

          size: 900MHz

          capacity: 900MHz

          clock: 100MHz

          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse

        *-cache:0

             description: L1 cache

             physical id: a

             slot: Internal L1 Cache

             size: 32KB

             capacity: 32KB

             capabilities: synchronous internal write-back

        *-cache:1

             description: L2 cache

             physical id: b

             slot: Internal L2 Cache

             size: 256KB

             capacity: 256KB

             capabilities: internal write-back

     *-memory

          description: System Memory

          physical id: 24

          slot: System board or motherboard

          size: 256MB

          capacity: 1GB

        *-bank:0

             description: SODIMM SDRAM Synchronous

             physical id: 0

             slot: DIMM 1

        *-bank:1

             description: SODIMM SDRAM Synchronous

             physical id: 1

             slot: DIMM 2

             size: 256MB

             configuration: width=64

     *-pci

          physical id: f8000000

          bus info: pci@00:00.0

          version: 03

          clock: 33MHz

        *-pci

             physical id: 1

             bus info: pci@00:01.0

             version: 03

             clock: 66MHz

             capabilities: pci bus_master

           *-display UNCLAIMED

                physical id: 0

                bus info: pci@01:00.0

                version: 13

                size: 128MB

                clock: 66MHz

                capabilities: bus_master cap_list

                configuration: irq=11

        *-pcmcia:0

             physical id: 2

             bus info: pci@00:02.0

             version: 03

             clock: 33MHz

             capabilities: pcmcia bus_master cap_list

             configuration: driver=yenta_cardbus irq=11

           *-network

                description: Realtek

                physical id: 0

                version: Rtl8139

                slot: Socket 0

                configuration: irq=11

        *-pcmcia:1

             physical id: 2.1

             bus info: pci@00:02.1

             version: 03

             clock: 33MHz

             capabilities: pcmcia bus_master cap_list

             configuration: driver=yenta_cardbus irq=11

        *-multimedia

             physical id: 5

             bus info: pci@00:05.0

             version: 01

             clock: 33MHz

             capabilities: bus_master cap_list

             configuration: driver=Sound irq=11

        *-bridge:0 UNCLAIMED

             physical id: 7

             bus info: pci@00:07.0

             version: 02

             clock: 33MHz

             capabilities: bridge bus_master
        *-ide

             physical id: 7.1

             bus info: pci@00:07.1

             version: 01

             clock: 33MHz

             capabilities: bus_master

             configuration: driver=PIIX_IDE

        *-usb

             physical id: 7.2

             bus info: pci@00:07.2

             version: 01

             clock: 33MHz

             capabilities: bus_master

             configuration: driver=uhci_hcd irq=11

        *-bridge:1 UNCLAIMED

             physical id: 7.3

             bus info: pci@00:07.3

             version: 03

             clock: 33MHz

             capabilities: bridge

             configuration: irq=9

        *-network

             physical id: 0

             bus info: pci@02:00.0

             version: 10

             clock: 33MHz

             capabilities: bus_master cap_list

             configuration: driver=8139too irq=11

  *-network:0 DISABLED

       description: Ethernet controller

       physical id: 1

       logical name: eth0

       serial: 00:14:d1:1c:dc:f5

       capabilities: ethernet

       configuration: broadcast=yes driver=8139too driverversion=0.9.27 multicast=yes

  *-network:1 DISABLED

       description: controller

       physical id: 2

       logical name: sit0


I don't know why, but I noticed that a few items listed as network showing DISABLED next to it. It does show the card and lists it accordingly. but what's really going on and how can i fix it?

---

### Post by dineshs on 2010-10-20
Which version of ubuntu are you using?10.04?
> *-network:0 DISABLED
You may right click the Network icon on right top of the panel and check if networking is enabled.(Hope it is enabled in BIOS)

---

### Post by seedainvisible737 on 2010-10-23
sorry for the delay. been online. I figured it out the very next day.

I did this from the desktop menu bar:

[Menu Bar]System>Administration>Networking

from here i corrected the issue of eth0 not configured. Once it was configured then activate eth0 from the same screen......It was so simple. I felt really silly trying to be deep and complicated with it. now it works. 

> Which version of ubuntu are you using?10.04?

believe it or not "Hoary Hedgehog" 5.04. the reason is that its an old system and i keep gettig issue when using an install or live disc to upgrade. still working on it. I have managed to get the Xubuntu 8.10 on the system. Its basiscally my test/Toy machine to get more familiar with Linux.

---

