---
title: "Ubuntu 9.10 loses Connectivity when it sleeps."
date: 2010-02-05
forum: Networking &amp; Wireless
---

### Post by jrb56 on 2010-02-05
Hi.  I had a lot of trouble with my broadcom card, but eventually (with a lot of your help) I got it to work.  It's been preforming wonderfully for a couple months but now it suddenly loses wireless connectivity every time I put it to sleep. 

I just have to restart it and it works again (Good thing it restarts so fast)  but it's still a bit annoying.

Any ideas?

---

### Post by jrb56 on 2010-02-05
Bump bump bump

---

### Post by imrazor on 2010-02-05
I believe Ubuntu can be set up to run scripts when being put to sleep or woken up, but I'm not familiar with them. You might try posting in Hardware & Laptops to see if someone there can help. Otherwise a couple of commands that *might* work:```
bash> sudo service networking restart
``` This will restart ALL of your network devices, and might bring the Broadcom back up. Assuming your Broadcom is a bcm4300 chipset, these commands might work as well:```
bash> sudo rmmod b43
bash> sudo modprobe b43
bash> sudo service networking restart
```
Good luck!

---

### Post by jrb56 on 2010-02-07
Thanks a lot.  You are a life saver
This worked for me


sudo rmmod b43
sudo modprobe b43



> **imrazor said:**
> I believe Ubuntu can be set up to run scripts when being put to sleep or woken up, but I'm not familiar with them. You might try posting in Hardware & Laptops to see if someone there can help. Otherwise a couple of commands that *might* work:```
bash> sudo service networking restart
``` This will restart ALL of your network devices, and might bring the Broadcom back up. Assuming your Broadcom is a bcm4300 chipset, these commands might work as well:```
bash> sudo rmmod b43
bash> sudo modprobe b43
bash> sudo service networking restart
```
Good luck!

---

