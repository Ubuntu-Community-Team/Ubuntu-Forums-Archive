---
title: "Samba is picky about whether I use wireless or wired NIC"
date: 2012-05-15
forum: Networking &amp; Wireless
---

### Post by scottbomb on 2012-05-15
Home network consists of:

main - this PC is wired to the router @ 192.168.1.2. Dual boots Win 7 & Xubuntu 12.04.

laptop-wired - this is a Lenovo T60 on 192.168.1.3  Dual boots Win 7 and Xubuntu 12.04. This IP belongs to the wired NIC.

laptop-wireless - this is the same Lenovo T60 with the wireless NIC on 192.168.1.4.

Android phone - sees and connects to all shares... it doesn't care. Seriously, Google did this networking thing right from the start.

So here's the problem: I've got the laptop and main PC sharing folders just fine. Windows shares with Linux and vice-versa, regardless of which computer is booted into which OS - as long as the laptop is plugged into LAN via the wired NIC. The minute I un-plug it, the laptop reverts to the wireless NIC and has access to the router and full internet access, but it cannot connect to the shares on main regardless of which OS is current running on main.

As an experiment, I unplugged the laptop and rebooted it. Now it connects to the shares on main just fine. If I plug it in, it directs all traffic thru the wired NIC (I can tell by the icon in the Xubuntu taskbar) and all is well. I then unplug the wired NIC and the wireless NIC is able to connect to the same shares just fine.

Therefore, it seems that the only time I have a problem is if the laptop is initially booted with the wired NIC... I then diconnect and it then reverts to the wireless NIC... bit it can no longer access shares on main.

However, if I boot the laptop using only the wireless NIC (unplugged) it has no problem sharing regardless of which NIC is currently in use.

To summarize, if the laptop is initially connected via the wired NIC and then is unplugged, it has no problem going to the wireless NIC for internet access through the router. However, it cannot access shares on the main pc (which is always wired). But if I do this the other way around... boot with it unplugged... the wireless NIC can access the shares. I can then plug in the wired NIC and still access shares. I can also unplug and go back to the wireless NIC and still access shares.

This seems to be the only way to guarantee that the laptop can access the shares whether it's using the wired or wireless NIC: boot it with only the wireless NIC (unplugged). 

Is there a setting I can change? Perhaps I should file this as a bug?

---

### Post by scottbomb on 2012-05-19
Bump. Any ideas? Should I report a bug against samba?

---

