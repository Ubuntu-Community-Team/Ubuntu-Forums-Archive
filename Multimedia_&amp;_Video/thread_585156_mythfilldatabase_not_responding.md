---
title: "mythfilldatabase not responding"
date: 2007-10-21
forum: Multimedia &amp; Video
---

### Post by bnuytten on 2007-10-21
During setup of the backend I run into the following problem. When running mythtv-setup, it first stops mythbackend and than wants to run mythfilldatabase. When mythfilldatabase is started it hangs like forever, no error messages, nada. I have run mythfilldatbase with verbose debugging as below but still no clue.

```
$ mythfilldatabase --verbose all
2007-10-21 18:26:28.652 Using runtime prefix = /usr
2007-10-21 18:26:28.666 New DB connection, total: 1


```

---

### Post by bnuytten on 2007-10-27
Well, I found the issue. Somewhere in the database, the wrong IP address for the mythbackend server was stored. Because I use DHCP, that IP address had changed and as a consequence, the mythbackend was not available anymore at that IP.

It would be great if mythfilldatabase would print some more "debug" information. It would have obvious see that the IP was incorrect.

---

