---
title: "Strange netstat listing"
date: 2009-10-27
forum: Networking &amp; Wireless
---

### Post by lavajumper on 2009-10-27
This is something that's been bugging me for years. When I do a netstat -anutp, I get a number of entries like the ones here:

```

Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:2049            0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:41993           0.0.0.0:*               LISTEN      -               
udp        0      0 0.0.0.0:2049            0.0.0.0:*                           -               
udp        0      0 0.0.0.0:44209           0.0.0.0:*                           -               

```

Note the PID being listed. I assume there is not anything 'wrong' as this has been happening on every Linux installation I've seen, It's just that a listen socket with no process id bugs me. Can anyone shed some light on this? 

(If this isn't the right forum, please let me know which I should post in)

---

### Post by kreggz on 2009-10-28
try the security forum

---

