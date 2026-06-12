---
title: "Asus P8z77-v Ethernet Problem"
date: 2012-10-21
forum: Networking &amp; Wireless
---

### Post by mevik on 2012-10-21
Hi guys, long time since my last post.
I built a new box during the summer and included an ASUS p8z77-v motherboad, while almost everything seems to work fine I am having the following issue:

The ethernet interface seems to work only if restarting the machine. If it is turned off and I turn it on, I find that it won't connect to the wired network, however, if I restart it it works without trouble. Wireless network is detected without trouble regardless of being turned on or restarted.

I have also found that when going into the mobo settings, a IBA GE slot sometimes appears as a boot option and sometimes when starting the computer an "intel Boot agent" appears.

Is there something wrong with drivers or is it hardware malfunction? Any suggestions?

Just to give you guys some more information that might be of help, I have used crunchbang (as live cd) ubuntu server 12.04, xubuntu 12.04 and Arch linux images from the last couple of months. If I type dhcpcd eth0 (always did this in arch to activate ethernet, until I properly configured it in the appropriate file) a message appears telling me that interface eth0 is not available. I have been using 64 bit images and EFI

---

### Post by mevik on 2012-10-23
So, my info was extremely vague, I did not have my computer available at the moment, sorry.

So I just turned it on and the usual problem appeared, when turning it on from being completely off it doesn't get the ethernet interface. Going into wired networks doesn't show anything. If I restart it, then it works like a charm.

Related to the IBA details:

When turning it on from being off nothing else other than the the usual "Press DEL to go into settings/configuration" appears, however when restarting it an "initializing Intel Boot Agent" appears. I'm guessing that the ethernet driver goes with the Intel Boot Agent, but cannot get why it doesn't load if not restarting. I already disabled the fast start and anything else that could mean not loading drivers/modules but it doesn't seem to make any difference.

If you can give me any pointers, please do. I can live restarting my computer every time after turning it on, however I'd rather have a computer which works and loads properly each time.

---

### Post by mevik on 2012-10-24
I know I am the only one writing here, but will keep doing it in case someone can help by reading the new details or if someone with the same issue gets any help.

I got IBA to start even when turning on and not rebooting, just had to enable PXE OPROM from the mobo settings. On the other hand, it seems like that wasn't the issue. I get the IBA message at the beginning but the computer still fails to connect to the wired network if being turned on (rebooting always works).

Any ideas?

---

