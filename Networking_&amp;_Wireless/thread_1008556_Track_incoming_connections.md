---
title: "Track incoming connections?"
date: 2008-12-11
forum: Networking &amp; Wireless
---

### Post by rhcm123 on 2008-12-11
I've been being hit repeatedly with SSH brute force attacks on my home server. However, i need to leave the SSH port open for SSH (duh) and SSHFS. (I don't want to use SMB or FTP for data transfer... i'd be more nuts then I am now.)

I would like to use deny hosts to block the attackers, but I can't figure out the IP their using. can anybody reccomend me a good program (preferably kept in the repositories, as i am not particularly fond of unpacking tarballs on the commandline) to track my incoming connections?

---

### Post by spiderbatdad on 2008-12-11
fail2ban

the config file is /etc/fail2ban/jail.local

---

### Post by albinootje on 2008-12-11
You can install denyhosts from the repositories, after that read the documentation in /usr/share/doc/denyhosts/ and edit the config-file.

On some servers i'm following a different approach, using AllowUsers in 
/etc/ssh/sshd_config to restrict my own access via ip-addresses.

For example :
AllowUsers root@65.100.200.111 root@66.101.201.112

See also : man sshd_config

---

### Post by jonobr on 2008-12-11
You could also change your SSH default port number also,
change the port number in /etc/ssh/sshd.config
ONce thats done you would need to change the port number on any clients wishing to connect

---

### Post by spiderbatdad on 2008-12-11
setting AllowUsers and AllowGroups is a definitely a good practice. Changing the default port is not always practical, and shouldn't be necessary. I would not set root as a user.
fail2ban is good in that it will ban the offending ip addresses after a specified number of bad login attempts.

---

### Post by albinootje on 2008-12-11
You're right, using root@ twice in that example was not a very good idea :(
Next time i'll remember to use the users steve.b@ and bill.g@ in examples :)

---

### Post by spiderbatdad on 2008-12-11
> **albinootje said:**
> You're right, using root@ twice in that example was not a very good idea :(
Next time i'll remember to use the users steve.b@ and bill.g@ in examples :)

Are you sure this isn't an example of "DenyUsers"?:lolflag:

---

### Post by albinootje on 2008-12-11
Rotfl :)

---

