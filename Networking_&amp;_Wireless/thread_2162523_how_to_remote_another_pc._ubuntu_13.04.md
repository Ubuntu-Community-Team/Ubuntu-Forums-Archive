---
title: "how to remote another pc. ubuntu 13.04"
date: 2013-07-14
forum: Networking &amp; Wireless
---

### Post by jairoh_ on 2013-07-14
anyone can teach me how to remote another pc from ubuntu 13.04 terminal? tnx

---

### Post by Bashing-om on 2013-07-14
jairoh_; Hi !

That depends on what you want to do and on what the other operating system is.
It ranges from a simple terminal command for ubuntu 2 ubuntu file transfer to setting up samba file sharing for Windows sharing.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by jairoh_ on 2013-07-31
> **Bashing-om said:**
> jairoh_; Hi !

That depends on what you want to do and on what the other operating system is.
It ranges from a simple terminal command for ubuntu 2 ubuntu file transfer to setting up samba file sharing for Windows sharing.
[INDENT][INDENT]where there is a will there is a way
[/INDENT]
[/INDENT]

i tried install Remote Desktop Viewer but this error pops out
```

vinagre: Depends: libavahi-ui-gtk3-0 (>= 0.6.30) but it is not going to be installed
         Depends: libgtk-vnc-2.0-0 (>= 0.3.10) but it is not going to be installed
         Depends: libvte-2.90-9 (>= 1:0.27.2) but 1:0.34.2-0ubuntu2 is to be installed

```

---

### Post by Bashing-om on 2013-07-31
jairoh_; Well well well...
Let's see what the package manager has to advise.
terminal codes:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade ##dist-upgrade is also able to remove existing packages if required/and install held back packages,

```
Then if we have to, will tackle the dependencies one at a time.

[INDENT][INDENT]we be look'n
[/INDENT][/INDENT]

---

