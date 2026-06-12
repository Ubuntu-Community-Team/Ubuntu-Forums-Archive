---
title: "Local login needed for SSH to be available"
date: 2013-07-01
forum: Networking &amp; Wireless
---

### Post by m1dnight on 2013-07-01
Hi there,

I've recently set up my SSH server on an ubuntu machine. Everything works, but after a reboot it seems I need to be logged in locally in order to be able to SSH into the machine.

I can ping my ubuntu, but SSH denies access. 

What is the proper way of fixing this issue?

Thanks.

---

### Post by Kujua on 2013-07-01
Sounds strange. As per default config, sshd should be started during bootup.

> I've recently set up my SSH server on an ubuntu machine.
Can you give more details on the configurations you have done? Did you by any chance put any configs in your user-specific init files?

---

### Post by steeldriver on 2013-07-01
^^^ agreed, more info on your setup please - e.g. are you trying to do key based login to a machine on which your home dir is encrypted by any chance ?

---

### Post by m1dnight on 2013-07-03
Yes, the home directory is indeed encrypted for the user "christophe", and that is also the user I try to log in with.

The ssh is configured to work with rsa keys and the only thing I've changed is the /etc/ssh/sshd_config file.

It's a new ubuntu installation, and the only thing I've tinkered with is the ssh server.

I used these tutorials:

[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)

---

### Post by steeldriver on 2013-07-03
Did you follow the extra steps in the 'Troubleshooting --> Encrypted Home Directory' section of the first tutorial? [https://help.ubuntu.com/community/SSH/OpenSSH/Keys#Troubleshooting](https://help.ubuntu.com/community/SSH/OpenSSH/Keys#Troubleshooting)

If you have an encrypted home directory, then your authorized_keys file can't be put in ~/.ssh, it needs to be relocated to a location that is NOT encrypted prior to login (else you get in a Catch-22 situation - can't get the key until the dir is decrypted - which happens at login - but can't login without the key)

Make sure you set the ownerships and permissions EXACTLY as described in the tutorial

---

### Post by m1dnight on 2013-07-03
Excellent! :) That worked indeed. I'm sorry for missing that. Thank you very much!

ps: I can't seem to find how to mark this thread as solved?

---

### Post by steeldriver on 2013-07-03
No problem, easy to miss if you don't expect it - arguably it should be in the main setup section now that encrypted home dirs are becoming more common

I *think* that to mark a thread as solved now you have to manually edit the title

---

