---
title: "Error with ssh-copy-id"
date: 2012-03-01
forum: Networking &amp; Wireless
---

### Post by YesGood on 2012-03-01
Hi

Please, help me.

I created a ssh key and then I need to copy this id to other host

and I run this command
[FONT=Century Gothic]ssh-copy-id -i  ~/.ssh/id_rsa.pub user@remotehost[/FONT]

and the result is
[FONT=Century Gothic]/usr/bin/ssh-copy-id: ERROR: No identities found[/FONT]
 
[FONT=Verdana]I see and try several tutorial with this error, but I cann't solved.

Any ideas?

Thanks.
[/FONT]

---

### Post by Iowan on 2012-03-02
> **YesGood said:**
> 
[FONT=Century Gothic]ssh-copy-id -i  ~/.ssh/id_rsa.pub user@remotehost[/FONT]

Probably a silly question, but you ARE substituting your username and hostname for user@remotehost?

---

### Post by YesGood on 2012-03-04
Hi, thanks Iowan

Yes, I sustituted with the respective name of user and hostname.

---

### Post by Iowan on 2012-03-05
I stumbled across [this]("http://www.thegeekstuff.com/2008/11/3-steps-to-perform-ssh-login-without-password-using-ssh-keygen-ssh-copy-id/")...

---

### Post by agestrada on 2012-04-03
Thanks Iowan, that solved the problem for me. I copy here the solution from the blog:

  	 	 	 	 	 	   "If trying to connect to x2go for the first time  gives the error:
 

 Authentification Failed
 The host key for this server was not found but an othertype of key exists.An Attacker might change the default server key toconfuse your client into thinking the key does not exist
 

 This will happen if you SSH into the server before installing x2go. SSH by default likes ecdsa keys, and x2go doesn't. On the server, edit the ssh config:
 sudo nano /etc/ssh/sshd_config
 

 Then comment out this line with a #:
 HostKey /etc/ssh/ssh_host_ecdsa_key
 

 Now restart ssh:
 sudo service ssh restart
 

 On your client you need to remove your old key. I just removed all of them.
 rm .ssh/known_hosts"

---

### Post by Iowan on 2012-04-03
Good to hear - you can mark this one [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

