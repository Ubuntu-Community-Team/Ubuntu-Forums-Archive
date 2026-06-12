---
title: "where can i put that Code ?"
date: 2012-04-09
forum: Networking &amp; Wireless
---

### Post by mohamed1042002 on 2012-04-09
[SIZE=3][FONT=Arial Black]hello : 
         i'm new user in ubuntu and i need help in something that i can't solve it out ... problem is that i must type this code at every time i log in to connect to internet ...
Code:
sudo mii-tool -F 10baseT-FD eth0

i need help to avoid type it each time ...where can i put it ? 
thy all.....
[/FONT][/SIZE]

---

### Post by praseodym on 2012-04-09
Hello,

open this file:

```
gksu gedit /etc/rc.local
```
Add the line
```
mii-tool -F 10baseT-FD eth0
```
without "sudo" before "exit 0", save, close, and reboot.

---

### Post by mohamed1042002 on 2012-04-09
[COLOR=Red][SIZE=3][FONT=Arial Black]thy alot u solve it [/FONT][/SIZE][/COLOR]

---

