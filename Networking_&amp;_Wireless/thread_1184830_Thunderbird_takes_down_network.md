---
title: "Thunderbird takes down network"
date: 2009-06-11
forum: Networking &amp; Wireless
---

### Post by Celauran on 2009-06-11
I've got all my mail files stored on a server so that I can access my email from whichever machine I happen to be working on, either via NFS or Samba. This has been working beautifully for months.

This morning I received an email, opened it in Thunderbird on a Windows XP desktop, and doing so killed the server's network connection. I was ssh'd into the server from another machine, and the ssh session die, so it wasn't specific to Samba nor to the Windows machine the email was read on.

It seemed strange enough that it must be coincidence, except that I've been reproducing the same problem for four hours now. It's only this one email -- and it's just a regular old HTML email -- and always this one email.

Not even sure where to start on this one, so any pointers are much appreciated.

---

### Post by doas777 on 2009-06-11
delete that message seems to be the easiest way to deal with it. it may contain malware, or jsut be horribly malformed to the extent that it just breaks everything.

also keep in mind, there is a class of exploits used in spear fishing attacks against server/network techs, which look for remote administrative connections to routers and servers and uses that link to affect the server/router. they are very rare because to work correctly the administrative link needs to be established before the malware runs to be sucessful. this is not likely your issue, unless the email is from blackhat friend that is playing with you.

---

### Post by dmizer on 2009-06-11
How do you have your samba share configured?

Did you check the ouput of dmesg to see if there were any system errors?

---

### Post by Celauran on 2009-06-12
> **dmizer said:**
> How do you have your samba share configured?

```
[sharename]
    comment = Blah blah
    path = /var/foo
    browseable = yes
    read only = no
    valid users = @group
    directory mask = 1770
    create mask = 0660

```

> **dmizer said:**
> Did you check the ouput of dmesg to see if there were any system errors?
dmesg looked fine.

---

