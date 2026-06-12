---
title: "if-up.d custom script on wireless not running"
date: 2011-03-21
forum: Networking &amp; Wireless
---

### Post by Dege88 on 2011-03-21
In my college wireless ap have a login webpage that I must fill everytime i want to use internet.
To automate the process i've written a bash script that do the login for me.
I've found that scripts in the /etc/network/if-up.d directory should run after a connection is established, but the script isn't executed.

This is the source of the script:
```
#!/bin/sh
if iwgetid |grep -i unimore
then
	echo "Connesso alla wireless dell'università esecuzione dello script di autologin!"
	wget -o /dev/null --spider --secure-protocol=auto --no-check-certificate --post-data="user=user&password=pass" "https://securelogin.arubanetworks.com/cgi-bin/login?cmd=login&mac=00:21:5d:4d:b3:92&essid=UNIMORE"
fi
```

---

### Post by Dege88 on 2011-03-22
Solved:
Scripts with the .sh extension aren't executed automatically in that directory, after a simple rename everything start to work again!

---

### Post by deckoff on 2012-03-08
God bless you, Long live and prosper and may the Force be with you!
I spent two hours here cursing here wondering what the problem is :)

---

