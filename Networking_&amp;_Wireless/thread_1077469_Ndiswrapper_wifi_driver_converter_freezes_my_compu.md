---
title: "Ndiswrapper wifi driver converter freezes my computer!"
date: 2009-02-22
forum: Networking &amp; Wireless
---

### Post by Chaoskeeper56 on 2009-02-22
Hello.
I have used ubuntu for a while, but the entire time, i had to use a router to get to the internet.
It is a pain, but i found a way to make the driver for it work on ubuntu, with the program Ndiswrapper.
But, whenever i import a driver into my computer, my computer freezes!
It is a good computer, not too old, i don't see why its freezing.

The Laptop i'm using is an Acer Aspire 5315, if that is useful advice that could solve my propblem.

thanks.

---

### Post by Reiger on 2009-02-22
It probably means your driver is not suppored by Ndiswrapper and the installation attempt is causing all sorts of errors to occur (won't ruin your system, just won't help getting the hardware to work either). Anywho you can check by typing:
```

sudo dmesg | grep ndis

```

In a terminal. If there are error messages in the output.. the conclusion is (almost) obvious.

---

### Post by Chaoskeeper56 on 2009-02-22
It happens with any driver that goes into the program, not just that one.

---

