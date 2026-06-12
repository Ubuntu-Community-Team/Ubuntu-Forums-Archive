---
title: "Sudo: unable to resolve host JamesServer"
date: 2013-08-23
forum: Networking &amp; Wireless
---

### Post by Jim01 on 2013-08-23
Hey guys,

I'm having the above title error come up with Ubuntu Server 12.04

After researching the issue I'm still a bit lost as to how I solve the issue, so any help will be greatly appreciated.

**_Note to moderators:_** Please feel free to move the topic to a different forum area if there's a more appropriate place for the discussion.

Cheer's guys :)

James

---

### Post by steeldriver on 2013-08-23
Did you modify either the /etc/hosts or /etc/hostname files?

---

### Post by Jim01 on 2013-08-23
Yes I changed the /etc/hostname file to "JamesServer", I can't remember what it originally was though.

---

### Post by CatKiller on 2013-08-24
It was originally what it says in /etc/hosts; the hostname needs to match in both files, and it's not as easy as it used to be to change both of them at once.

Boot in recovery mode, or from a live cd, and edit one or the other to match.

---

### Post by Jim01 on 2013-08-24
> **CatKiller said:**
> It was originally what it says in /etc/hosts; the hostname needs to match in both files, and it's not as easy as it used to be to change both of them at once.

Boot in recovery mode, or from a live cd, and edit one or the other to match.

I'm a bit confused as to what I'm supposed to be changing, I have supplied screenshots within the "vim" editor of what I have in /etc/hosts and /etc/hostname.

[ATTACH=CONFIG]245663[/ATTACH]

[ATTACH=CONFIG]245662[/ATTACH]

What is it I'm supposed to be changing in the hosts file to suit the new hostname?

Cheer's guys! :)

---

### Post by Cheesemill on 2013-08-24
Change ubuntuserver in /etc/hosts to JamesServer so that the names match in both files.

---

### Post by Jim01 on 2013-08-24
That did the trick!  Thanks for the help everyone! :D

---

