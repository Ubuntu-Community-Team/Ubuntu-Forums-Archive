---
title: "Secript checking for inet connection make a pptp connection and mount share"
date: 2011-06-13
forum: Networking &amp; Wireless
---

### Post by apamix on 2011-06-13
Hello dudes ;) I want to write a  script what do this things 

1) First check from time to time for Internet Connection
2) If you have connection make pptp connection to fixed ip 
3) then mount the network sharing for the pptp server ...  

Can somebody help me with this thing ...

I have something for begging but he is not in period time  

```
#!/bin/bash

WGET="/usr/bin/wget"

$WGET -q --tries=10 --timeout=5 http://www.google.com -O /tmp/index.google &> /dev/null
if [ ! -s /tmp/index.google ];then
    echo "no"
else
    echo "yes"
fi

```

---

