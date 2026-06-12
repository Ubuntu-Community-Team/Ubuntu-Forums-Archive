---
title: "How-to use and troubleshoot GMA 500 (Poulsbo) video graphics"
date: 2009-12-04
forum: Multimedia Software
---

### Post by michael37 on 2009-12-04
This video card is common on a number of netbooks.  How do you know you have this card?

Run 
```
lspci | grep VGA
```

If you have GMA 500, you will see something like
```
00:02.0 VGA compatible controller: Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller (rev 07)
```

**UPDATE: The most updated source of information is this [Hardware Support guide]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo") from Ubuntu Wiki.**

This link summarizes excellent collection of information on forums, such as [thread=1229345]Guide to Get the Best Performace from the GMA 500[/thread].

---

