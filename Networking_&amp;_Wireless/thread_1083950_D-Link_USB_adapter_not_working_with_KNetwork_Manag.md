---
title: "D-Link USB adapter not working with KNetwork Manager, not working at all [Pictures]"
date: 2009-03-01
forum: Networking &amp; Wireless
---

### Post by Hexifford on 2009-03-01
The device is a D-Link WUA-2340 wireless USB adapter. I do not have a wireless card built into my computer. I have a Broadcom card built into my computer, but it's for wired connections, so it is useless to me. Kubuntu's KNetwork Manager detects the Broadcom card and it is named eth0 in KNM. I installed the drivers for my adapter using ndiswrapper, and as you can see here with the sudo ndiswrapper -l command it shows the adapter as present.
[img]http://img264.imageshack.us/img264/9285/present.jpg[/img]
And not present when not plugged in.
[img]http://img8.imageshack.us/img8/4602/ndiswrapperlistnotprese.jpg[/img]
At this point, I don't think the problem is with the driver right now. I'm thinking that the problem lies within KNM. As you can see, the KNM menu still only lists my Broadcom card, even after I restarted the computer.
[img]http://img264.imageshack.us/img264/7126/nochangesnetworkmanager.png[/img]No networks are being detected either...
[img]http://img88.imageshack.us/img88/7978/networknotdetected.png[/img]A search proved useless...
[img]http://img88.imageshack.us/img88/478/nothingforsearch.png[/img]
I don't understand why this is happening. I heard that WICD was a better alternative to KNM, and I would install it, but my dependencies got messed up when I tried installing MP3 support manually, so Kubuntu refuses to install anything new now. I tried repairing the dependencies, but to no success. It seems as if I need an internet connection to repair them. And seeing that KNM isn't cooperating, I'm really in a bind here. I tried installing WCID before the dependencies got messed up, but KNM was conflicting with the installation and I could not install WICD with it running. I ran a couple extra commands in the terminal and got some more information.
[img]http://img8.imageshack.us/img8/1458/extracommands.png[/img]
Maybe some of that can help solve the problem. Do I have to reinstall Kubuntu because of this dependency problem?

Thanks for the help in advance.

---

### Post by Hexifford on 2009-03-01
Please help, my grama is going to kill me if I don't get her computer fixed..

Edit: Yup, grounded for a week.

---

