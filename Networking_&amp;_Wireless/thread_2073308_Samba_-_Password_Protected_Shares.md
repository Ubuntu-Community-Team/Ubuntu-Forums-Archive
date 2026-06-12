---
title: "Samba - Password Protected Shares?"
date: 2012-10-19
forum: Networking &amp; Wireless
---

### Post by GaryRixon on 2012-10-19
Hello!

Running ubuntu server 12.04 fully updated/upgraded.

Been trying to set up a password-protected samba share that requests a user name and password EVERY TIME I try to connect to the share.

I currently have the default smb.conf file as I have done a complete re-install.

Can anyone give me a complete smb.conf file or any helpful information/links where I can read about samba security? I'd really like to further my knowledge in this area.

Many thanks in advance

Gary Rixon.

---

### Post by nclucid on 2012-10-19
Hello,

This is pretty basic samba stuff. You will need to use something like this:

```

[global]
    workgroup = WORKGROUP
    encrypt passwords = yes
    log level = 1
    max log size = 1000
    read only = no
    guest ok = no
[test]
    browsable = yes
    writeable = yes
    path = /srv/share

```

Keep in mind that this means anyone who is trying to authenticate will need a unix account blah blah blah. Read the documentation for more details.

[http://www.samba.org/samba/docs/using_samba/ch09.html](http://www.samba.org/samba/docs/using_samba/ch09.html)
[http://www.samba.org/samba/docs/using_samba/ch06.html](http://www.samba.org/samba/docs/using_samba/ch06.html)

Hope that helps

---

