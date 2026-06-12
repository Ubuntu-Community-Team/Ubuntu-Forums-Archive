---
title: "DHCP /30 server"
date: 2011-01-04
forum: Networking &amp; Wireless
---

### Post by phrysque on 2011-01-04
I'm looking for a DHCP server that provides IP addresses in the /30 subnet--similar to what Cisco NAC (formally Clean Access) provides.  Does anyone have a suggestion for such a configuration?

Thanks.

---

### Post by anystupidname1 on 2011-01-04
Are you saying dhcp3-server won't let you configure it to assign a 30 bit mask for some reason?

option subnet-mask 255.255.255.252;

[https://help.ubuntu.com/community/dhcp3-server](https://help.ubuntu.com/community/dhcp3-server)

Sorry if I didn't understand your question...

---

### Post by phrysque on 2011-01-05
Thanks!  You understood my question correctly...  Every google search I tried came up unhelpful, so I thought i'd give the forum a shot!  Thanks for your quick response.  Now that I have a direction I'll give it a shot and play.  Thanks for the link to the docs too.

---

### Post by anystupidname1 on 2011-01-05
No problem, you're welcome. Don't forget to mark the thread "solved". "Thread Tools" link up there >^

---

