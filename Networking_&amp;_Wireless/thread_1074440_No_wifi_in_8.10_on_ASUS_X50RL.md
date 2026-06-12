---
title: "No wifi in 8.10 on ASUS X50RL"
date: 2009-02-19
forum: Networking &amp; Wireless
---

### Post by deg12 on 2009-02-19
Hi there

I 've look everywhere but I can't find an answer so here's the question:

How do I get the wifi to work on my Asus X50RL in Intrepid (8.10)?

Everything works fine in 8.04 (Hardy) but now all I get is a short blink from the wifi light.

In Hardy i got it running using compat ([http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-old.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-old.tar.bz2))

Thanks

---

### Post by binbash on 2009-02-19
paste the output of sudo lshw because i can't find the chipset of your notebook

---

### Post by deg12 on 2009-02-19
OK

I finally got Kubuntu running with the new compat drivers same website as above.

First I did this:

gksudo gedit /etc/acpi/start.d/60-asus-wireless-led.sh

Then I switched the 1 and 0

Ans then I ran the compat drivers from wireless.kernel.org

Thankx

---

