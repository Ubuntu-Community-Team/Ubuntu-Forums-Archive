---
title: "NFS or Samba"
date: 2009-01-06
forum: Networking &amp; Wireless
---

### Post by e24ohm on 2009-01-06
forum:
I am trying to link a CentOS box acting as the as file server running NFS, and using Ubuntu as my desktop client. Since i am using linux based systems, I thought about only using or implementing 'NFS'.

But I am very Curious, aside from the benefits of Samba allowing the ability to run services for file and print sharing for windows environment, what are the benefits I would see in my implantation? My main concerns are with speed and reliability. Simply put, which service is faster?

I have already played around with the ‘nfs’ options when I mount my drive on the client side, but I am unsure what the speed range is, and how do I judge the range I should input. Is there a “rule of thumb”, a mathematical formula to use, that takes in account for the network speed and NICs?

Just brainstorming and wanted to hear what individuals have to say, and hopfully get some real world examples.

Thank you,
E

---

### Post by cariboo on 2009-01-06
I don't have any specific numbers, but to me NFS feels faster than Samba. To find out what transfer speeds I am actually getting I use a program called iperf, it is available in the repositories.

Jim

---

### Post by theozzlives on 2009-01-06
From my wireless laptop downstairs to my wired network upstairs, the transfer rate for copying files is about 1.6 MB/s running samba and 802.11g.

---

### Post by e24ohm on 2009-01-06
> **cariboo907 said:**
> I don't have any specific numbers, but to me NFS feels faster than Samba. To find out what transfer speeds I am actually getting I use a program called iperf, it is available in the repositories.

Jimhey thanks for the post, and I will try out 'iperf' and see what I get. Thanks again

---

