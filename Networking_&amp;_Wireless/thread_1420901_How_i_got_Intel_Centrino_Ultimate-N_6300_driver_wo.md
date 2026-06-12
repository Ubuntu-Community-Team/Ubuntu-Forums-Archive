---
title: "How i got Intel Centrino Ultimate-N 6300 driver working."
date: 2010-03-03
forum: Networking &amp; Wireless
---

### Post by TwoWordz on 2010-03-03
Hello,

I just thought I should drop this here so it's easy to find.

To make Intel Centrino Ultimate-N 6300 wireless card work on ubuntu, you just need to download the firmware from [here]("http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-6000-ucode-9.193.4.1.tgz") decompress it and copy the ucode in /lib/firmware.

This works in jaunty.

My laptop is a HP Elitebook 8440p. 

Hope this helps.  

TW

---

### Post by blackrim on 2010-03-23
i have the same card and installed the driver but i get a "network DISABLED" when i run lshw -C network. any ideas (would love ideas also on the brightness buttons, and sound too -- i have an 8440w)

---

### Post by blackrim on 2010-03-23
fixed. i needed to install linux-backports-modules-karmic

---

