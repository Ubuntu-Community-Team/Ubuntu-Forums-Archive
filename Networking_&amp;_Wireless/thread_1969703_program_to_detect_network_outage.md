---
title: "program to detect network outage"
date: 2012-04-30
forum: Networking &amp; Wireless
---

### Post by Skaperen on 2012-04-30
I'm looking for a program (so I don't have to develop one ... you know, why re-invent the wheel) to do a simple detection of a network outage.  It would be like the ping program, but with some changes.  It would have a list of IP addresses and the network is considered out if ALL of them cannot be reached for a specific time interval.  One should not depend on a single IP since maybe just that one computer goes down.  As long as the network is up, it should stay running and keep pinging at whatever rate is specified (though maybe up the rate when packets start to go missing).  When their is a failure, it can exit with a special status code, or send a message somewhere, or start another program.

Do I need to invent this program?

---

