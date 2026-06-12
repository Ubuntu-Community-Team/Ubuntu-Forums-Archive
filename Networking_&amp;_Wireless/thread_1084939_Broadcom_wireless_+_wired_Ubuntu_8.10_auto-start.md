---
title: "Broadcom wireless + wired Ubuntu 8.10 auto-start"
date: 2009-03-02
forum: Networking &amp; Wireless
---

### Post by TechnoChick on 2009-03-02
Summary: How do I get my Ubuntu 8.10 system to properly auto-start my networking interface(s), activating the wireless or wired interface depending on the available connection?

Details: My Dell laptop has a Broadcom 4328 wireless adapter and a Broadcom 4401 wired adapter. Under Ubuntu 8.04 I used ndiswrapper to drive the wireless interface. At home I accessed my wireless network (no wired connection). At the office I booted my system with a wired connection (no wireless access point present). I've upgraded my system so I can no longer produce the exact configuration details. All I know is "it just worked".

I recently upgraded to Ubuntu 8.10. After some experimentation I determined that ndiswrapper still seems to be the best wireless driver for my configuration at this time. But, unlike under 8.04, I had to make /etc/modprobe.d/ndiswrapper look like this:

alias wlan0 ndiswrapper
install ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;

As mentioned in other's posts, the Broadcom wired driver can conflict with ndiswrapper, so this modprobe script removes the wired drivers, loads ndiswrapper, and then reloads the wired drivers. (For some reason I didn't have to do this under 8.04. Perhaps there was another wired driver that worked with my wired interface.)

In my new configuration both interfaces work, but they do not automatically start-up properly. I have to manually enter "sudo ifconfig xxx0 up" and "sudo dhclient xxx0" (where xxx0 is either eth0 or wlan0) after the system boots.

Issue #1: Is the modprobe script disrupting the normal network auto-start process? That is, since I am unloading the wired driver and then reloading it, am I confusing the start-up process?

Issue #2: I am not currently using Network Manager. I couldn't get it to connect to my WEP-based wireless access point. The failure symptom was it always selected the wrong frequency/channel, but that might just be a misleading symptom.

Instead I maintain my network configuration information in /etc/network/interfaces:

iface lo inet loopback
auto lo

iface eth0 inet dhcp
auto eth0

iface wlan0 inet dhcp
wireless-key 01020304050607080910111213
wireless-essid technochick
auto wlan0

So, my question is "how can I get my system to auto-start either both or the active network interface(s)?" I'm willing to use Network Manager if you can guide me through setting it up to support my WEP key (and choose the correct channel). Or I'm happy to avoid Network Manager.

Perhaps someone understands the start-up script processing order and can comment on the effects the modprobe script may be producing.

Perhaps there's another wired driver that will work with the 4401 that doesn't conflict with ndiswrapper. Or perhaps someone else with my Dell hardware configuration has been able to avoid ndiswrapper.

I appreciate any suggestions you might wish to offer.

---

### Post by set.zhang on 2009-09-22
I also want to know how i could auto start my wireless broadcom

---

