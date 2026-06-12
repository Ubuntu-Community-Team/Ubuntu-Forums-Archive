---
title: "Disconnect modem when postfix queue empty"
date: 2011-11-07
forum: Networking &amp; Wireless
---

### Post by Nerdhacker on 2011-11-07
in **/etc/ppp/ip-up.d/script** I have the following that runs fetchmail when the **ppp0** interface is up (connected) and when it finish the modem ends internet conection automatically.

```
 #!/bin/sh
 /usr/bin/fetchmail -v -f /etc/fetchmailrc -L /var/log/fetchmail.log
 killall wvdial
```

this works perfectly. now i need to add to the script below the fetchmail command execution something that checks if the mail queue of postfix is completely empty and if is true then execute the command **killall wvdial** to hangup the modem.

In theory i know i could do something using **if, else, do, while, until**, etc. but in practice i do not know how to develop it. I would like you guys to help me to program and complete this script to work properly. I appreciate the comments.

---

