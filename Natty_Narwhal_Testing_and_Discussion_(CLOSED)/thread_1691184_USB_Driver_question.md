---
title: "USB Driver question"
date: 2011-02-19
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by teachop on 2011-02-19
There is a driver in 11.04 that was not present before, called sam-ba.ko.  This is a problem solver for me, but I was not able to get it to load reliably without black-listing cdc-acm.

I am very grateful devs took the time and trouble to create sam-ba, it is working great.  However, I cannot practically use the computer once 11.04 comes out with cdc-acm black-listed.  So question:

How can I get sam-ba.ko to reliably load for the one type of hardware that needs it, and yet allow cdc-acm to work as usual for everything else that need that module?  Can I configure modules to assign a driver to a specific hardware item?

---

