---
title: "Problem with ethernet card"
date: 2009-08-01
forum: Networking &amp; Wireless
---

### Post by Idefix82 on 2009-08-01
Hi, all. I have just updated to the kernel 2.6.28-15 and my RTL8111/8168B ethernet card isn't recognised. Here is the relevant output from lshw:

```
lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED
       description: Ethernet controller
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ce:59:97:a9:20:da
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

In the past the r8169 driver took control but didn't work. I always had to replace it with the r8168 driver from the official Realtek website. However, in the previous kernel (2.6.28-14) even the r8168 didn't work and I had high hopes for this kernel update. But they seem to have removed any suitable drivers from the kernel altogether. Anybody with the same card/same problem or any ideas? Should I just try the r8168 again?

---

### Post by Idefix82 on 2009-08-02
This is a gentle bump.

---

### Post by brayden13 on 2009-08-02
coincidence, i have the EXACT same realtek gigabit onboardlan. and the internet is workign fine, my switch is picking up a gigabit speed. and nothing wrong with it. oh and i'm on jaunty 64bit with the latest kernel. I have had absolutely no problem. must be just your problem.

---

### Post by Idefix82 on 2009-08-02
Thanks for the useful feedback! Could you give me the output from your
```
lshw -C network
```
so I can see which driver is controling your card?

---

### Post by Idefix82 on 2009-08-02
So I just realised, that I am in fact blacklisting the r8169, which is why it's not loading.

Now, here is the strange thing: when I put it back by hand, it takes over my ethernet card and the output from lshw and from ifconfig looks healthy, but if I left click on the network manager then the "Wired Network" item is greyed out and the computer is not connecting to the router. Any ideas?

Edit: I feel really stupid now. All I had to do was add a new wired connection without specifying anything. I didn't have to do it before so it didn't occur to me to try it. This issue is SOLVED then.

---

