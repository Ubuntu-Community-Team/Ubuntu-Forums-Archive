---
title: "Lucid: BCM4312 doesn't show correctly in panel"
date: 2010-05-03
forum: Networking &amp; Wireless
---

### Post by gohanssjn on 2010-05-03
So, here's the issue.

I have a Dell Laptop with a DCM4312 according to lspci -v | less.

I am running the hardware driver that Lucid suggested: Broadcom STA wireless driver.

It connects to the router fine.  But the icon is always the blank lines with a ! beside it.  It never shows signal strength.

Ideas?

---

### Post by TBABill on 2010-05-03
I have the BCM4312 and I believe that is what you meant to type? If so, try the B43 driver instead. When I go through System>Hardware it takes me to the drivers for the Broadcom wireless and gives me the option of B43 and STA. I choose B43 and it works great.

---

### Post by gohanssjn on 2010-05-03
Fantastic!

---

### Post by TBABill on 2010-05-04
Should I interpret that to mean it is working now? If so, could you mark the thread solved?
 
Good luck!

---

### Post by gohanssjn on 2010-05-04
I already marked it solved, because yes it did work :)

---

### Post by bobharvey on 2010-09-28
> **gohanssjn said:**
> It connects to the router fine.  But the icon is always the blank lines with a ! beside it.  It never shows signal strength.

I have the same issue, and can find no mention of the ! in the documentation.  I've raised a bug report:
[https://bugs.launchpad.net/bugs/649632](https://bugs.launchpad.net/bugs/649632)

I shall try the fix, but I still think that the documentation should explain things.

---

