---
title: "Ubuntu phone/touch superphone / desktop convergence, hardware requirements?"
date: 2013-06-19
forum: Mobile Technology Discussions (CLOSED)
---

### Post by Willard on 2013-06-19
Hi,

As can be seen for instance [here](http://www.ubuntu.com/phone/operators-and-oems), a igh-end Ubuntu "superphone" is classified as being one which has the following hardware:

[LIST]
[*]Processor architecture: Quad-core A9 or Intel Atom
[*]Memory: Min 1GB
[*]Flash storage: Min 32GB eMMC + SD
[*]Multitouch: Yes
[*]Desktop convergence: Yes[/LIST]

Two questions:

[LIST=1]
[*]What, exactly, does "Min 32GB eMMC + SD" mean? Does it mean that "the sum of the storage available on the phone eMMC and on the SD card (if any) must exceed 32GB"? For instance, if my phone has 16GB of internal memory, and I put a microSD card into the phone which has at least 16GB of space on it, will my phone become a superphone? Does this then also mean that the Nexus 4 can never be a superphone?
[*]What, exactly, does Quad-core A9 mean? Is Canonical refering to [these guys](http://en.wikipedia.org/wiki/ARM_Cortex-A9_MPCore)?[/LIST]

Thanks,
Willard.

---

### Post by grahammechanical on 2013-06-20
1) [http://www.simmtester.com/page/news/showpubnews.asp?num=181](http://www.simmtester.com/page/news/showpubnews.asp?num=181)

As it is flash storage I would expect the + sign to mean the total of eMMC and SD to be at least 32GB.

2) ARM does not make chips. It designs chips to order. The ARM A9 Cotex can be 1 to 4 cores depending on design requested by the customer. So, not all ARM A9 powered devices will have quad (4) cores.

That specification is for handset makers. It shows the lowest specification devices that "high-end Ubuntu Superphone" platform will run decently on. Whether any existing smartphones will be able to run the full Ubuntu superphone platform will depend not only on the hardware specification but on whether anyone will port it to that device.

[https://wiki.ubuntu.com/Touch/Devices](https://wiki.ubuntu.com/Touch/Devices)

You might want to check out the hardware specs of those devices that Ubuntu Touch is being ported to. Canonical is working on the Nexus 4 but from this specification it seems to be a bit low on internal memory to be more than a Ubuntu Phone. It has 2GB of RAM which is twice the minimum but 8/16GB internal storage with no facility for a card slot.

[http://www.gsmarena.com/lg_nexus_4_e960-5048.php](http://www.gsmarena.com/lg_nexus_4_e960-5048.php)

Just to confuse us even further, Canonical is working on the Nexus 10 and that has 2GB of RAM and 32GB of internal memory but a dual core processor. So, I guess that a 2 core ARM Cortex A15 must be faster than a 4 core A9 and that must be the important bit as well as the graphic capabilities.

I suppose there is a difference between Canonical wanting a very good user experience from Ubuntu Touch pre-installed on handsets and us ordinary users putting up with a little less than an excellent user experience because we have self installed on a device that we already owned or that was a lower spec and therefore less money to buy.

Regards.

---

