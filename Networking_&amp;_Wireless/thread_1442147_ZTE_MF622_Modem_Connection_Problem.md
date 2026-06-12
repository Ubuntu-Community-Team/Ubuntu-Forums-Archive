---
title: "ZTE MF622 Modem Connection Problem"
date: 2010-03-29
forum: Networking &amp; Wireless
---

### Post by Minsky on 2010-03-29
I have a mobile broadband connection using a ZTE MF622 USB dongle with Karmic as my OS. The dongle works well apart from a slight annoyance, it seems to be temperamental when connecting to the internet. Sometimes, I can connect on-line at the first attempt, but more often than not, it takes several attempts with disconnecting and connecting again before I can get on-line. The connected wireless icon appears in the top panel at each attempt which suggests that I am on-line, but I cannot access any web pages or my email so I have to disconnect and try again. I dual boot with Windows XP and I can connect on-line at the first attempt every time with XP. If its any help, the output in the log file at each failed attempt states that the remote IP address could not be determined and so defaults to 10.64.64.64. Can anyone help me to resolve this?

---

### Post by alexfish on 2010-03-29
Hi

can you have a look here , read carefully

[http://ubuntuforums.org/showthread.php?t=1438828](http://ubuntuforums.org/showthread.php?t=1438828)

try  the replacedefaultroute or the  IPCP configure-NAKs returned before starting 

regards

alexfish

---

### Post by Minsky on 2010-03-29
Thanks Alexfish, I'll try that for a few days and I'll let you know how I got on.

---

### Post by Minsky on 2010-04-04
I'm pleased to say that enabling the **pcp-max-failure** setting fixed the problem. I also had success with an alternative method, I normally have **ping** and **traceroute** disabled, and I found that by enabling them, my connection worked at the first attempt though I didn't test this method for a sufficient length of time to determine if it was a permanent solution. Thanks again Alexfish.

---

