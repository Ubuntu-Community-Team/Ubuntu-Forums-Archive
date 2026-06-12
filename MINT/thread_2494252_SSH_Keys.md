---
title: "SSH Keys"
date: 2024-01-10
forum: MINT
---

### Post by fractalcatuk on 2024-01-10
Hello,

I hope this is the correct forum for my issue.  Apologies if it isn't.

I can access my remote Ubuntu server using ssh on Windows 10, but I also have a Linux laptop running Linux Mint.  How can I accurately set the key on my Linux Mint desktop to the one
on my Windows 10 desktop so I can login using my Linux laptop ?

Thanks

FC

---

### Post by howefield on 2024-01-10
Thread moved to the "*MINT*" forum.

---

### Post by The Cog on 2024-01-10
You don't do that. The key on your desktop should remain on your desktop and nowhere else. You should generate a new key pair (public and private) on the laptop and transfer the laptop's public key to the server, appending it to the appropriate user account's .ssh/authorized_keys file. ssh-copy-id will be able to do the transfer (provided that password based logins are still permitted: if not then give your public key to a server admin who can put it in the right place).
This looks like a good tutorial: [https://www.tecmint.com/ssh-passwordless-login-using-ssh-keygen-in-5-easy-steps/](https://www.tecmint.com/ssh-passwordless-login-using-ssh-keygen-in-5-easy-steps/)

---

### Post by TheFu on 2024-01-10
> **fractalcatuk said:**
> I can access my remote Ubuntu server using ssh on Windows 10, but I also have a Linux laptop running Linux Mint.  How can I accurately set the key on my Linux Mint desktop to the one
on my Windows 10 desktop so I can login using my Linux laptop ?


There is a client key (private) and a server key (public).  Each client will generate a private/public key pair.  **ssh-keygen** is the tool for this on all platforms.

Then from the client, the public key is placed into the ~/.ssh/authorized_keys file.  From MS-Windows, this is a manual process.  On any Unix-based system, there's a tool called **ssh-copy-id** which will copy the public key to the server and append it to the authorized_keys file.  Additionally, ssh-copy-id also will ensure file permissions are correct and create the ~/.ssh/ directory if it doesn't exist on the remote system.

ssh is really picky, for security reasons, about directory and file permissions on these sensitive files.  Best to always use  **ssh-copy-id** and then you'll never have the issue.

In summary, 
Setting up keys is only 2 steps these days.

Step 1:  Run on the client as the normal user:
```
   $ ssh-keygen -t ed25519
```

Step 2:  Run from the client to the server:
```
   $ ssh-copy-id -i ~/.ssh/id_ed25519.pub username@remote
```
 The "username" is optional and not needed if the same between the client machine and remote server.
 "remote" can be a DNS name, IP address, some manually setup lookup inside the /etc/hosts or configured in the ~/.ssh/config file.

Best to avoid RSA keys these days. ed25519 is standard and well supported across all platforms. On some, it is even preferred over using 4Kb RSA keys.

Probably more detail than you need.

---

