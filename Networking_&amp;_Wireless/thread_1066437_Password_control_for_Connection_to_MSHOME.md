---
title: "Password control for Connection to MSHOME"
date: 2009-02-10
forum: Networking &amp; Wireless
---

### Post by lmbevard on 2009-02-10
I finally got my Netbook with Ubuntu 8.10 installed to connect to my network under MSHOME. I can move files from my XP desktop but to run from drives on the desktop, Ubuntu ask me for a password. My accts. on the XP have no password but Ubuntu will not accept a blank. Will I have to put a password on one of my accts on the desktop or is Linux asking for something else?

---

### Post by cariboo on 2009-02-10
On your Ubuntu computer, open an Applications-->Accessories-->Terminal and at the prompt type:

```
sudo smbpasswd -L -a <username>
```

the above command will ask you to enter your password, I usually use my ubuntu user password.

And to enable the user:

```
sudo smbpasswd -L -e <username>
```

Jim

---

