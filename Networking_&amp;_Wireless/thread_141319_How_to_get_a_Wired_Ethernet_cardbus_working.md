---
title: "How to get a Wired Ethernet cardbus working"
date: 2006-03-08
forum: Networking &amp; Wireless
---

### Post by ddumanis on 2006-03-08
Hi all,

I struggled with this problem for a long time, trying to get my U.S. Robotics 10/100 NIC cardbus working on my laptop. I tried everything--compiling a company-supplied linux driver, tweaking every network control panel, etc.

Finally I decided to use ndiswrapper, even though I only knew it as an adapter for wireless Windows drivers. And what do you know, it worked with my wired driver too!

Here are the steps I took:
1. Install ndiswrapper GTK using Synaptic.
2. Go to the new control panel System>Administration>Wireless Windows Drivers
3. Drag the .INF file of the windows driver into the Wireless Windows Drivers dialog box and watch it load up.
4. After saving, activate it with System>Admininstration>Networking. (Mine showed up as wlan, a "wireless" networking device--but who cares, it worked!)

Dave

---

### Post by ddumanis on 2006-03-11
By the way, I found that the cardbus doesn't get recognized at startup--it tends to make my laptop hang.

So, I just eject it before starting up and then pop it back in after startup is complete. (I then have to go through the above routine of initializing the network with the Networking control panel again--takes about 3 minutes.)

---

