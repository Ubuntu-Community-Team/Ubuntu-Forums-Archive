---
title: "Networking -  not working"
date: 2010-06-15
forum: Networking &amp; Wireless
---

### Post by sandy8925 on 2010-06-15
I have the same problem! I'm running Kubuntu 10.04 on a sony laptop. my network manager is also disabled. ifconfig shows only the loopback interface(lo) and iwconfig shows output similar to the original poster's. I think it happened after I told it to hibernate and I think it disabled network management then. or maybe it's one of the updates. can anyone help me to get network manager working again? if i want to use wicd then is just compiling and installing wicd okay or should i disable/enable something first?

---

### Post by Iowan on 2010-06-15
Moved to new thread from [here]("http://ubuntuforums.org/showthread.php?t=1490833")
Appending to [SOLVED] thread may not be the best way to get help. ;)

[Here]("http://ubuntuforums.org/showthread.php?t=1505217") is a thread that mentions:```
 service network-manager stop
 rm /var/lib/NetworkManager/NetworkManager.state
 service network-manager start
```

---

### Post by sandy8925 on 2010-06-17
ok thanks. will try that.

---

### Post by sandy8925 on 2010-06-18
it worked. internet's back :)

---

