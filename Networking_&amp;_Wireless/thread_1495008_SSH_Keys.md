---
title: "SSH Keys"
date: 2010-05-27
forum: Networking &amp; Wireless
---

### Post by Whisp3r on 2010-05-27
I'm having a problem generating keys for my SSH server.

I make my certificate using ssh-keygen -t rsa -b 1024. It generates the two files and puts them into my /home/user/.ssh/ file. I can ssh-copy-id username@host, and if I check the ssh folder on the host, it has generated an authorized_keys file. A look into the file shows that the RSA key was copied over correctly. 

When I attempt to ssh to my server, I get the following error:

```
Agent admitted failure to sign using the key.
```

It then asks me for my password to log into the host. What am I doing wrong?

---

