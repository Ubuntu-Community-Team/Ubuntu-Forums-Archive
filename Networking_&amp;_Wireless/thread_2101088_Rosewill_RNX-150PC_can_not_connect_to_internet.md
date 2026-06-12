---
title: "Rosewill RNX-150PC can not connect to internet"
date: 2013-01-03
forum: Networking &amp; Wireless
---

### Post by Jisawesome on 2013-01-03
Hello, I recently built a computer using ubuntu desktop 12.10.
I got it working properly, except for the wireless card. The card I have is the rosewill RNX-N150PC with chipset Ralink RT3060. It connects via PCI slot.

The issue is this: when I start my computer up, it finds the network ok, and prompts for the network password (which is good). Then, the notification comes up telling me that I am connected to the internet. However, when I actually try to use the internet, it immediately disconnects me. Also, if I dont try to use the internet, it disconnects me regardless after about 60 seconds.

As there were no drivers in the Linux kernel, I attempted installing linux compatible drivers from rosewill's website, as well as Ralink's site.

If you have any idea what is going wrong, please help!

Thanks,

---

### Post by chili555 on 2013-01-03
> As there were no drivers in the Linux kernel, I attempted installing linux compatible drivers from rosewill's website, as well as Ralink's site.I believe there are. I suspect that the in-kernel driver is conflicting with the less good drivers you intrepidly built. Let's do some diagnostics:```
lspci -nn | grep 0280
lsmod | grep rt
```Thanks.

---

### Post by Jisawesome on 2013-01-03
I think I will just return this card and replace it with one on the suggested cards page, but thank you anyway.

---

