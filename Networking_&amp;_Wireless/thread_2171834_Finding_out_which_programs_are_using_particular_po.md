---
title: "Finding out which programs are using particular ports"
date: 2013-09-01
forum: Networking &amp; Wireless
---

### Post by jefelex on 2013-09-01
Hi All - i was checking my network usage, everything seems normal, except for one item which kept coming up with an unusal port # to receive data on that I was not expecting to see.  I wondered if there is a gui or cl utility to tell me what program is using data from what port

Thanks in advance!

John

---

### Post by steeldriver on 2013-09-01
You can use netstat with the -p or --program switch

```

   -p, --program
       Show the PID and name of the program to which each socket belongs.

```

e.g.

```
sudo netstat -tnp
```

to see **t**cp connections and the **n**umeric foreign addresses they're connected to; or

```
sudo netstat -tp
```

which tries to resolve the foreign addresses to names. If you're only interested in inbound connections (i.e. things trying to connect to running services on your machine) you can add -l ('listen')

```
sudo netstat -tnpl
```

---

### Post by jefelex on 2013-09-05
Of course - dumb me! I've used that before, but forgot about -p !!
 :)
Thanks

---

