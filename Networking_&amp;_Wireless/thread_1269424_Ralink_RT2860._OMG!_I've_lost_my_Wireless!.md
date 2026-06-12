---
title: "Ralink RT2860. OMG! I've lost my Wireless!"
date: 2009-09-18
forum: Networking &amp; Wireless
---

### Post by ^_Pepe_^ on 2009-09-18
Hi everyone.

I was decided to fix my not-working WPA connection. Only WEP was working with 2.6.8-15 kernel.

AFAIK, last drivers were working, so since I've found this .deb [https://launchpad.net/~henrik-hw0/+archive/ppa/+build/1104251](https://launchpad.net/~henrik-hw0/+archive/ppa/+build/1104251), I feel I can, but no!!

:confused:

After install, restart...no wireless devices. Is like I couldn't find the adapter. 

lspci gives me the adapter, and if I start verbose mode, I can see the driver loading. 

I've test my Router with WEP and WPA, but I cannot see my SSID because there's no wireless.

Please help! It could be a good solution to restore previous driver (the original kernel one) I will wait for 9.10...

Thanks.
^_Pepe_^

---

### Post by ^_Pepe_^ on 2009-09-18
Hi.

Well, let's say solved!, but not by the smartest way.

1st test: Check the last kernel 2.6.28-14, but, rt2860 is automatically installed on the 1st run... :-/

2nd test: Open de .deb with GDebi, and check the files. Delete all! Obviously it doesn't work, previously driver is not automatically loaded...

3rd test: Open 2-6-28-13, kernel...and works! Uf!!!!

I uninstalled 14 and 15 kernels with Ubuntu Tweak (great tool).

And...finally, I tried to install last kernel with Synaptic...but...oooooh!, Wifi is not working again!

Ok, let's say: My ubuntu skill is not 4/10...is 2/10 :(((

I'm now with 2.6.28-13, but happy...

regards,
^_Pepe_^

---

