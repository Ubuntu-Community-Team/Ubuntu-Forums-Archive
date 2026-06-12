---
title: "Cannot run Samba"
date: 2013-05-24
forum: Networking &amp; Wireless
---

### Post by seruling on 2013-05-24
Running Ubuntu 13.04
I try to share a folder with to another laptop under local network, but never succeed.
After search google, I try to run "samba" from terminal, but receive this message:

[COLOR=#0000cd]samba: /usr/lib/i386-linux-gnu/libwbclient.so.0: no version information available (required by /usr/lib/i386-linux-gnu/samba/libauth4.so)[/COLOR]

When I check, the installed version for libwclient is version 2:3.6.9-1ubuntu1.
I don't know why they said that "no version information available" ?
How to solve this problem?

perhaps this is problem prevent me to share a folder?

---

### Post by prodigy_ on 2013-05-24
To set up Samba server:
```
sudo apt-get update
sudo apt-get install samba
```

To start Samba server:
```
sevice smbd start
```

More info:
[https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)
[http://www.samba.org/samba/docs/](http://www.samba.org/samba/docs/)

---

