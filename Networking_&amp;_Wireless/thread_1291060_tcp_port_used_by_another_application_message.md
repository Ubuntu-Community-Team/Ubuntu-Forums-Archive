---
title: "tcp port used by another application message"
date: 2009-10-14
forum: Networking &amp; Wireless
---

### Post by folabiklan on 2009-10-14
hello, pls am a noob, only 1 month at ubuntu so humor me. i use a proxy client called freedom and 9i discovered that when i start it it gives me an error message that it cannot create a socket on port 8080. therefore i cant tunnel thru that port. pls how do find what app is that and how do i free that port so i can use it

---

### Post by puppywhacker on 2009-10-14
I always use lsof to find which process is listening to a port.
```
sudo lsof -i:8080
```

If it is not installed you can  can install it by running
```
sudo apt-get install lsof
```

---

