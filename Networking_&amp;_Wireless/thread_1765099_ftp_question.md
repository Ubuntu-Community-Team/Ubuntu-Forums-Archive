---
title: "ftp question"
date: 2011-05-22
forum: Networking &amp; Wireless
---

### Post by flyingsliverfin on 2011-05-22
How come when I use firefox to go to [ftp://gimp.org](ftp://gimp.org) i don't need a password, but when i try to use terminal ftp and type "ftp gimp.org" I'm prompted for "Name (gimp.org:joshua): "? What would I put there?

---

### Post by flyingsliverfin on 2011-05-22
nevermind, i tried to use wget to get the file and it automatically logged in as anonymous. I tried that for username/pass and it worked :)

---

### Post by matt_symes on 2011-05-22
Hi

> **flyingsliverfin said:**
> How come when I use firefox to go to [ftp://gimp.org](ftp://gimp.org) i don't need a password, but when i try to use terminal ftp and type "ftp gimp.org" I'm prompted for "Name (gimp.org:joshua): "? What would I put there?

It's an anonymous ftp server.

When prompted type

```
anonymous
```And the for the password (Uppercase)

```
PASS
```Like this.....

```
matthew@matthew-laptop:~$ ftp gimp.org
Connected to gimp.org.
220 Welcome to ftp.gtk.org.
Name (gimp.org:matthew): anonymous
331 Please specify the password.
Password:
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> 

```Kind regards

---

