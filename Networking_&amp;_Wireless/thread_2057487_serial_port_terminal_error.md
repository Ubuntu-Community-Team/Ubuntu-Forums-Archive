---
title: "serial port terminal error"
date: 2012-09-13
forum: Networking &amp; Wireless
---

### Post by Abo El Nile on 2012-09-13
Hi ;

i am using serial port terminal on ubuntu 12.4 LTS 
and it give this error 
" Cannot open /dev/ttyS0: Permission denied "
hope that any one can help me to solve this error

Thanks ;

---

### Post by jonobr on 2012-09-13
Hello

Check permissions

```
/dev/ttyS0
```

Post back or research what ownerships and permissions should be

Cheers

---

### Post by Lars Noodén on 2012-09-14
The devices ttyS* belong to the group, 'dialout'  You might not be a member of the group 'dialout'

```

groups aboelnile

```

If not you need to add yourself to the group.  

```

sudo gpasswd --add aboelnile dialout

```

Then log out and log back in again for the changes to take effect.

---

### Post by Abo El Nile on 2012-09-14
> **jonobr said:**
> Hello

Check permissions

```
/dev/ttyS0
```Post back or research what ownerships and permissions should be

Cheers

the result is

amrsoliman@pc12:~$ /dev/ttyS0
bash: /dev/ttyS0: Permission denied
amrsoliman@pc12:~$

Thanks;

---

### Post by Lars Noodén on 2012-09-14
Try showing the permissions.

```

ls -l /dev/ttyS0

```

Also, what about group membership of your account as mentioned in #3 above?

---

### Post by Abo El Nile on 2012-09-14
> **Lars Noodén said:**
> The devices ttyS* belong to the group, 'dialout'  You might not be a member of the group 'dialout'

```

groups aboelnile

```If not you need to add yourself to the group.  

```

sudo gpasswd --add aboelnile dialout

```Then log out and log back in again for the changes to take effect.

i try it and the error disappeared 
when i open the serial port terminal not show this massage again 
i will try it on a device

thanks;

---

### Post by Abo El Nile on 2012-09-14
> **Lars Noodén said:**
> Try showing the permissions.

```

ls -l /dev/ttyS0

```Also, what about group membership of your account as mentioned in #3 above?

the result is 

amrsoliman@pc12:~$ ls -l /dev/ttyS0
crw-rw---- 1 root dialout 4, 64 Sep 14 11:36 /dev/ttyS0
amrsoliman@pc12:~$ 

Thanks;

---

### Post by jonobr on 2012-09-14
Apologies on that,
I dropped the ls -l

Lars Noodén , that for the correction

jonobr

---

### Post by Abo El Nile on 2012-09-15
Thanks it works good on the device :)
Thanks all for  your help :)

---

