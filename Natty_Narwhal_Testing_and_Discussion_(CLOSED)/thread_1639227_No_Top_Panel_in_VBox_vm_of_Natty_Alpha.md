---
title: "No Top Panel in VBox vm of Natty Alpha"
date: 2010-12-06
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by mikodo on 2010-12-06
Hi, 

I have the newest version of VirtualBox running in my desktop version of Lucid. I updated it today to the newest.  I forget the version.

I upgraded a vm from Lucid -> Karmic -> Natty Alpha by:

```
upgrade-manager -d
``` I was able to install the guest additions in the vm Natty Alpha.

I have no upper panel in the Natty vm (Applications Places, System etc). Never received one on upgrade.

I can open a terminal in the Natty vm using Ctrl-Alt-t. I tried in Terminal ```
sudo service gdm restart

```That crashed it; I closed and rebooted Natty and still no upper panel!

How can I get that Panel?

Thanks.

---

### Post by clhsharky on 2010-12-06
mikodo


I would try asking in,
Natty Narwhal Testing and Discussion
[http://ubuntuforums.org/forumdisplay.php?f=394](http://ubuntuforums.org/forumdisplay.php?f=394)


Sharky

---

### Post by mikodo on 2010-12-06
Hi, 

I have the newest version of VirtualBox running in my desktop version of  Lucid. I updated it today to the newest.  I forget the version.

I upgraded a vm from Lucid -> Karmic -> Natty Alpha by:
     
     ```
upgrade-manager -d 
``` I was able to install the guest additions in the vm Natty Alpha.

I have no upper panel in the Natty vm (Applications Places, System etc). Never received one on upgrade.

I can open a terminal in the Natty vm using Ctrl-Alt-t. I tried in Terminal:

     ```
sudo service gdm restart 
```That crashed it; I closed and rebooted Natty and still no upper panel!

How can I get that Panel?

Thanks.
                                                                                                                                    *                                              [Last edited by mikodo]("http://ubuntuforums.org/posthistory.php?p=10207706"); 1 Minute Ago at 04:21 PM..                                                                   Reason: New information.                                      *

---

### Post by mikodo on 2010-12-06
> **clhsharky said:**
> mikodo


I would try asking in,
Natty Narwhal Testing and Discussion
[http://ubuntuforums.org/forumdisplay.php?f=394](http://ubuntuforums.org/forumdisplay.php?f=394)


Sharky


Thanks, Sharky:

I reposted on that board.

mikodo

---

### Post by Joeb454 on 2010-12-06
*Thread moved to **Natty Narwhal Testing and Discussion**.*

Please use this thread: [http://ubuntuforums.org/showthread.php?t=1639285](http://ubuntuforums.org/showthread.php?t=1639285)

Apologies - you reposted as I moved this thread :) I have closed this thread

---

### Post by cariboo on 2010-12-06
Are you  using the Classic desktop, as Unity won't run in vbox. To start the panels, open a terminal, by pressing Ctrl-Alt-T, and typing:

```
gnome-panel &
```

you can then log out properly and switch to the Classic Desktop session.

---

### Post by mikodo on 2010-12-06
> **cariboo907 said:**
> Are you  using the Classic desktop, as Unity won't run in vbox. To start the panels, open a terminal, by pressing Ctrl-Alt-T, and typing:

```
gnome-panel &
```you can then log out properly and switch to the Classic Desktop session.

That did it.

Thanks cariboo907.

---

### Post by cariboo on 2010-12-06
Ooops, I merged the two threads, before I noticed joeb closed the other one.

---

### Post by jfernyhough on 2010-12-07
You guys are just *too* efficient. :D

---

