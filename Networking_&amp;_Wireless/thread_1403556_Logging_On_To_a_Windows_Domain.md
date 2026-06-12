---
title: "Logging On To a Windows Domain"
date: 2010-02-10
forum: Networking &amp; Wireless
---

### Post by chiques on 2010-02-10
My Windows XP Pro box had to be added to x.y.com domain. What is the process to do this with my Ubuntu box? 

Currently I can browse the network (from my Ubuntu box) and see all the folders I would like to access but am unable to access them ( I assume because they require me to be logged on to the domain).

---

### Post by suseendran.rengabashyam on 2010-02-11
Hi,

When you click on the share in Nautilus, do you get a password dialog?

I assume there is no Domain Controller involved here. If there is no Domain Controller in the picture, you will need to find out the workgroup that the XP machine is a part of and provide that along with the user name and password (appropriate for the XP share) in the password dialog in Nautilus to connect to the share of the XP Machine.

---

### Post by chiques on 2010-02-12
> **suseendran.rengabashyam said:**
> Hi,

When you click on the share in Nautilus, do you get a password dialog?

I assume there is no Domain Controller involved here. If there is no Domain Controller in the picture, you will need to find out the workgroup that the XP machine is a part of and provide that along with the user name and password (appropriate for the XP share) in the password dialog in Nautilus to connect to the share of the XP Machine.

Hi,
I don't see a 'share option' in Nautilus. May I ask for a reference on how to perform this or maybe some more detailed instructions?

I don't know if there is a domain controller involved. I can give it a shot regardless.

I have the workgroup, username and password. As soon as I figure out how to perform the task you mention above, I'll try it.


Thanks:P:P

---

### Post by chiques on 2010-02-15
'ping

Any suggestions?

---

