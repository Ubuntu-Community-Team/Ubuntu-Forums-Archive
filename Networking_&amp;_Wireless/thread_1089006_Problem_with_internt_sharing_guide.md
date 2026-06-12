---
title: "Problem with internt sharing guide"
date: 2009-03-06
forum: Networking &amp; Wireless
---

### Post by Skaterguy on 2009-03-06
ok first off i have ubuntu 8.10. I what trying to fallow the guide but when i typed in (# ifconfig eth0 ip) but all the came up was ip: unknown host. I am tired of MS windows and want to use other means. but i am 100% linux illiterate. wtf do i do now.

---

### Post by Iowan on 2009-03-06
The # was there to show that input was from a terminal.  **ip** should be an IP address.  Substitute your IP address instead of 192.168.1.4 when you enter the following in a terminal:```
ifconfig eth0 192.168.1.4
```

---

### Post by Skaterguy on 2009-03-07
ok that explains alot thank you. sorry for being a nub. now i just fallowed your instructions and i got this message
dman@dman-desktop:~$ ifconfig ath0 192.168.1.254
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied

should i use su mode to do this or what.

btw way i connect to a wireless network with my computer and another computer does not have a wireless card. i have to share the Internet using mine as the host and i link my pc to a linksys router and then the other computer connects to the router. i hate to say but the one thing i like about MS is that there is a easy to use network wizard so all i have to do is point and click.

---

### Post by curadebt on 2009-03-07
Try to find useful information from internet instead of buying guides.

---

### Post by Skaterguy on 2009-03-07
thats what im trying to accomplish here try and get some tips to help me move things along. and believe me i try to google everything. but i no nothing about linux im so used to xp its almost trying to learn a new language alot of time and patience.

---

### Post by Gary13579 on 2009-03-07
> **Skaterguy said:**
> ok that explains alot thank you. sorry for being a nub. now i just fallowed your instructions and i got this message
dman@dman-desktop:~$ ifconfig ath0 192.168.1.254
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied

should i use su mode to do this or what.

btw way i connect to a wireless network with my computer and another computer does not have a wireless card. i have to share the Internet using mine as the host and i link my pc to a linksys router and then the other computer connects to the router. i hate to say but the one thing i like about MS is that there is a easy to use network wizard so all i have to do is point and click.

Then you should really go back to Windows.

Also, permission denied errors can almost always be overridden by typing "sudo" before the command.

---

### Post by ugm6hr on 2009-03-07
Couple of points:

1. What guide are you using?

2. Use *sudo* at the start of the line when entering commands that require super-user permission.

---

### Post by Iowan on 2009-03-07
Oops, my bad... sometimes I forget about **sudo** until I try a command and get the Permission Denied message.  You done good (butchered English intentional) to seek information via forum - sorry I led you astray. Linux does require you to "intervene" a bit when setting stuff up.  Ordinarily, that's a good thing - it lets you "Have it your way" (sorry Burger King), but sometimes that means getting your hands a little dirty.

---

