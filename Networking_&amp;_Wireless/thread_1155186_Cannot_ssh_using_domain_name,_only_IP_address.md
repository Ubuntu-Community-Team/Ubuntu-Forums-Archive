---
title: "Cannot ssh using domain name, only IP address"
date: 2009-05-10
forum: Networking &amp; Wireless
---

### Post by Bloodrule on 2009-05-10
I have a small LAN running Ubuntu on several machines.  I can login using SSH from one to another, but only if I use the IP address.  Assume I am trying to ssh to a machine with an IP of 192.168.0.10 and a hostname of Desktop.

ssh me@192.168.0.10 logs me into Desktop to a prompt me@Desktop:~$

But if I try

ssh me@Desktop I get a message "ssh: Desktop: Name or service not known" even though I know that the hostname Desktop exists.

What am I missing?

---

### Post by drs305 on 2009-05-10
First step in troubleshooting, so it has to be asked: Do you know *for sure* your Desktop IP address hasn't changed. Mine do on occasion as I move laptops around the house.

```

cat /etc/hosts

```

**Added:** I didn't explain the /etc/hosts as well as I could have, based on your reply. Not only the IP, but that Desktop is still linked to the correct IP address in your hosts file.

---

### Post by Bloodrule on 2009-05-10
No, definitely not a changing IP address - set to static.

---

### Post by apmcd47 on 2009-05-10
> **Bloodrule said:**
> I have a small LAN running Ubuntu on several machines.  I can login using SSH from one to another, but only if I use the IP address.  Assume I am trying to ssh to a machine with an IP of 192.168.0.10 and a hostname of Desktop.

ssh me@192.168.0.10 logs me into Desktop to a prompt me@Desktop:~$

But if I try

ssh me@Desktop I get a message "ssh: Desktop: Name or service not known" even though I know that the hostname Desktop exists.

What am I missing?

Stupid question, but ***where*** does the name Desktop exist?

Have you set up a DNS server for your local network? If so, are you sure your machines can access it?

If you are not using DNS have you tried setting up */etc/hosts* on the machine you are trying to connect to Desktop from? e.g.

```
192.168.0.10 Desktop
```
Use *sudoedit* to edit */etc/hosts*; or the sudo gui (*gksu* or *kdesudo*?) to edit the file using your favourite editor.

If this is not the answer you are looking for you need to be more specific to how the name is set up.

Andrew

---

### Post by Bloodrule on 2009-05-10
The name "Desktop" exists in the /etc/hosts file and was the name I gave the PC at installation.  So it appears at the shell as myname@Desktop~#$

Is that what you mean?

And no I don't think I have set up a DNS server on my LAN.  Maybe that's why it isn't working.  And yet I discovered that if I try to ssh [email]myname@Desktop.local[/email] it works, but myname@Desktop doesn't connect.

---

### Post by Iowan on 2009-05-10
> **Bloodrule said:**
> Is that what you mean?*Probably *not...> **apmcd47 said:**
> If you are not using DNS have you tried setting up */etc/hosts* on the machine you are trying to connect to Desktop from?  To re-iterate - is the name/address information in the CLIENT's /etc/hosts file, too? Apparently you have in in the server's /etc/hosts file.

---

### Post by Bloodrule on 2009-05-12
The solution to my problem was to manually enter the IP address and hostname of each machine on the LAN into the /etc/hosts file on the server from where I was making the outgoing ssh connection.  As soon as I did that, the system "knew" that entering 

***ssh myname@Desktop***

was actually performing 

***ssh myname@192.168.0.10***

Hope this helps someone else.

---

### Post by apmcd47 on 2009-05-12
> **Bloodrule said:**
> The solution to my problem was to manually enter the IP address and hostname of each machine on the LAN into the /etc/hosts file on the server from where I was making the outgoing ssh connection.  As soon as I did that, the system "knew" that entering 

***ssh myname@Desktop***

was actually performing 

***ssh myname@192.168.0.10***

Hope this helps someone else.

This is correct. Unless you are running some sort of name service such as DNS the hosts file has to be populated manually on each machine for all other machines. This is what I said to do in my original reply to you.

Glad you got it working.

Andrew

---

