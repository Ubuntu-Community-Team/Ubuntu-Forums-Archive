---
title: "How do I Re-enable Linux Wireless Drivers?"
date: 2010-01-10
forum: Networking &amp; Wireless
---

### Post by LADmaticCA on 2010-01-10
Hi. Today I bought a Trendnet TEW-423PI pci wireless adapter for my Jaunty 64bit desktop. Wireless worked out the box but it was really slow and with a poor signal. After searching the forums I found that some improved performance by using the ndiswrapper. I have failed at getting the ndiswrapper to work and was wondering if anyone knew how to re-enable the initial linux driver? Thanks.

---

### Post by LADmaticCA on 2010-01-10
I figured it out reading the man pages. The original linux module for my card was the rtl8180. So I ran:

```
sudo modprobe -a rtl8180
```

Now I've got the original driver back.:D I'll have to try another method to improve my connection.

---

### Post by Pithikos on 2010-06-29
Well did you succeed with anything? I have kind of the same problem. I have a rtl8185 card but it seemed to work a bit with the rtl8180 driver though it was really slow and with low signal like in your case :(

---

