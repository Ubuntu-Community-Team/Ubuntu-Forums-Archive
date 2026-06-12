---
title: "opening port 22"
date: 2006-05-08
forum: Networking &amp; Wireless
---

### Post by orlox on 2006-05-08
Hi...I'm trying to mount a server to create a web application on it, and got it working with apache. However, when i try to ssh from another machine to it, it says

```

root@pcpablo:/# ssh 144.123.38.221 -l guillermo
ssh: connect to host 144.123.38.221  port 22: Connection refused

```

The server is on my college, so I talked to the people in charge of the network, and they told me that port 22 was open...So I guess that the port is closed in the configuration of my server...how can i open it?

---

### Post by the_tiger on 2006-05-08
If you would like to see whether a port is open try:

[http://www.canyouseeme.org/]("http://www.canyouseeme.org/")

---

### Post by orlox on 2006-05-08
I don't have acces to the server right now so i'll check that site tomorrow. Anyway, if that site tells me that my port is closed, what can I do?

---

