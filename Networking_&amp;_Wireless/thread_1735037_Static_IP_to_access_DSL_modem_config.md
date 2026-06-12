---
title: "Static IP to access DSL modem config"
date: 2011-04-20
forum: Networking &amp; Wireless
---

### Post by nick3501 on 2011-04-20
So i have a d-link modem and the DHCP server is not running. I need to access the internal config to do some troubleshooting.  IP is supposed to be 192.168.1.1, but I only have my DSL ppoe IP, and can not access it.  Can anyone help?

---

### Post by dineshs on 2011-04-21
Configure ethernet as in
[http://ubuntuforums.org/showpost.php?p=9467538&postcount=5](http://ubuntuforums.org/showpost.php?p=9467538&postcount=5) 
Configure DSL as in 
[http://ubuntuforums.org/showpost.php?p=9611335&postcount=9](http://ubuntuforums.org/showpost.php?p=9611335&postcount=9)
Now if you want to enter modem menu click on Network manager icon,disconnect DSL ,connect ethernet , open browser, type 192.168.1.1 on the address bar and click go
If you want to connect DSL click on Network manager click DSL connection and proceed
Is this what you want?

---

### Post by nick3501 on 2011-04-21
bingo...worked like a charm:P:guitar:

---

### Post by dineshs on 2011-04-25
Please mark the thread as [solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") via thread tools

---

