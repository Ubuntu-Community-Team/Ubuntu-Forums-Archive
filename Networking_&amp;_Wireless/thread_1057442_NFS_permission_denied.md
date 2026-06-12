---
title: "NFS permission denied"
date: 2009-02-01
forum: Networking &amp; Wireless
---

### Post by f37u5g0d on 2009-02-01
I set everything up and when I try to mount my share from my client with sudo mount "ip of server":/"directory" /"directory on client" I get an error "accessed denied by server while mounting"  What's the deal?  The UID and user name are the same on the client and the server.

---

### Post by JillSwift on 2009-02-01
What's in your /etc/exports file?

---

### Post by Crafty Kisses on 2009-02-01
Have you ran the following yet?
```
exportfs -a
```

---

### Post by f37u5g0d on 2009-02-02
I went to post my exports file and I realized that my problem was that I had the wrong ip in there (typo).  Thanks though guys!

---

