---
title: "Kernel 2.6.15-25 Madwifi missing?"
date: 2006-07-08
forum: Networking &amp; Wireless
---

### Post by al_erola on 2006-07-08
I got automatic recognition of my D-Link DWL G-630 card in my 2.6.15-23 kernel but when I upgraded to 2.6.15-25, it would not recognize ath0.

I can find any reference to madwifi, or atheros when searching adept?

Is there a problem with madwifi, not recompiled yet?

This is not a big issue, but surprising to lose the functionality with a kernel upgrade and no warning.

Thanks.

---

### Post by Eversmann on 2006-07-08
Intall linux restricted modules.

```
sudo apt-get install linux-restricted-modules-$(uname -r)
```

You'll get it working again.

---

### Post by al_erola on 2006-07-08
Thanks for the suggestion.  

However when I do:
sudo apt-get install linux-restricted-modules-2.6.15-25-686 or
sudo apt-get install linux-restricted-modules-2.6.15-25-386

I get the following:
E: Couldn't find package-restricted-modules-2.6.15-25-686 or
E: Couldn't find package-restricted-modules-2.6.15-25-386

So the modules aren't available yet?

---

### Post by tturrisi on 2006-07-08
yes, the modules are available, use synaptic in the Base System (restricted) area. You need to have apt configured to use univers & multiuniverse.

---

### Post by ZeeDD on 2006-07-13
Ok, just go here and you will be able to download the linux-restricted debian package for lasts kernel updates (even v2.15.26):
 [http://mir2.ovh.net/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.15/](http://mir2.ovh.net/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.15/)

Simply install it with package manager and reboot your system. Your wifi card will work after that.

ZeeDD.

---

### Post by al_erola on 2006-07-13
Thanks!  That worked.

---

