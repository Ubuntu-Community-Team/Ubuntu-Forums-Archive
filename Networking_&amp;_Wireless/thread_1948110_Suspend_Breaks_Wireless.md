---
title: "Suspend Breaks Wireless"
date: 2012-03-27
forum: Networking &amp; Wireless
---

### Post by dave2001 on 2012-03-27
After resuming from suspend, my laptops wireless is broken. I have tried to reload the module via terminal, but I get an error message. I have a pcmcia card for wireless internet connectivity on my thinkpad A20m. The card is from cisco systems, and according to lspcmcia, uses the *airo_cs* driver.

I've seen other posts and tutorials to "fix" this kind of issue, but their solution isn't working for me... perhaps I'm missing something. I've been trying to restart the network manager (Wicd), and reload the driver with the following commands:
```
sudo service wicd stop
sudo rmmod airo_cs
sudo modprobe airo_cs
sudo service wicd start
```

However, attempting to use rmmod on the airo_cs driver returns this:
```
ERROR: Module airo_cs is in use
```
using "sudo modprobe -r -f airo_cs" returns a similar message.

I'd love to get suspend working properly, any ideas? Thanks in advance.

---

### Post by dave2001 on 2012-03-29
Still hunting for a solution on what I'm doing wrong.

---

