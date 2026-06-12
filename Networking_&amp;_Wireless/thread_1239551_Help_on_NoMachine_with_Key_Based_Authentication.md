---
title: "Help on NoMachine with Key Based Authentication"
date: 2009-08-13
forum: Networking &amp; Wireless
---

### Post by Johnny.Fan on 2009-08-13
Hi All,

First of all, this is my first post, so plz enlighten me if there's anything I missed in the post. Thanks in advance.

Alight, back to business. I am posting for help on NoMachine config to enable using NoMachine with Key Based Authentication. Basically, the situation here is that PasswordAuthentication is disabled for the server's SSH. Before I changed that config, NoMachine works fine.

Additional info I can provide is that the nx user authentication is successful as I can see from the progress. The error message from NoMachine client is "Authentication failed for user xxxxx", where the xxxxx is the actual user I tried to login with. I also tried the user check option from nxserver, and fixed some error as I can spot. Right now, its output is as below:

```
#./nxserver --usercheck xxxxx
NX> 900 Verifying public key authentication for NX user: xxxxx.
NX> 900 Public key authentication succeeded.
NX> 999 Bye.
```

So far, I am out of idea and cannot find any other useful help. NoMachine's KB did not help resolving this issue neither. Would appreciate if someone more experienced here could help.

Many thanks with warm regards.

---

### Post by Johnny.Fan on 2009-08-13
Did I post to wrong section? Also, am I in an unique situation that no one else has met?

---

### Post by serpentine on 2009-08-13
> **Johnny.Fan said:**
> Hi All,

First of all, this is my first post, so plz enlighten me if there's anything I missed in the post. Thanks in advance.

Alight, back to business. I am posting for help on NoMachine config to enable using NoMachine with Key Based Authentication. Basically, the situation here is that PasswordAuthentication is disabled for the server's SSH. Before I changed that config, NoMachine works fine.

Additional info I can provide is that the nx user authentication is successful as I can see from the progress. The error message from NoMachine client is "Authentication failed for user xxxxx", where the xxxxx is the actual user I tried to login with. I also tried the user check option from nxserver, and fixed some error as I can spot. Right now, its output is as below:

```
#./nxserver --usercheck xxxxx
NX> 900 Verifying public key authentication for NX user: xxxxx.
NX> 900 Public key authentication succeeded.
NX> 999 Bye.
```

So far, I am out of idea and cannot find any other useful help. NoMachine's KB did not help resolving this issue neither. Would appreciate if someone more experienced here could help.

Many thanks with warm regards.

Johnny.Fan,

While it is not currently possible for the NX Client to authenticate via DSA/RSA key or Kerberos, it is on the development roadmap.  The following feature requests may be of interest to you:

Allowing to choose the authentication method via the NX Client GUI
[http://www.nomachine.com/fr/view.php?id=FR02G02185](http://www.nomachine.com/fr/view.php?id=FR02G02185)

Removing the NX specific code from the nxssh component
[http://www.nomachine.com/fr/view.php?id=FR03G02203](http://www.nomachine.com/fr/view.php?id=FR03G02203)

In short, you must use password authentication at this point.

Thanks,

/JW

---

### Post by Johnny.Fan on 2009-08-14
Hi serpentine,

Thanks for reply. I guess I will have to stay with this and keep an eye on NoMachine update.

Thanks for the handy link, good to know.

---

