---
title: "Nfs"
date: 2006-07-15
forum: Networking &amp; Wireless
---

### Post by jyer on 2006-07-15
Hi,
I know that this question doesn't concern any hardware failure, but I didn't know where else to post a question regarding networking.
I've been configuring an NFS server on my local network. I'm pretty sure I set up the server and configured the export, hosts.allow and hosts.deny correctely. Nevertheless, as I want to mount a filesystem from the client, the server denies permission. I've checked that the user name has the same IUD number on the server and client side. 
A quick google up led me to the following sentence: 
> I have encountered a problem using autofs to mount remote nfs shares. The problem was that the server's log reports successful authentication whereas the client told "permission denied by server". The workaround is to put "/etc/init.d/portmap restart" into "/etc/conf.d/local.start". That problem seems to be related to how portmap and nfs interact...
Being a newbye, this unfortunately didn't help me that much. Questions are the following:
1. How do I access the server's log reports
2. What does s/he mean by "put "/etc/init.d/portmap restart" into "/etc/conf.d/local.start""?
Thanks in advance,
jr

---

### Post by jyer on 2006-07-16
By the way, I wonder if this as anything to do with the sudo command in Ubuntu. My shared folder is owned by user on the server and I have to mount it on the client by using sudo command. Could root on one side and user on the other be the source of my problem?

---

