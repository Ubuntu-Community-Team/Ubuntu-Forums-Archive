---
title: "Can only connect to ubuntu server via SSH when logged in"
date: 2009-10-04
forum: Networking &amp; Wireless
---

### Post by roelipot on 2009-10-04
I got ubuntu server 9.04 installed on a headless machine and can successfully establish an ssh connection between my macbook and the server when I'm logged in on the server. I'm using private-, publickey to establish the connection and no passphrase and no passwords.

Although when I reboot the server and do not log in first (I don't want to because everytime i've to connect keyboard and monitor), I can't connect via SSH. It gives me the following reason:

[I]Ubuntu 9.04
Permission denied (publickey).[/I]

Anyone an idea? If you need more information please ask.

P.S. Funny thing is that when I first connect my macbook via an afp-connection to the server, it is possible to ssh into the server without logging in first.

---

### Post by VipX1 on 2009-11-15
I had the same problem recently. It used to work for me, I could reboot the server and get in again only using my public key. I had to re-enable password authentication as a solution to the problem for now until I find why it happens. If I have an up-date I'll post it.

---

### Post by falconindy on 2009-11-15
Eek, double post.

---

### Post by falconindy on 2009-11-15
You'll need to specify a "universal" authorized_keys file in /etc/ssh/sshd_config with the AuthorizedKeysFile option. Without specifying this, the keyfile is '$HOME/.ssh/authorized_keys' -- something that won't work too well without a user logged in.

---

### Post by U2XS on 2009-11-15
> **roelipot said:**
> ...because everytime i've to connect keyboard and monitor...
This is the most interesting part for me.  I have two computers at work which will not load the OS if the keyboard and mouse are not plugged in.  It will just stay in the BIOS.  Have you ever tried disconnecting the keyboard/mouse but leaving a monitor plugged in to the PC?  You might be experiencing the same thing.  Clearly, you wouldn't be able to SSh into the BIOS.

---

### Post by falconindy on 2009-11-15
> **U2XS said:**
> This is the most interesting part for me.  I have two computers at work which will not load the OS if the keyboard and mouse are not plugged in.  It will just stay in the BIOS.  Have you ever tried disconnecting the keyboard/mouse but leaving a monitor plugged in to the PC?  You might be experiencing the same thing.  Clearly, you wouldn't be able to SSh into the BIOS.
If the server was stuck at the POST because of an error, he wouldn't be able to bounce off the IP, let alone get a permission denied response.

---

### Post by VipX1 on 2009-11-15
I can get into my server via ssh but I 've noticed my /home/user directory is encrypted. When I try to restart ssh it tells me the "/home/user/Authorize_keys Line 27" is causing an error. This is because the /home/user directory is encrypted so the keys can't be read or found. I don't know why my /home directory is encrypted but I would say yours roelipot is encrypted too. The following command is supposed to un-encrypt the /home directory but it asks for a passphrase which I don't know.```
sudo ecryptfs-mount-private
```I take it you can't get into your server to check. Did you choose to encrypt your /home directory when you installed the OS originally.. The /home directory doesn't un-encrypt until you log-in physically to the server, ssh doesn't count! I think this is what I did..
You could change the location of the auth_keys file to an always un-encrypted directory to solve the problem..

---

