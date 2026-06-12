---
title: "Networks are found but don't connect"
date: 2011-06-29
forum: Networking &amp; Wireless
---

### Post by Coolcam262 on 2011-06-29
I tried installing Ubuntu 10.04 LTS, the networks were shown but when I clicked them they didn't connect. I just upgraded to 11.04 to try and solve my problem but it didn't help. It doesn't work with any networks and it doesn't give an error it just times out. Do you have any idea of what I should do?

Thanks,
Cameron

---

### Post by Coolcam262 on 2011-06-30
Anyone?! Please help!! What information would i need to provide?

---

### Post by georgelab on 2011-06-30
Did you try to disable/enable your network card to see if the issue remains? I had some problems like these when I was running 10.10, and I could solve the issue by reinstalling the network driver. It was a broadcom one.

---

### Post by Iowan on 2011-06-30
Wired or wireless networks?
**sudo lshw -C network** from a terminal (Applications>Accessories>Terminal) should provide details on the hardware.

---

