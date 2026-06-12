---
title: "why sometimes need to use ip to connect to shared windows folder"
date: 2009-01-28
forum: Networking &amp; Wireless
---

### Post by ubantuwannabe on 2009-01-28
Hi,

Places->Network

type

**smb://forevershare/**

initially I was not able to view the files and folders.

but after I type smb://192.168.abc.cde/

it display list of files and folders

after that I type smb://forevershare,

it display list of files and folders again.

before that I was able to access the shared windows folder from another ubuntu desktop at the same time using only shared name.

It is able to display the folders and files.

thanks

---

### Post by cariboo on 2009-01-28
Do you have forevershare aliased to 192.168.abc.def (why not put the full ip address, it isn't routable) in your /etc/hosts file eg:

```
127.0.0.1          localhost
127.0.1.1          <yourcomputername>
192.168.abc.def    forevershare
```

Jim

---

