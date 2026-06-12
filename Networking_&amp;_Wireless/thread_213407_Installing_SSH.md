---
title: "Installing SSH"
date: 2006-07-11
forum: Networking &amp; Wireless
---

### Post by zugu on 2006-07-11
How do I install SSH? Is it installed by default? How do I start the SSH server? How do I make it to start everytime Ubuntu boots?

Thank you.

---

### Post by MonkeyNet on 2006-07-11
> **zugu said:**
> How do I install SSH? Is it installed by default? How do I start the SSH server? How do I make it to start everytime Ubuntu boots?

Thank you.

Hi zugu,

You can install ssh with the following

```
sudo apt-get install openssh-server
```

It will generate the relevant keys for the machine and will automatically be loaded at startup

Cheers,

Andrew

---

### Post by zugu on 2006-07-11
Very helpful, thanks.

---

