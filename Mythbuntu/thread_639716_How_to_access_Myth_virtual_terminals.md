---
title: "How to access Myth virtual terminals?"
date: 2007-12-13
forum: Mythbuntu
---

### Post by NickGray on 2007-12-13
I am using Ubuntu 7.10 and MythTV 0.20.2. This machine is my primary frontend, and my primary backend.

When I press **ALT+CTRL+F1**, it takes me to shell and promps for a login. If I press **ALT+F8**, I see things in a terminal window like...

[FONT="Courier New"]* LIRC is not configured.
* Running local boot scripts....
[/FONT]
Is there more than **ALT+CTRL+F8**? Is there a virtual terminal for mythfrontend and a separate one for mythbackend?
I would like to watch what the system is working on, so that if something freezes or runs slowly, I can attempt to search for fixes.

---

### Post by superm1 on 2007-12-13
> **NickGray said:**
> I am using Ubuntu 7.10 and MythTV 0.20.2. This machine is my primary frontend, and my primary backend.

When I press **ALT+CTRL+F1**, it takes me to shell and promps for a login. If I press **ALT+F8**, I see things in a terminal window like...

[FONT=Courier New]* LIRC is not configured.
* Running local boot scripts....
[/FONT]
Is there more than **ALT+CTRL+F8**? Is there a virtual terminal for mythfrontend and a separate one for mythbackend?
I would like to watch what the system is working on, so that if something freezes or runs slowly, I can attempt to search for fixes.
Just like any linux distro, ctrl-alt-f1 through f6 will be virtual terminals.  ctrl-alt-f7 will be X,ctrl-alt-f8 is your system log.

You are better off ssh'ing into your box however.

---

