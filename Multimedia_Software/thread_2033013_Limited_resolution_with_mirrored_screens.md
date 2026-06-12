---
title: "Limited resolution with mirrored screens"
date: 2012-07-25
forum: Multimedia Software
---

### Post by Priceguy on 2012-07-25
I just bought a new laptop, installed Ubuntu 12.04 on it, and then connected an external monitor to it, one I have been using with my old Ubuntu laptop for years.

When I do not mirror screens the laptop's resolution can be set up to 1366*768 and the external monitor's can be set up to 1280*1024, but when they are mirrored I can't set it to higher than 1024*768.

As I'm writing this I'm realizing the problem; the laptop can't go higher than X*768 and is 16:9 while my external monitor is 4:3. Still strange as my old laptop was 16:9 as well.

Is there anything to do about this that doesn't involve buying a new monitor? I'm running Gnome Fallback if it matters.

---

### Post by Priceguy on 2012-07-25
I realized I hadn't installed additional drivers for my graphics card and found two under System Settings - Additional Drivers: ATI/AMD proprietary FGLRX graphics driver, and one with the same name and post-release updates added. Neither could install; I got an error message telling me to check /var/log/jockey.log which turned out to contain, among 2000+ lines, the following that looked to me most like an explanation:

2012-07-25 11:31:29,251 DEBUG: fglrx_updates is not the alternative in use
2012-07-25 11:31:29,476 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-07-25 11:31:29,870 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted

---

### Post by Priceguy on 2012-07-25
After a few updates I managed to install one of the proprietary drivers, not the "post-release updates" one. I can now set a higher resolution but only a 16:9 or 16:10 one. I can choose between having a bad resolution or a squished image.

I understand that when mirroring a 4:3 screen and a 16:9 screen, one of them will inevitably look awful. I want the laptop screen to look awful since I only use it when travelling and then the external monitor isn't involved anyway. Surely there must be a way to accomplish this?

---

### Post by Priceguy on 2012-07-25
But even after installing the proprietary driver I now see that it is not activated under Additional Drivers. It installs fine, I reboot, and it is not activated.

---

