---
title: "Samba"
date: 2010-12-22
forum: Networking &amp; Wireless
---

### Post by Colo2 on 2010-12-22
Hello
I have an issue.

My Linux machine's samba is working, I think. I am able to browse my own samba shared folders via "Network" on my linux PC, however my 3 windows machines can't browse the linux pc's folder. It sees it on the network, but it won't go in, gives an error.

Any ideas as to whats wrong?

Thanks

Tom.

---

### Post by CharlesA on 2010-12-22
See if you can connect to the ip address of the linux server from a Windows box.

---

### Post by Colo2 on 2010-12-22
> **CharlesA said:**
> See if you can connect to the ip address of the linux server from a Windows box.


Affirmative, VNC works from a my windows PCs

---

### Post by CharlesA on 2010-12-22
Ok, you need to have some sort of name resolution, since NetBIOS broadcasts don't work with Linux.

You can either set up a simple DNS server using something like DNSMasq, or just add the server's IP into the hosts file on the Windows machines that can't find it.

---

### Post by Colo2 on 2010-12-22
> **CharlesA said:**
> Ok, you need to have some soft of name resolution, since NetBIOS broadcasts don't work with Linux.

You can either set up a simple DNS server using something like DNSMasq, or just add the server's IP into the hosts file on the Windows machines that can't find it.

hmm... but, this was working fine until not long ago, it just happend when the hard drive was unplugged for a lenge of time

---

### Post by CharlesA on 2010-12-22
In that case, make sure that nmbd is running:

```
service nmbd status
```

---

### Post by Colo2 on 2010-12-22
There's no problem normally, under a fresh install etc, samba works as normal. But  put another hdd in the machine to install windows for a while decided that I hate windows, and have now gone back to my linux drive. Since then, I have this problem

---

### Post by Colo2 on 2010-12-22
> **CharlesA said:**
> In that case, make sure that nmbd is running:

```
service nmbd status
```

Ah, thanks, let me try that

---

### Post by Colo2 on 2010-12-22
hmm 
> dump@STORAGE-DUMP:~$ service nmdb status
nmdb: unrecognized service
dump@STORAGE-DUMP:~$

---

### Post by CharlesA on 2010-12-22
It's nmbd. There's a typo in there. :)

---

### Post by Colo2 on 2010-12-22
Ah sorry man :P see what lack of sleep does to you? :D

---

### Post by Colo2 on 2010-12-22
hmm...

> dump@STORAGE-DUMP:~$ service nmbd status
nmbd start/running, process 1462
dump@STORAGE-DUMP:~$ 

---

### Post by CharlesA on 2010-12-22
Hmm it's running.

Do you have any firewall rules in place?

---

### Post by Colo2 on 2010-12-22
Okay! 

I fixed it. 

I did
> sudo service nmbd restart

and it works now

Thanks so much for your help :) as always, it's extremely appreciated.

No more Windows for me :)

---

### Post by CharlesA on 2010-12-22
Glad you got it working. :)

Don't forget to mark the thread as solved from thread tools.

---

