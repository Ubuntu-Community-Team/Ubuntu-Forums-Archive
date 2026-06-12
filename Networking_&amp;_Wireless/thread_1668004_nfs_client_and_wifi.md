---
title: "nfs client and wifi"
date: 2011-01-15
forum: Networking &amp; Wireless
---

### Post by untamed on 2011-01-15
I'm having a problem with NFS connection to a server via wireless lan.
In my ubuntu (lucid) box I configured /etc/fstab to connect automatically at boot to a nas that is running nfs service.
If I'm using cable lan, my box is connecting successfully. However if I'm using wireless lan, nfs share is not connected after machine boot.
In /var/log /messages I see:

```
rpcbind: server terminus not responding, timed out
```

I can't figure out what is not working........ 

:???:

---

### Post by untamed on 2011-01-16
up!

---

### Post by apollothethird on 2011-01-16
> **untamed said:**
> I'm having a problem with NFS connection to a server via wireless lan.
In my ubuntu (lucid) box I configured /etc/fstab to connect automatically at boot to a nas that is running nfs service.
If I'm using cable lan, my box is connecting successfully. However if I'm using wireless lan, nfs share is not connected after machine boot.
In /var/log /messages I see:

```
rpcbind: server terminus not responding, timed out
```

I can't figure out what is not working........ 

:???:

That's probably because the wireless connection hasn't completely become established at the time of the fstab process.

You might best put a script in the rc.local to connect to your nfs client.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by untamed on 2011-01-16
Isn't there a way to make wifi connection established at the time it tries to connec to NFS server?

---

### Post by apollothethird on 2011-01-16
> **untamed said:**
> Isn't there a way to make wifi connection established at the time it tries to connec to NFS server?

Personally I would think that might be a tall order when you consider what an early process the fstab loading happens to be.  Even if you were to get that level configured, there would still be times when it'll miss because even the best wifi signals are not perfect.

You'd probably have to perform the mount operation again once the system is fully up.  I believe putting line in the rc.local should resolve the latter concern also.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by untamed on 2011-01-16
Thanks, I'll try with rc.local.

---

### Post by josir on 2011-08-16
Hi untamed, 

did you find a solution for the nfs mount with wifi connection ?

Thanks in advance,
Josir

---

