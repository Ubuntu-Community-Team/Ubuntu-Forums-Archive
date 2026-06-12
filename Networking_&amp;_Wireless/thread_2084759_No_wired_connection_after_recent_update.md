---
title: "No wired connection after recent update"
date: 2012-11-16
forum: Networking &amp; Wireless
---

### Post by beju0506 on 2012-11-16
Hey everyone,

I was using my machine on Monday, Nov 12, 2012 and everything was working fine. I had some pending updates I had been putting off for a few days so I went ahead and ran them then shut down the machine. I just turned it on today and the nm-applet says I have no internet connection on the wired connection. I restarted a few times, no dice. Killed the nm-applet and restarted it, no dice. I went to look at the update history for anything involving "network" and the only thing at all recently was one for "libqt4-network" that was pushed out on Nov 9th. I rebooted the machine into my windows partition and the network works fine. I have another machine using the same version of Ubuntu which had updates around the same time, rebooted and no problems at all. 
I had seen some people say it might be related to a network update, some say it might be a kernel update that removed necessary drivers, etc. Has anyone else had this issue or know what might be going on or what I can do? Does anyone have an idea of what I can do to diagnose/fix this?

My stats:

Ubuntu: 12.04LTS

Network card: NVidia nForce 10/100/1000Mbps (according to Windows device manager)

Any help you can give is greatly appreciated!

---

### Post by chili555 on 2012-11-16
I think the driver for your ethernet card is the wonderfully named forcedeth. When you boot and the ethernet isn't working, please run:```
sudo modprobe forcedeth
```Does your ethernet spring to life? If so, let's instruct the system to load it on boot:```
sudo su
echo forcedeth >> /etc/modules
exit
```If not, let's dig deeper:```
lspci -nn
dmesg | grep forcedeth
```Thanks.

---

### Post by beju0506 on 2012-11-16
Hey! Thanks for the reply... I had rebooted, shut off, etc numerous times this morning to no avail and ended up using my windows partition today for work. I rebooted this afternoon into Ubuntu and logged in and... presto, network working just fine. *sigh*
If it happens again, I'll try your solution and see if that works... for now though, it's working again.

Thanks again for your support! :)

---

