---
title: "No networking with 12.10 after CPU and Motherboard upgrade"
date: 2013-01-15
forum: Networking &amp; Wireless
---

### Post by CJNZ2011 on 2013-01-15
Hi all,

Just upgraded my motherboard, ram and CPU on a 12.10 install.
I have used the same drive and operating system - I have not performed a fresh install.
After doing this networking stopped working.
I played around with it for a few hours and came to the conclusion based on some googling that my NIC was not supported - which was the case for 12.04, but is likely not the case now.

Anyway, I brought a new PCIe NIC but still have the same problem.
I guess this means it is likely in software.

Is this a known issue?
I'm not sure what to do next and couldn't uncover any similar issues in the forums.

---

### Post by sanderj on 2013-01-15
I would do this:

Boot a live-Ubuntu 12.10 from CF or USB-stick. Check if your network works. If so, you know Ubuntu 12.10 and your network card like eachother.

If so, boot Ubuntu again from the harddisk. Analyze which network card you have:

```
lspci
lsusb

```
Post the output here.

---

### Post by CJNZ2011 on 2013-01-16
Thanks very much for the advice!
Turns out it was an interfaces issue.

---

