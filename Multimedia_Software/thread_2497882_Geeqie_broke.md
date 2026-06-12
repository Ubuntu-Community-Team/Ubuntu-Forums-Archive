---
title: "Geeqie broke"
date: 2024-05-21
forum: Multimedia Software
---

### Post by currentshaft on 2024-05-21
1

---

### Post by TheFu on 2024-05-21
Works fine here.

But there's a a huge absence of information about the system and program, so I have doubts that my 2 different OS versions (both LTS) map to whatever you have.

---

### Post by currentshaft on 2024-05-22
lo

---

### Post by TheFu on 2024-05-22
No 24.04 here. Sorry.  Maybe someone else can test.

Does the issue happen for every type of file or just 1 specific type or 1 specific file?
```
$ dpkg -l geeqie*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version         Architecture Description
+++-==============-===============-============-=================================
ii  geeqie         1:1.5.1-8build1 amd64        image viewer using GTK+
ii  geeqie-common  1:1.5.1-8build1 all          data files for Geeqie
un  geeqie-dbg     <none>          <none>       (no description available)
```

and on the other system
```
$ dpkg -l geeqie*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version         Architecture Description
+++-==============-===============-============-=================================
ii  geeqie         1:1.7.2-1build1 amd64        image viewer using GTK+
ii  geeqie-common  1:1.7.2-1build1 all          data files for Geeqie
```

Basic information that is **always** needed. Perhaps the exact kernel used would help too. IDK.

---

### Post by #&amp;thj^% on 2024-05-22
It works here on 24.04 and 24.10
```
dpkg -l geeqie*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  geeqie         1:2.4-2      amd64        image viewer using GTK+
ii  geeqie-common  1:2.4-2      all          data files for Geeqie

```

---

### Post by currentshaft on 2024-05-22
4

---

### Post by TheFu on 2024-05-23
Create a new userid. Login under it. Try Geeqie.  Does it work?  This will help determine if it is system-wide or just your personal settings.  If it works for the new account, which I expect it will, then clean up your Geeqie config/settings.  Normally, that means deleting them. I don't know where they are kept. If they are stuck inside  gconf/dconf crap, it might be easier to just create a new useraccount and migrate to it all your personal files ... except the gconf/dconf crap.  IDK.  I've never needed to do that.

If it doesn't work under the other user login, boot into a Try Ubuntu environment using a flash drive, install Geeqie into it and try again.  If that works and it doesn't work for both user accounts on the installed system, then the problem is within your installation.

Geeqie is the image viewer I've been using for a long time.  Every once in a while, I have had to clean up the generated preview cache, but I don't remember cleaning any settings.

---

