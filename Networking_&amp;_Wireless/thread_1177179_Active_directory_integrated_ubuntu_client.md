---
title: "Active directory integrated ubuntu client"
date: 2009-06-03
forum: Networking &amp; Wireless
---

### Post by piddewest on 2009-06-03
Hi!

In test purpose i have successfully joined an ubuntu 9.04 client to our windows 2003 active directory using likewise open 5.

So far so good. I am able to login and can browse network resources through Network.

BUT....since we have approximatly 3000 users i need to be able to map their homedirectory and some others shares in a simple way so that it is connected after logon. Their homedirectories are on serveral windows 2003 servers. Is there a way to do this with out to much work?

We are in a phase when we want to test ubuntu if it is an alternative to some windows clients. 

I really like linux as a standalone client (home use)...but does it coexist well in a mixed windows and linux company environment?

---

### Post by theDaveTheRave on 2009-06-03
piddewest

I get the feeling that you want to automount networked shares which I believe is possible using fstab.

checkout bodhi.zazen thread [here]("http://ubuntuforums.org/showthread.php?t=283131") for a complete fstab guide.

David.

ps, did that help at all??

---

### Post by Stuart42 on 2009-06-03
I'm trying to a similar thing, with OS X and Linux clients. I've been writing a bash script to check group membership and based on that mount specific shares. Works (mostly) on OS X, aside from some odd issues checking membership, but on Ubuntu mounting the cifs share is giving me a headache. I'm expecting mount.cifs to use the kerberos ticket obtained during login, but it doesn't seem to do this. As soon as I find a way around this, I will be smiling.

EDIT: This is actually simple

just specify -o "user=username" and you're golden :-)

---

### Post by piddewest on 2009-06-03
Thanks for your ideas.....

The mount command would be great if it could get some variables like the %HOMEDIR from active directory? Every user in AD has a homedir specified. And if likewise or any of the mount commands could get that information everything would be great.

And it would be great if it isnt necessary to specify a password to mount the share. It have to use the kerberos ticket like you said.

But has anyone had a success with this? Or is it a feature to come?

I have seen a few quite complicated examples using pam_mount. But it seems that the user have to specify a password anyway....

---

### Post by Stuart42 on 2009-06-04
I still havent' got this working the way I'd like.
It may be worth looking through the tools that are installed with likewise, some of them may be able to pull this info.

---

