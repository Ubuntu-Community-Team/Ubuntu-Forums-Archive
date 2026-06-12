---
title: "Kerberos Problem"
date: 2010-04-14
forum: Networking &amp; Wireless
---

### Post by 10125 on 2010-04-14
Hi-

So I was trying to configure my CUPS server and checked the box marked "Use Kerberos Authentication." Now, I cannot change anything and get an unauthorized error every time I try. How can I remove Kerberos? I have access to the local computer as root and can use sudo. 

Thanks

---

### Post by romeroc24 on 2010-04-14
Man look at:
```

$sudo vim /etc/cups/cupsd.conf

```
and try to find some like "Kerberos Authentication" and delete it.

---

### Post by slapt0p on 2010-04-17
I did the same thing exactly.  now I can't undo it.  How can CUPs be unhooked from kerboros?

There's nothing in cupsd.conf

thanks in advance

---

### Post by gokhankelle on 2012-02-24
Hello,
i have just bumped into that problem by accidentally switching the check box `Kerberos Auth.` in the cups web interface http//:localhost:631,

after that, to alter the behavior manually, i tried to look into /etc/cups/cupsd.conf file for the word `Kerberos` but no related words in there, 

The documentation of cupsd.conf says that `Kerberos Authentication` is denoted with `Negotiate` keyword and making cups to use local groups and user passwds is denoted with `Basic`, so i changed the 
defalt authentication to `Basic`, changing the line below;

...
DefaultAuthType Negotiate # old one,
...

...
DefaultAuthType Basic # new one,
...

The rest of the regions requiring authentication in cupsd.conf file uses Default authentication method, so changing the default method yields changing all of them, i.e.,

...
<Location /admin/conf>
AuthType Default 
...

After that i killed the cups daemon and performed a re-start, 

# sudo cupsd
 
Now it worked for me and i can use username: root and pass: <my-root-passwd> to administrate the server.  

Regards,

gokhankelle.

---

