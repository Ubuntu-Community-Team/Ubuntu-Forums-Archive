---
title: "Network Manager Auto Reconnect"
date: 2011-09-30
forum: Networking &amp; Wireless
---

### Post by razorxpress on 2011-09-30
Previously I used to run dsl-provider or pppoe-connect, everything was fine. Recently Network Manager has become quite stable. However, dsl or pppoe connection keeps on going down and Network Manager never reconnects. Consequence of this is, I cannot rely my computer to download file whole night. 

If I could run ```
$service network-manager restart
``` I could get the network back. However there is still a problem. It sometimes take 5 to 6 times to get the connection and I have to wait at least 30 seconds for the Network Manager to try to connect and establish the connection or fail.

So, I created a [script]("http://ubuntuforums.org/attachment.php?attachmentid=203238&stc=1&d=1317406277"). Now I can use cron to run this script. If the connection is down it tries to connect and gives at least 30 seconds before trying for 10 iterations.

If you want to try if this script works for you, try setting following setting in crontab to run the script every 2 minutes.
```
$ sudo crontab -e
*/2 * * * * sudo perl /home/username/bin/network_restart.pl
```

Disconnect your network to see if it reconnects. If you are comfortable you can edit the script to change iterations or consecutive connection sleep time. If you like to poll your connection every 1 hour like me you can change crontab as follows

 ```
* */1 * * * sudo perl /home/username/bin/network_restart.pl
```

---

