---
title: "Replacing Network Manager with Wicd - glitches and solutions"
date: 2010-09-05
forum: Networking &amp; Wireless
---

### Post by yashaneiman on 2010-09-05
I'm running Ubuntu 10.04 on an LG laptop. I'm connecting to my home wireless network with WEP encryption.

The default Network Manager handles this fairly well. However, I prefer using Wicd, since it starts scanning for networks at boot time, saving me an annoying wait after I log in.

I wanted to share the problems I ran into while switching, and how to avoid them. 

The solution that worked is as follows:
1. Install the wicd package (with Synaptic, or whatever is your preferred method).
2. Reboot.
3. Now you should have the Wicd icon at the upper right of the screen, along with the Network Manager icon. Click it to check that it can see your wireless networks.
4. Remove the packages network-manager, network-manager-gnome, network-manager-pptp and network-manager-pptp-gnome.
5. Reboot.

The documentation claims that step 1 should uninstall Network Manager automatically. That doesn't happen for me.
If I try to uninstall Network Manager (step 4) together with step 1, Wicd doesn't detect wireless networks at all.
If I don't do step 4 at all, Wicd detects the networks, but cannot connect, giving a "Bad Password" message.

Cheers, hope this helps.

---

### Post by wrtrgeek on 2010-09-11
Thank you!!! I spent all day yesterday trying to get my wireless connection to work, settled on using Wicd, had it working fantastically before bed... then woke up to a hot mess!! But your steps helped me backtrack, reinstall it all, and it's working again!! Thank you!!

---

### Post by MaindotC on 2010-09-12
Please mark the thread as "Solved"...I guess.

---

### Post by mariost on 2010-12-29
Awesome thread, thank you for posting this. I have tried to switch to wicd before, only to stumble upon the Bad Password dead end. Now its working :) Only I've got two questions: which should i use as DHCP Client (Preferences>External Programs) - automatic, which i believe is dhclient(third option), or dhcpcd, which i installed before, when i couldnt get it to work. Ive got only these three options, other are grayed out. Both auto and dhcpcd work, no noticeable difference. And the other question, the only one still being a problem with wicd: with nm-applet my 3G GPRS vodafone dongle asked for password upon plugging and then could select it from the network managed menu. I don't see such an option using wicd, can someone tell me how to use it with this manager?

---

