---
title: "Wifi won't connect on campus"
date: 2010-09-01
forum: Networking &amp; Wireless
---

### Post by JD32 on 2010-09-01
Just upgraded to ubuntu 10. My wireless was working fine at home, it picked up my wireless no problem and connected just fine. I get to campus today and now it won't connect (let alone even pick up) the network. It's an open network that you just have to click agree once you connect. No password or anything so that's why I don't no y it won't pick it up. My wireless is on and active so it says. I'm typing this on my phone and I got a long day here so any help would be greatly appreciated!

---

### Post by MaindotC on 2010-09-01
There's a [Ubuntu Wireless Troubleshooting Guide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide) that will help you determine the problem, especially checking to see if your wireless card is even associating with the campus network.  Please follow the troubleshooting and let us know if you have any difficulty and at what point in the troubleshooting you are having problems.

---

### Post by JD32 on 2010-09-01
Well my wifi card is working but I got 2 the point about there mayb being 2 drivers installed. (I can post the code when I get home) it looks like there might b two but I don't understand how I was using my home wireless last night just fine. It even picks up the networks when I run nm-tool and I tried 2 manually connect through the network tools, mayb connect through the terminal which I'm not sure how to do?

---

### Post by JD32 on 2010-09-01
so now back at home and it connects to my home wifi no problem????

---

### Post by Iowan on 2010-09-01
Check your IP address (**ifconfig -a**). When on campus, see if you get an IP address - or if keeps the one it has at home.

---

### Post by uRock on 2010-09-01
My campus requires shows a log in and password. You have tried opening Firefox?

---

### Post by MaindotC on 2010-09-02
> **uRock said:**
> My campus requires shows a log in and password. You have tried opening Firefox?

He already mentioned in the first post that there does appear to be a captive portal but it simply asks for an agreement of the terms of use, not credentials.

---

