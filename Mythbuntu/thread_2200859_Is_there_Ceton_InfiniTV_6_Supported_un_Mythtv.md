---
title: "Is there Ceton InfiniTV 6 Supported un Mythtv?"
date: 2014-01-21
forum: Mythbuntu
---

### Post by mcapaldo on 2014-01-21
Did not find this box under supported tuners list in the Top Sticky section so I gotta ask?

Bright House is going all digital in my county in 02/14.  So my analog tuners are going bye bye.  

I just checked with my local Bright House and they have a Cisco 803 (up to 6 tuners) Multi Stream Cablecard.  And was looking at the Ceton InfiniTV 6 to run it.  

Is the Ceton InfiniTV 6  (6 tuner external box) functional under mythtv?

---

### Post by scstanton1337 on 2014-01-30
I don't use the external box, but the PCIe card works fine with MythTV.  I have the PCIe 6-tuner unit.  You need to use Myth 0.27 and compile the Ceton kernel drivers, but it does work.

---

### Post by ronluna on 2015-01-30
Hello @mapaldo, wondering if you got to try the Centon InfiniTV 6 ETH with mythTV 0.27?

---

### Post by George_Boyce on 2015-05-17
I just tried to get the 6 card working. The driver compiled and loaded ok, and the device initializes. But the net does not initialize, either with dhcp or static address. The same card and PC hardware does work ok booted under windows 8.1, but I don't have nor want windows media center. This is with the latest firmware loaded and ubuntu 14. Any ideas where to go from here?

---

