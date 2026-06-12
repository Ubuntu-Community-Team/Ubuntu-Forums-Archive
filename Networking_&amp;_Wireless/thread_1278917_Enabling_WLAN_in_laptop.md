---
title: "Enabling WLAN in laptop"
date: 2009-09-30
forum: Networking &amp; Wireless
---

### Post by rkannanunni on 2009-09-30
Hi, i am desperate. Am new to Linux and Ubuntu. Have loaded Ubuntu 9.04 on my ACER Aspire 4520 laptop. Nothing seems to be getting my wi-fi to work. have tried installing all possible wireless applications from "add/ remove"... but its been of no avail. I have a Netgeat wireless router WGR614 v7. Could someone give me basic instructions on activating my wifi?

regards, Kannan

---

### Post by lisati on 2009-09-30
I wish to confirm that your router is compatible with Ubuntu (I have one too, works well).
Does your network show when you click on the network icon on the top right of your screen? (If you're using a wired connection it will look like a couple of small computer screens, otherwise it will look like a bar graph)

---

### Post by t0mppa on 2009-09-30
If you're not seeing networks through network manager (see the screen shot), open up a terminal (Applications / Accessories / Terminal), run **lshw -C network** and post back with the results to see what the status of your wireless & its drivers are.

---

