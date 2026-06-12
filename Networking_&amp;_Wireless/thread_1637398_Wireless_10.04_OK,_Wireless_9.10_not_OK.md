---
title: "Wireless 10.04 OK, Wireless 9.10 not OK"
date: 2010-12-04
forum: Networking &amp; Wireless
---

### Post by Moustaffa on 2010-12-04
Hi,

I was wondering why my wireless isn't working out of the box with ubuntu 9.10 while it did work right away with 10.04 and 10.10.

I decided to go back to 9.10 because the later versions of Ubuntu were too buggy imo. I went to System > Hardware drivers, but couldn't find anything for my wireless card.

Do I have to enable wireless somewhere or...?

Hope someone can help, because so far 9.10 > 10.04, don't want to go back to lucid.

Kind regards

---

### Post by Moustaffa on 2010-12-04
Oh, and I don't have a switch or something to enable/disable wireless.

Anyone?

---

### Post by Moustaffa on 2010-12-04
Bump..

Surely this doesn't need a complicated solution.

The wireless worked for the newer versions of Ubuntu, what could possibly prevent wireless working in Karmic?
Really confused here.

---

### Post by smo0th on 2010-12-04
I also had problems with 9.10 but everything works out of the box in 10.04

---

### Post by Moustaffa on 2010-12-04
> **smo0th said:**
> I also had problems with 9.10 but everything works out of the box in 10.04

Yeah, I know, but I didn't like lucid and maverick.

No one knows how I can solve the wireless problem in 9.10?

---

### Post by northd_tech on 2010-12-04
The newer 10.xx kernels must have built-in support for your WiFi interface, where the 9.xx do not.  I personally found Ubuntu 9.10 a little "buggy" for my liking and I stuck with 9.04 for a very long time (until the updates were recently discontinued- so I'm running 10.04 now).

Let's figure out quite a lot about your WiFi hardware- will you copy&paste the output from the following terminal commands (Applications > Accessories > Terminal)?:

```
lspci
lsusb
lsmod
sudo lshw -C network
ifconfig
iwconfig
ndiswrapper -l
```

---

