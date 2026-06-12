---
title: "Samba Not Locking files in use"
date: 2012-10-19
forum: Networking &amp; Wireless
---

### Post by debianguru85uk on 2012-10-19
Hello,

I installed Samba on Ubuntu Server 12.04 and added users to the system, created a shared directory with the following settings:

[share]
comment = Main share
path = /share
guest ok = no
writable = yes
create mask = 0755
directory mask = 0755
browsable = yes
write list =  dave  slav
force group = users

The only thing I changed in global was enabled security = user

The problem happens when user dave has a file open, user slav open the file without any notification that file is already open. 

Please let me know if this is some sort of bug in SAMBA or am I missing something.

---

### Post by debianguru85uk on 2012-10-19
Hi everyone,

I managed to solve the problem. 

I was doing the test using notepad file. 

File lock only works if application supports it. 

I did the test using Excel file and I can confirm that there are no issues. 

Thank you all.

---

