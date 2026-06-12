---
title: "Unable to connect to local LAN computer via IP address"
date: 2010-07-27
forum: Networking &amp; Wireless
---

### Post by sincityharley on 2010-07-27
I recently setup motion on one of my computers with a USB camera. On that computer if I type [http://localhost:8081](http://localhost:8081) I can see my live video. If however I type [http://192.168.1.103:8081](http://192.168.1.103:8081) on that computer or any other on my wireless network, I get a page cannot be displayed. I checked that UFW was disabled and I am able to ping the motion computer from any other computer on my network. Also I am not sure if it matters but I do have apache installed on my motion computer as well. If someone could help me understand why I cant view my live video from different computers I would be much appreciated. Thanks. 

I am using Ubuntu 10.4 on all computers

---

### Post by heimo on 2010-07-27
Not 100% sure, but check if you have "control_localhost on" setting in motion.conf and turn it "off". Restart/reload motion and try again.

---

### Post by sincityharley on 2010-07-27
Thanks very much. It wasn't control_localhost but it was two lines away called webcam_localhost or something to that effect. I really appreciate you pointing me in the right direction.

---

### Post by heimo on 2010-07-27
> **sincityharley said:**
> Thanks very much. It wasn't control_localhost but it was two lines away called webcam_localhost or something to that effect. I really appreciate you pointing me in the right direction.

Ah, excellent! Glad I was able to help even though my answer wasn't correct. :-)

---

### Post by Iowan on 2010-07-27
Would it be safe to assume the problem is [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")? :)

---

