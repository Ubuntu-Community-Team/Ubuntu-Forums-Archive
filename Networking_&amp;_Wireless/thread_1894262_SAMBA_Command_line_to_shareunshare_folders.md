---
title: "SAMBA: Command line to share/unshare folders ?"
date: 2011-12-12
forum: Networking &amp; Wireless
---

### Post by Jethro_uk on 2011-12-12
Hi all, is it possible to run a command line to share a folder in Samba, in a similar way to the NET SHARE command in Windows ?

I know Samba uses a conf file to outline shared dirs ... is that the only way to add/remove a share ? If so, are there any scripts that can be used to achieve a single command-line control ?

---

### Post by Morbius1 on 2011-12-12
There's 2 ways to create a samba share:

* Classic-share uses smb.conf and it's shares are defined there. I don't know if there is a way to create a share from a terminal for these shares.

* Usershares also uses smb.conf but it's shares are defined in /var/lib/samba/usershares. These can be created from a terminal although the syntax is very awkward:

Let's say I wanted to create a guest writeable share of my Documents folder:
```
net usershare add documents /home/morbius/Documents "morbius documents" everyone:F guest_ok=y
```To make it Read Only change "everyone:F" to "everyone:R"
To make it a private share vs a Public share change "guest_ok=y" to "guest_ok=n"

Usershares don't have the flexibility and configurability of a classic share but depending on your needs it might be enough.

The command to delete the Usershare I created above:
```
net usershare delete documents
```And the command to get a list of how all your usershares are configured:
```
net usershare info --long
```

---

### Post by Jethro_uk on 2011-12-12
Thanks Morbius1 - that works a treat ! Exactly what I wanted ... now I can easily switch a share on/off from a SSH login, rather than using Webmin, or having to access the GUI to use SMBConf ..

(can you tell I'm a windows user !)

Weird using almost the same command in Linux as Windows ...

---

