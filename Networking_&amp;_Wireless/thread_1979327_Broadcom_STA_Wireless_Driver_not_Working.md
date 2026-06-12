---
title: "Broadcom STA Wireless Driver not Working"
date: 2012-05-13
forum: Networking &amp; Wireless
---

### Post by The Idiot on 2012-05-13
So, after upgrading to Linux 12.04, my wireless driver stopped working. I tried to activate it using "additional drivers" under system settings, it tells me to look at the log file. I looked under var/log/jockey and got this as the message:

2012-05-13 07:15:05,258 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-05-13 07:15:05,296 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2012-05-13 07:15:05,296 DEBUG: nvidia_current is not the alternative in use
2012-05-13 07:15:06,454 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2012-05-13 07:15:06,596 DEBUG: KMH enabled: True
2012-05-13 07:15:07,947 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-05-13 07:15:07,977 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-05-13 07:15:08,008 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2012-05-13 07:15:08,008 DEBUG: nvidia_current is not the alternative in use
2012-05-13 07:15:08,055 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2012-05-13 07:15:08,189 DEBUG: KMH enabled: True
2012-05-13 07:15:27,985 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-05-13 07:15:33,242 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-05-13 07:15:33,242 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2012-05-13 07:15:33,386 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-05-13 07:15:35,332 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-05-13 07:15:35,366 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2012-05-13 07:15:35,366 DEBUG: nvidia_current is not the alternative in use
2012-05-13 07:15:35,440 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2012-05-13 07:15:35,584 DEBUG: KMH enabled: True
2012-05-13 07:15:35,882 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-05-13 07:15:35,911 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-05-13 07:15:35,943 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2012-05-13 07:15:35,944 DEBUG: nvidia_current is not the alternative in use
2012-05-13 07:15:35,990 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2012-05-13 07:15:36,137 DEBUG: KMH enabled: True
2012-05-13 07:15:37,552 DEBUG: Shutting down

Sorry, I know it's a lot. Around where it mentions Broadcom STA driver, it mentions something being blacklisted. I have a hunch I need to take it off the blacklist but I don't know how and I don't even know if this will solve it. It is hard to get to the internet now so I would appreciate help ASAP. (Using library).
Please help!!! :sad:

---

### Post by chili555 on 2012-05-13
Let's identify your exact device. Please run and post:```
lspci -nn | grep 0280
```I will be right here and we can solve this in a few moments.

PS- I guess you left the library already.

---

### Post by DeepThoughtV2 on 2012-05-13
I have a similar problem with the same driver, I think mine is due to the wifi power management,
The wireless might work when pluged in, worth a try to check the problem.
James

---

### Post by chili555 on 2012-05-13
> **DeepThoughtV2 said:**
> I have a similar problem with the same driver, I think mine is due to the wifi power management,
The wireless might work when pluged in, worth a try to check the problem.
JamesWould you care to start your own new thread and troubleshoot? The doctor is in.

---

