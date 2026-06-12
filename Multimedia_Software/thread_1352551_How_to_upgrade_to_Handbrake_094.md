---
title: "How to upgrade to Handbrake 094"
date: 2009-12-11
forum: Multimedia Software
---

### Post by tomreid on 2009-12-11
Hi all, 

I used to use Handbrake a lot when I was running 9.04, but as most of us know, 9.10 initially broke Handbrake. 

I was really happy to see a new version of Handbrake (0.9.4.) released that I've read works fine with 9.10. 

But, when I download the .deb from Handbrake.fr, when the package installer tries to install it, I get the following message "Error, conflicts with installed package Handbrake". (Screenshot attached).

So, I'm thinking that I need to de-install the previous version of Handbrake first. But Synaptic Package Manager and the new "Ubuntu Software Center" does not see that "Handbrake" is there and therefore I can't de-install it from there. 

I've also tried searching and searching the system's hard drive to try to see the old version of Handbrake, I deleted all files and folders I saw titled "handbrake", re-booted, but the same thing just happened again. 

Any ideas anyone?

---

### Post by tomreid on 2009-12-11
sorry, forgot the screenshot

---

### Post by JohnAStebbins on 2009-12-12
have you tried
```
sudo apt-get remove handbrake
```

---

### Post by tomreid on 2009-12-14
Thanks - easy when you know how.

cheers

---

