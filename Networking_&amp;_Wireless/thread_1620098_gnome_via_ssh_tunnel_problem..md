---
title: "gnome via ssh tunnel problem."
date: 2010-11-12
forum: Networking &amp; Wireless
---

### Post by dhysk on 2010-11-12
Ubuntu 10.10_64 (remote machine)
Ubuntu 10.10 (client)

So I have ssh server up and running on my main box.  I'm trying to log into it and start a gnome session by

```

xinit -- :1

ssh -p 22 -X -C -l username ipaddress

```
This bring up a basic xserver and logs into the machine just fine.

However when i do
```

gnome--session

```

its starts as normal however everything displays upside-down and backwards(like a mirror reflection turn upside-down).  

Any ideas?

looks like this guys picture: [http://ubuntuforums.org/showthread.php?t=1269091](http://ubuntuforums.org/showthread.php?t=1269091)

The server is using nvidia drivers however I did this from over seas, same 2 computers, using 9.04 just fine.

---

### Post by dhysk on 2010-11-12
well i think it may be a driver thing because once i was able to disable desktop effects it displayed correctly.....

talk about testing patience.  Not only is everything displayed all crazy the buttons are actually in thier 'proper' spots so you have to guess ware to click... but i got it ;)...

I would still like to fix it so i don't have to bounce back and forth turning effects on and off all the time though ...

---

### Post by zhouleon on 2011-07-23
Start gnome-session if failsafe mode instead :

> gnome-session -f

---

