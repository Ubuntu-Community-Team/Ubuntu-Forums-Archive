---
title: "Running Ubuntu over a network (NOT live CD)"
date: 2010-03-30
forum: Networking &amp; Wireless
---

### Post by mark_lar on 2010-03-30
Hey guys and girls.

I have currently got Ubuntu running over the network so it boots like a live CD over PXE. There is a rather good tutorial on YouTube for anyone looking to do this.

Now, what I am trying to do is make the live CD install persistent, or install it to a virtual hard drive or something so I don't have to download the programs I need each time I need to use the system.

The files are stored on a FreeNAS server, and the PXE requests are sent on from a router running PfSense.

Is this a blindingly obvious thing? Can anyone out there link me some instructions?

Before someone asks, it is not possible to install Ubuntu on the machines that are currently network booting.

---

### Post by mark_lar on 2010-03-30
Having done yet more research I have stumbled upon iSCSI targets, which have just confused me even more! Are these the way to go? Or is it still possible to use a similar system to a live USB pen?

confused.com

---

