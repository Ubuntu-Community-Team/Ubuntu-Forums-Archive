---
title: "Wireless issues with 10.10"
date: 2011-02-02
forum: Networking &amp; Wireless
---

### Post by dervil on 2011-02-02
Former Win7 user - installed Ubuntu 10.10 just yesterday and I really can't get my wireless to work...

Problem is there's no router in my flat so I'm transfering drivers and updates via an usb stick.. Downloaded Ndiswrapper along with what I think are updated wifi drivers.. But I can't seem to even install Ndiswrapper succesfully. It installs, but doesn't complete the install.. What I've tried is using the terminal;

ls
ls ndiswrapper-1.56
cd ndiswrapper-1.56
make install

That's as far as i've gotten.. 

Any help is appreciated, I am getting seriously frustrated!!

---

### Post by chaosdx on 2011-02-02
> **dervil said:**
> Former Win7 user - installed Ubuntu 10.10 just yesterday and I really can't get my wireless to work...

Problem is there's no router in my flat so I'm transfering drivers and updates via an usb stick.. Downloaded Ndiswrapper along with what I think are updated wifi drivers.. But I can't seem to even install Ndiswrapper succesfully. It installs, but doesn't complete the install.. What I've tried is using the terminal;

ls
ls ndiswrapper-1.56
cd ndiswrapper-1.56
make install

That's as far as i've gotten.. 

Any help is appreciated, I am getting seriously frustrated!!

Why do you need to compile ndiswrapper? There is a current version of the pre-compiled package for 10.10. If you choose to use it, anyway, you'll also need ndisgtk and ndiswrapper-utils-1.9. And proper WinXP drivers for your card.

By the way, you never mentioned if your system was 64-bit or 32-bit, your wireless chip model or any details of it... Please, refer to this thread before proceeding to ask further: [http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

---

### Post by dervil on 2011-02-02
Is that Ndiswrapper common youre refering to?

---

### Post by chaosdx on 2011-02-02
> **dervil said:**
> Is that Ndiswrapper common youre refering to?

Yes.

---

