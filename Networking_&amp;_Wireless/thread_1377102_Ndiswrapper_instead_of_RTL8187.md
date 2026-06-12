---
title: "Ndiswrapper instead of RTL8187"
date: 2010-01-09
forum: Networking &amp; Wireless
---

### Post by Burky on 2010-01-09
I have Ubuntu 9.10. My USB WG111v3 Wireless Card uses the rtl8187 driver. This driver is buggy. I would like to use Ndiswrapper instead. How to make it so Ubuntu doesn't load the rtl8187 driver but Ndiswrapper instead?

---

### Post by The Toxic Mite on 2010-01-10
Well, do you have the **Windows XP **drivers for it?
 
The reason I ask is because NDISwrapper doesn't work with drivers that have been installed on/designed for Windows Vista and above (for some reason :-k)
 
First of all you will need to install NDISwrapper from the CD.
 
Just pop it in, load a terminal and:
 
```

sudo apt-get install ndiswrapper-common

```
 
If you want to use the graphical front-end (ndisgtk):
 
```

sudo apt-get install ndisgtk

```
 
-TTM-

---

### Post by Burky on 2010-01-10
Yes, I have everything configured with ndiswrapper. I just need linux to use ndiswrapper instead of the RTL8187 driver.

---

