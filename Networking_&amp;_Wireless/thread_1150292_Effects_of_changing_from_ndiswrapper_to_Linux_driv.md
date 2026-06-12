---
title: "Effects of changing from ndiswrapper to Linux driver?"
date: 2009-05-05
forum: Networking &amp; Wireless
---

### Post by lesliek on 2009-05-05
I just upgraded to v 8.10 from v 8.04.

Before, I was using ndiswrapper and a Windows driver. This time, I've tried the supplied Linux driver, the Broadcom STA wireless driver.

There are two things I've noticed immediately, but I don't know whether they're a result of switching drivers.

1. The network monitor icon shows an error. It says "SIOCGIFFLAGS error: no such device". However, subject to my second point, I AM connected.

2. Every so often, I'm told by the network manager that I've been disconnected from my wireless network and that a network address is being requested. Then, I'm told I'm connected again.

Can those two things be the result of using the Linux driver? Is there a way to fix them, other than going back to ndiswrapper and the Windows driver?

---

### Post by coffeeaddict22 on 2009-05-06
if you open a terminal, what's the output of 
```
lshw -C network
``` and ```
iwconfig
```

---

### Post by lesliek on 2009-05-06
Thanks for replying.

A judge in a famous English case asked the rhetorical question: "With the light before us, why should we grope in the dark?"

I decided to act in accordance with that statement. I disabled the Broadcom STA wireless driver and went back to the Windows driver plus ndiswrapper. Both problems immediately disappeared.

I was about to edit my original post when I learnt of your reply.

I hope my problem's gone away.

I'm sorry to have troubled people unnecessarily.

Thanks again.

---

### Post by coffeeaddict22 on 2009-05-06
No trouble. Part of the fun of Linux is that you CAN mess with the system, and there's always more than one way of doing things.

---

### Post by tripolitan on 2009-05-06
.

---

