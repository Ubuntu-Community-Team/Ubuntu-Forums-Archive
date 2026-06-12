---
title: "Wireless in 2.6.10"
date: 2005-03-20
forum: Networking &amp; Wireless
---

### Post by lavinaz on 2005-03-20
Hi,

I just installed the linux-image 2.6.10-5-686 from the synaptic packages list.
Before that, I used the default kernel 2.6.8-3-386. Everything worked fine until I tried to use wireless. 

When I used my wireless centrino with kernel 2.6.8, and the signal quality was always over 50, while the noise is very low, about -200. But now, the signal could not be over 30, while the noise level is high, about -80. 

The new kernel used another ipw2200 module, it's ipw2200-2.6.10 something. The old one is ipw2200-2.6.8.
Anyone knows anything about how to make it better with the new kernel?

---

### Post by rmjokers on 2005-03-21
I havent had a chance to look at the power levels with this network card and the new kernel, but I did have the IPW 2200 module fail after a few MB's of an apt-get upgrade.  It printed something about a FATAL error on the command line and my network connection was inoperable until after a reboot.  There must have been some regressions with this module in the current kernel.

---

### Post by knappen on 2005-03-25
Well there seems to be some problems with ipw2200. Drop outs and some weird things happening :-)

---

