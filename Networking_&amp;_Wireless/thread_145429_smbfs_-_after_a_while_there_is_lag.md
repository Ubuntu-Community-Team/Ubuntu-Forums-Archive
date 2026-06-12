---
title: "smbfs - after a while there is lag"
date: 2006-03-16
forum: Networking &amp; Wireless
---

### Post by ubuntumaneh on 2006-03-16
Hello,

   Im connecting my Ubuntu box with a XP computer through smb. I use a directory there only to save some data. But this is not being smooth. The problem:

I use the command:
```
 
smbmount //XPcomputer/SharedDir ~/win/ -o uid=my_name,rw,guest,sockopt="SO_KEEPALIVE IPTOS_LOWDELAY 
TCP_NODELAY"

```

or i can just issue a mount, for I have in fstab:
//computador/SharedDocs  /media/Win_Share  smbfs  rw,guest,uid=my_name,sockopt
=SO_KEEPALIVE 0  0


Everything works ok in each of the above procedures. But after a while, maybe 5 minutes, it starts to take a long time to see the directory. For instance, if I want to enter the directory with:
cd ~/win/

It will take a long time to happen. And any other action in the directory will take a time. Even in my home, if I want to issue a plain ls, it will take a while.

I have been googling, and could not find much. I have tweaked a little with sockopt, but without luck. My last attempt was to insert in smb.comf the following:
 socket options = "TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192"

The lag remains.

Has someone an idea, suggestions, a link?

Thanks in advance

---

