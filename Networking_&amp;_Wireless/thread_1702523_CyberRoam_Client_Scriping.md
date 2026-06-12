---
title: "CyberRoam Client Scriping"
date: 2011-03-07
forum: Networking &amp; Wireless
---

### Post by hitman2k9 on 2011-03-07
Guys I have an ISP using cyberroam client so I have made a .sh for login  and logout ..but I wast to create a script which will re login so that  IP changes ... The problem is that am not able to fine a function to  delay the calls in between .
 
I have this file 
LOGIN.sh
"
cd Desktop
./crclient -u <username>
"
 
LOGOUT.sh
"
cd Desktop
./crclient -l
"
 
So is there a way I can use them both in a new .sh or any other [executable file]("http://en.wikipedia.org/wiki/Executable_file") after 10-20secs say... And am using this on Jdownloader <- If this info helps :/

---

### Post by hitman2k9 on 2011-05-04
Finally got it working .
**[SIZE="3"]Relogin.sh[/SIZE]** stands as
```
cd Desktop
./crclient -l
sleep 20s
./crclient -u <user>
```

**[SIZE="3"]Jdownloader[/SIZE]** settings stand like this .

[IMG]http://forums.linuxmint.com/download/file.php?id=6417[/IMG]

---

