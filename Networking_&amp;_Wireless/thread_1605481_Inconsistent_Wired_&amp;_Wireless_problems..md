---
title: "Inconsistent Wired &amp; Wireless problems."
date: 2010-10-25
forum: Networking &amp; Wireless
---

### Post by KalChung on 2010-10-25
Hi!  Thought I'd just try posting my problems here as I have no idea what the cause of these problems are, related or what not.

I'm using a install from an upgrade, and I'd rather solve my troubles than reinstall.  I use the network-manager applet that comes default with the installation.  Best I can figure, the applet only works when I'm in a location with a pre-defined wireless access point or if I'm already connected to the network prior to starting my laptop.

If per-chance I'm not at home, the applet doesn't even show up on the toolbar.  If no wired connection is connected, even if one is plugged in later on, it is not detected.  It would seem to me if a wired or wireless connection cannot be detected on startup then the said adaptor is disabled until I reboot.

Would appreciate if anyone can point me in the right direction. As it is a pain to do things manually every time I startup, the problem also prevents me from easily browsing through new wireless access points when I go out of the house.

Thanks!

---

### Post by KalChung on 2010-10-27
Thought I'd just update this thread as I've recently found the solution.

I was able to find out how to manually enable|disable my cards (from another post) using the command **sudo ifconfig <name> [up|down]**

Once I enabled the said wired or wireless connection using the command line I restarted the network manager applet using **sudo /etc/init.d/network-manager restart**.  That fixed my initial problem, however, my wired network was still classified as not managed.

Googling this problem lead me to modify nm-system-settings.conf in /etc/NetworkManager , apparently the managed setting in the [ifupdown] tag was set to **trues**, which seemed to be wrong so I changed it to **true**.

After another network-manager restart my wired network was being detected properly.

Hope this helps someone out there.

---

