---
title: "What command can I use to determine the address by ISP allocates to me?"
date: 2011-08-01
forum: Networking &amp; Wireless
---

### Post by bwallum on 2011-08-01
In the terminal, what command can I use to find out the current ip address that my ISP allocates to me from their server to my router?

---

### Post by nm_geo on 2011-08-01
try this one 

```
wget -q -O - checkip.dyndns.org|sed -e 's/.*Current IP Address: //' -e 's/<.*$//'
```

[http://www.go2linux.org/what-is-my-public-ip-address-with-linux](http://www.go2linux.org/what-is-my-public-ip-address-with-linux)

---

### Post by bwallum on 2011-08-01
Hole in one! Thank you!

EDIT
Also found a script to automate the process using an alternative source, [www.whatismyip.com:-](www.whatismyip.com:-)

----------------------------------
#!/bin/bash 
# 
#  From: [http://ubuntuforums.org/showthread.php?t=526176](http://ubuntuforums.org/showthread.php?t=526176) 
# echo Your external IP Address is: 
wget [http://automation.whatismyip.com/n09230945.asp](http://automation.whatismyip.com/n09230945.asp) -O - -o /dev/null 
echo  
exit 0

---

