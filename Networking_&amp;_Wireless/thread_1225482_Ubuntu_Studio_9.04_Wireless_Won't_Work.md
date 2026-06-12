---
title: "Ubuntu Studio 9.04 Wireless Won't Work"
date: 2009-07-28
forum: Networking &amp; Wireless
---

### Post by RustyShackelford on 2009-07-28
Just put studio on my laptop, everything seems to work fine but the wireless won't work. It worked fine on the the non-studio 9.04. It also works on fedora (dual boot).

When I go into System > Admin > Network Tools and select Wireless Interface (wlan0). Click configure I get "the interface does not exist"

I tried google searching and searching the forums but still couldn't come up with a solution.

---

### Post by djrudra on 2009-08-06
hi
try 

sudo apt-get install network-manager

---

### Post by superprash2003 on 2009-08-06
post output of **lshw -C network**

---

