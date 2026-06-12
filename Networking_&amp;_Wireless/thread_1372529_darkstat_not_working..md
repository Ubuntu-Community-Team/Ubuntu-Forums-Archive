---
title: "darkstat not working."
date: 2010-01-04
forum: Networking &amp; Wireless
---

### Post by markp1989 on 2010-01-04
Im trying to setup darkstat on my server, it runs, and i can normaly see the graph for a few minuts , then the web interface frezzes.

when i run dark stat from the terminal, i get an error  repeatedly (as in fills up terminal constantly) 

saying : 

```
darkstat (06763): tcp: packet too short (28 bytes)
```

im not sure what this means?

i am running deluge web ui on the server if that makes any difference

thanks Markp1989 :)

---

### Post by markp1989 on 2010-01-06
bump?

---

### Post by ar521684 on 2011-02-17
Hello, I found your post while looking for the solution to this.
The solution is to use the 10.10 version on 10.04. [1]
I can confirm that this works.

References: [1] [https://bugs.launchpad.net/ubuntu/+source/darkstat/+bug/576862](https://bugs.launchpad.net/ubuntu/+source/darkstat/+bug/576862)

---

