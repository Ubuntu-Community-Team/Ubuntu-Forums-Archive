---
title: "Ubuntu won't connect to network unless I disable/enable."
date: 2011-02-07
forum: Networking &amp; Wireless
---

### Post by Roasted on 2011-02-07
I'm running Ubuntu in VMWare for a side project. I noticed when I boot up, it doesn't let me access anything externally. I have to disable network manager and re-enable it. Once done, I can hit everything fine.

I'm using a static IP in network manager.

Any ideas?

---

### Post by amsterdamharu on 2011-02-27
I know this is old so it might have been fixed already.

Do you have a vboxnet0 in your networks? When you execute the following command:
```
ifconfig -a
```
It shows up as vboxnet0 on my machine (using sun virtualbox).

What is the output of the following command?
```
cat /etc/networks
```

---

