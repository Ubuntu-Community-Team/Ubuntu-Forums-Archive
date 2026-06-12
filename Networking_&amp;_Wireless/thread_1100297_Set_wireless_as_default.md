---
title: "Set wireless as default"
date: 2009-03-19
forum: Networking &amp; Wireless
---

### Post by TriloByte on 2009-03-19
[The tag is supposed to be ubuntu, not xubuntu]

At the moment my Aito Eth0 internet is set as the computers default, so it wont let me connect to a wireless network, how can I change it from Auto Eth0 Default to Wireless?

Screen shot of what I mean:

---

### Post by mikewhatever on 2009-03-19
Your wireless card may be associated with wlan0 or eth1, so that you need not change anything related to eth0. From the look of that screenshot, it seems no wireless interface is detected. You may want to verify it with
**sudo lshw -C network**.

---

