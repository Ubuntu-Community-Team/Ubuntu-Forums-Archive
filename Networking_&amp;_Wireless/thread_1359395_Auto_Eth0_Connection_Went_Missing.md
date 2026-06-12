---
title: "Auto Eth0 Connection Went Missing?"
date: 2009-12-19
forum: Networking &amp; Wireless
---

### Post by SirKablaam on 2009-12-19
My internet connection shut down for a little while. As I was trying to reconnect, auto eth0 went missing and i cant no longer connect to the internet, how can i get auto eth0 back up on ubuntu without reinstalling. btw, im using another computer to post this.

---

### Post by Iowan on 2009-12-19
You could probably rebuild it... Have you restarted the machine since the incident? A few (jaunty-era) threads suggested that Auto eth0 kept regenerating itself (much to their chagrin). 
Might check **ifconfig -a** and/or **lshw -C network** to verify the interface is still active.

---

### Post by SirKablaam on 2009-12-20
i got it back, fortuntely for me I kept the installation disc and wrote down the MAC code. Put it into Wired Connection 1, all set. :)

---

