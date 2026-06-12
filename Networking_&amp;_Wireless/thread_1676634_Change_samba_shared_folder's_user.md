---
title: "Change samba shared folder's user"
date: 2011-01-27
forum: Networking &amp; Wireless
---

### Post by E.Fil on 2011-01-27
Hi,

I installed samba just as described in
[https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html)

Now I want the shared folders (and the files created in them) to be owned by a user named efil. How do I do this?

Thanks
E.Fil

---

### Post by gordintoronto on 2011-01-27
The command:
chown
is for changing owners. The command:
man chown
will tell you how to use it.

---

### Post by Morbius1 on 2011-01-27
That's an interesting HowTo. For the benefit of others it creates a share:> [share]
    comment = Ubuntu File Server Share
    path = /srv/samba/share
    browsable = yes
    guest ok = yes
    read only = no
    create mask = 0755Then it changes ownership of the target directory to nobody:
> sudo chown nobody.nogroup /srv/samba/share/The howto never issues a chmod 777 so the only way it works now is  because the remote unauthenticated user ( nobody ) and the folder  ownership ( nobody ) match. If you just change ownership ( chown ) you  will be denied write access.

I have a question for you. Who is this efil person and why do you want to do this.

Do you want efil to be the only person who can access the share?
Or is this really a server with a small "s" ( meaning your own desktop ) and your username is efil?

If it's the later then I would suggest you do the following:
```
 sudo chmod 0777 /srv/samba/share
```Then change the share definition to this:
> [share]
    comment = Ubuntu File Server Share
    path = /srv/samba/share
    browsable = yes
    guest ok = yes
    read only = no
    force user = efilThe chmod 777 will allow unauthenticated lan users to access the share.
The "force user" will convert the unauthenticated lan user "nobody" to efil so that efil can access the shares from the server locally.

---

### Post by E.Fil on 2011-01-28
Hi,

Morbius1, that was exactly what I needed. I have a small server and the only user was named efil.

Perfect answer

Thanks :)

---

