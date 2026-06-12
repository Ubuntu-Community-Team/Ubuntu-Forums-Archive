---
title: "HELP: Networking Disabled"
date: 2010-06-09
forum: Networking &amp; Wireless
---

### Post by tripower on 2010-06-09
Assistance please. I all of a sudden have a networking disabled message. I did a search and found this post:

[http://www.uluga.ubuntuforums.org/showpost.php?p=4702242&postcount=2](http://www.uluga.ubuntuforums.org/showpost.php?p=4702242&postcount=2)

But when I try to save or overwrite this interface file I get a permissions error. I am logged in as admin. What gives? How do I change this file and how can I fix this networking disabled problem??

---

### Post by Iowan on 2010-06-09
Hey, that looks vaguely familiar... ;)
Back in '08, Network Manager seemed a little less aggressive. I'm not sure how you're logging in as "admin", but ```
sudo nano /etc/networking/interfaces
``` or ```
gksudo gedit /etc/networking/interfaces
``` should let you edit the file. From other threads, that might/not help. 
First, right-click the Network Manager icon to verify networking is enabled there... some threads suggest updates somehow turn it off. Another place to check: [I]/var/lib/NetworkManager/NetworkManager.state
[/I]

---

