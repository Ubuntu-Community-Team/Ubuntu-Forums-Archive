---
title: "help setting up computer lab"
date: 2010-04-06
forum: Networking &amp; Wireless
---

### Post by gforster on 2010-04-06
Right now, we have 30 computers in our school computer lab. Currently, each computer has a generic student account that all students share. What I would like to be able to do is have each student have their own login and be able to use that login at any of the 30 computers. When logged in, all of their files would be available to them - either as a network mounted disk or, preferably, as their home folder.

There seem to be so many options out there that are a little bit confusing - NFS, LDAP, SSO, etc.  They seem to be inter-related, but I can't figure out where to start and what direction to take.  If someone could point me in the right direction, I would be ever so grateful.

---

### Post by DGortze380 on 2010-04-06
> **gforster said:**
> Right now, we have 30 computers in our school computer lab. Currently, each computer has a generic student account that all students share. What I would like to be able to do is have each student have their own login and be able to use that login at any of the 30 computers. When logged in, all of their files would be available to them - either as a network mounted disk or, preferably, as their home folder.

There seem to be so many options out there that are a little bit confusing - NFS, LDAP, SSO, etc.  They seem to be inter-related, but I can't figure out where to start and what direction to take.  If someone could point me in the right direction, I would be ever so grateful.

Start with LDAP. It will handle log-in authentication on a central server.

---

### Post by Iowan on 2010-04-06
[Here]("https://help.ubuntu.com/9.10/serverguide/C/network-authentication.html") is one LDAP help page/guide.

---

### Post by gforster on 2010-04-07
What is the benefit of LDAP over NIS?

---

### Post by DGortze380 on 2010-04-07
I have no experience with NIS, but it looks like it has some issues I'd certainly avoid at all cost. None of this is a consideration with LDAP.

Not to mention 3/4 of the tutorials I saw were focused on 'Securing NIS'. Anything that needs an excessive amount of hardening raises a red flag for me.

> 
Note: This assumes your server and clients have static IP addresses. NIS with dynamic IP addresses present a serious security hazard. See the "Security" section, below, for a discussion of security problems inherent with NIS and how to avoid them. 

Security: NIS is a dangerous thing. Anyone who can get access to the daemon can dump your password lists. If they can do that, then they have your passwords. It doesn't matter that the passwords are encrypted; they are plaintext equivalent (since authentication is done with encrypted passwords, you don't need to know the text password, you just need to write an app to provide the encrypted one to the authentication system correctly). 

A note about administration: Since the root user's account is disabled, make sure that whomever is to admin the machine is in the /etc/sudoers file on the client machine. It is also a good idea to have those users as local users on the client machine, with the same UID as is in the domain password list. It keeps things nice and consistent, and if there ever was a problem, you might need to have a local account to gain access to the machine. 

Solution #1: IPSec. You can set up all your domain members to only talk to each other over IPSec which will effectively authenticate that your client is who it says it is. How? Well, it encrypts traffic to the server with the server's key, and the server sends back all replies encrypted with the client's key. The traffic is decrypted with the respective keys. So, if the client doesn't have the keys that the client is supposed to have, it can't send or receive data. Provided the file containing the keys is reasonably secret (only readable by root), you can't get the keys unless you compromise the client. And, if you compromise the client, you can dump the password list anyway, so the attacker has got you (which is a flaw in most domain authentication systems).


---

### Post by gforster on 2010-04-07
Gotcha. As I read some more, it seems that NIS is outdated and people moved to LDAP from it. I am still a little confused, but I do believe that LDAP is the right approach. It seems I could integrated NFS at a later time if that were desirable without too many problems.

---

### Post by DGortze380 on 2010-04-07
> **gforster said:**
>  It seems I could integrated NFS at a later time if that were desirable without too many problems.

Correct.

---

### Post by gforster on 2010-04-09
Oh my, oh my. It seems that LDAP was changed with Karmic, but I am wanting to install on Lucid 10.04. Still, it seems that Karmic instructions should work, but I am getting very lost. I cannot figure out what my FQDN is. If you haven't figured it out, I am very new at networking (will be working on getting a second bachelors in it soon, though)

---

