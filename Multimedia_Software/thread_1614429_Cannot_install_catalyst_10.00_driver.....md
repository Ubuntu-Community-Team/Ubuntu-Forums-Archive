---
title: "Cannot install catalyst 10.00 driver...."
date: 2010-11-05
forum: Multimedia Software
---

### Post by alexpennos on 2010-11-05
Let me describe the problem:
I have already downloaded and installed ati's catalyst for my ati mobility radeon 4570 (at least i think so, since there is the ATI catalyst control center in the system-> preferences menu).
The problem is that i want to upgrade its version from 10.9 to 10.10. and since i want to firstly uninstall the previous version,I get this:
```
alexandros@alexandros-laptop:/usr/share/ati$ sh ./fglrx-uninstall.sh
sh: Can't open ./fglrx-uninstall.sh

``` 

The uninstall.sh doesn't exist!!! (at least there.... :confused: )
Any suggestions!???

---

### Post by bsmith1051 on 2010-11-05
is the 'fglrx-uninstall.sh' file actually in that folder?  if you run 'ls' can you see it there?  and, is it marked executable?

---

### Post by alexpennos on 2010-11-06
> **bsmith1051 said:**
> is the 'fglrx-uninstall.sh' file actually in that folder?  if you run 'ls' can you see it there?  and, is it marked executable?
No, and that is the problem...it isn't there....:(

---

### Post by alexpennos on 2010-11-06
To make it more clear...
[IMG]http://img826.imageshack.us/img826/7158/catalystcontrolcenter05.png[/IMG]

[IMG]http://img233.imageshack.us/img233/2237/ati059.png[/IMG]

[IMG]http://img233.imageshack.us/img233/2765/amdcccle061.png[/IMG]
:confused:

---

### Post by Yellow Pasque on 2010-11-06
IIRC, if you installed by building packages, then the uninstall file will not exist. To uninstall, just remove/purge the packages you built/installed.

---

### Post by alexpennos on 2010-11-06
> **Temüjin said:**
> IIRC, if you installed by building packages, then the uninstall file will not exist. To uninstall, just remove/purge the packages you built/installed.

thank you foa the answer but, how can i do it? (not an experirnced user here...)


p.s. : what is IIRC? :)

---

### Post by alexpennos on 2010-11-06
Well...did it...I removed the proprietary drivers from System->Admin -> additional drivers, and i run the (driver install).sh manualy. Everything looks fine.
Thank you for the replies.

---

