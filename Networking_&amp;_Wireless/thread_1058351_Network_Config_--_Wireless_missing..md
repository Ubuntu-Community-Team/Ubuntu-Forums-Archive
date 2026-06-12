---
title: "Network Config -- Wireless missing."
date: 2009-02-02
forum: Networking &amp; Wireless
---

### Post by A13kSAk3 on 2009-02-02
Hi all. 
I posted before, but I have not found a solution yet. Here's a the problem as simple as I could possibly explain it:

System > Administrator > Network

And I don't get the as an option. Theres wired,dsl, but not wireless. I have an hp, Atheros AR5007 802.11b/g WiFi Adapter I can't get i-net access while booting Ubuntu and it really stresses me out.  Idk if it's my wireless card that Ubuntu does not support, idk what it is. I checked, and Ubuntu is "stealing" a driver from windows, even though I cannot get it to work.

Thank you all. I'm being patient. Just want to dip into Ubuntu and never get out, but without i-net and access to forums, I cannot do much..

---

### Post by yeats on 2009-02-02
This is an extremely frustrating problem, and the answer is madwifi:

[http://madwifi-project.org/]("http://madwifi-project.org/")

It's a long road, though, even after you know this.  I'm sure some pros can step in and help explain.

---

### Post by bumanie on 2009-02-02
Are you able to plug the computer into an ethernet port to get the internet working whilst you download the appropriate driver? I have the same card on my laptop and got it going with the use of backports - I tried madwifi but couldn't get it to work. If you can connect to ethernet, let me know, and I'll try and help you get connected.

---

### Post by A13kSAk3 on 2009-02-02
ok .. here's my next step. watched about 10 videos on NDISwrapper, im going to try to install the drivers from windows. That is what i think i need. Thanks all.

---

### Post by A13kSAk3 on 2009-02-02
can you please guide me thru madwifi installation.. i never really used linux before. Just in case installing the drivers does not work.

---

