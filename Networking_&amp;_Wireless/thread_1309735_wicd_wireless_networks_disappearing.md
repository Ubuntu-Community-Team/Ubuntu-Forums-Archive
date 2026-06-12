---
title: "wicd: wireless networks disappearing"
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by walrus_t on 2009-11-01
Hi everyone,
I just installed Karmic on my Thinkpad X60s and I installed wicd from the software channel too (1.6.1 version). Then:
1. I click on wicd tray icon;
2. I can see my neighbour's wireless network but not mine as I chose to hide SSID;
3. I then click on Network, Connect to hidden network;
4. I type my network SSID;
and... wicd says no wireless networks found! It does not find anymore my neighbour's network, even if I keep on refreshing. At this point, I try Wifi radar that can find my neighbour's network.

I tried to downgrade to 1.5.9 (worked fine on 9.04) but same problem.

When I reboot, what I described before happens again: I can see all the networks before I try to connect to my own and then, no network show up!

Please help me if you can :) Thanks a lot!

---

### Post by wonko on 2009-11-02
Experiencing the exact same thing on my x60s after upgrading from Kubuntu 9.04 to 9.10 (had wicd installed before the upgrade). Strange thing is, it did work earlier, when I was visiting a friend and connecting to his network. My home network setup is wpa 2, hidden essid on an Apple Airport Extreme. My friend I believe use wep. I tried reinstalling network-manager-kde, but now no wireless networks show up at all :( I'll post back when I've tried reinstalling wicd and connecting to another wireless network again.

Btw.: my thinkpad's wlan-card use the iwl3945 driver.

Update: wicd works on other networks, but not my own. Also wicd-client.py keeps crashing and won't show me any wireless networks (tray-icon work though). So I give up - installing Ubuntu (gnome) now, and hope it won't be too long before Kde4 actually works :(

---

### Post by walrus_t on 2009-11-02
Hi wonko, thanks for your reply.
I haven't tried to connect to another network but unhid my network: wicd can see the SSID but still can't connect. I get the "Unable to get IP address" error... :(
Will try your driver soon.
I hope everything gets fixed really soon.

---

### Post by Belerophon on 2009-11-03
Same issue here.
Upgraded from 9.04.

Have always been working with wicd and connecting to a hidden network at work and a normal at home. Everything worked just fine.
With Karmic, I always get this behaviour.

I have iwl3945 too.

Thanks.

---

### Post by flaflashr on 2009-11-21
I don't know if this will help your problem or not, but it just solved mine.  Kubuntu 9.10 Krusty Klown new installation on Dell D400 with Broadcom set trying to connect wifi, but Wicd kept reporting "No wireless network found" (I used Wicd because of previous errors on other machines trying to use the KDE Network Mangler).

lshw -C network reported *-network DISABLED

Solution was to to go to Applications | System | Hardware Drivers which reported "No proprietary drivers ...", but also listed Broadcom B43 Wireless Driver, tested by Ubuntu Developers, License Free.  At bottom of this dialog, "This drivers is not currently activated".  I clicked the activate button, and it downloaded and installed the driver, and my Wifi network was magically found.

The dialog box also mentions "fwcutter is a tool which can extract firmware from various source files. It's written for BCM43xx driver files." 

Hope that somebody finds this helpful.

JimR

---

### Post by FatalChaos on 2009-11-29
Has anyone had any luck fixing this problem? Unfortunately for me, madwifi is not part of karmic, so there is no option to switch to proprietary drivers.

---

### Post by Yeeha on 2009-11-30
Same problem from alpha5 wifi didnt work anymore. card is PRO/Wireless 3945ABG [Golan].Kubuntu network manager sees networks but is unable to connect. Wicd used to see too but not even that anymore. Although i saw through wicd with i386 version of kubuntu 9.10 now i am using amd64 so maybe it has something to do with that.

---

### Post by Fremont_Cunningham on 2011-05-22
18 months later and this problem STILL haunts UBUNTU!
Acer Aspire4530/AMD 64-bit/Maverick. Wicd only, no NM, per general advice.
Problem appears to be that after a suspend + return to operation the system no longer sees the USB wifi devices. Is does see wired ethernet but needs manual command to get that to reconnect. wifi is simply *gone*.
Is Wicd a dead product? anyone working on it?

---

