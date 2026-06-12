---
title: "SSH key does not work"
date: 2010-05-27
forum: Networking &amp; Wireless
---

### Post by WA1DH on 2010-05-27
I've been trying to set up an SSH key on my server and laptop. I generate the key on the laptop, copy the id_rsa.pub file over into '/home/server/.ssh/authorized_keys', and try restarting the SSH server on the remote machine (server). Every time I try to ssh into the server from the laptop, I get a password prompt.

When I created the key, I left the password blank. It is asking me for PASSWORD, not PASSPHRASE when I try to login. So, I would assume the key is not working/being recognized at all.

I have tried changing the permissions of the ssh folder and authorized_keys file on the server per various posts I have found on the web. Nothing works.

Any ideas?

---

### Post by wojox on 2010-05-27
You followed this exactly? [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

---

### Post by WA1DH on 2010-05-27
> **wojox said:**
> You followed this exactly? [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

Thanks.. that tutorial didn't help, but another one did (here: [http://jimmyg.org/blog/2008/beginners-guide-to-ssh-keys-with-ssh2.html](http://jimmyg.org/blog/2008/beginners-guide-to-ssh-keys-with-ssh2.html)). I had to rename the key files and restart the gnome session, then change them back, and it works now.

---

