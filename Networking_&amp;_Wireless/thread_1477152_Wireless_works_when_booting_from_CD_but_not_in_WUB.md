---
title: "Wireless works when booting from CD but not in WUBI"
date: 2010-05-08
forum: Networking &amp; Wireless
---

### Post by cunniman on 2010-05-08
Hi,

I am a complete Ubuntu newbie.  If I boot Ubuntu 10.04 LTS from CD, it prompts me that I need to install drivers for my NIC wireless card and links me to a generic Broadcom driver. After installation of this driver I can see my wireless network.

If I then reboot and boot into a Wubi installation I created, my wireless adapter light stays off and I get a message that Wireless networks are disconnected.

Do I need to do something to get the same drivers installed under Wubi, or is this a separate issue?

Thanks in advance

Mark

---

### Post by cunniman on 2010-05-09
Just for info, I found the solution to my problem.  I created a wired connection and then I went to "System-Administration-Hardware Drivers" and got a list of available drivers. I chose the Broadcom B43 wireless driver and it has been working perfectly for me. Hope this helps you.

---

