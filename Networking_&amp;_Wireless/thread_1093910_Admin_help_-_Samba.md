---
title: "Admin help - Samba"
date: 2009-03-12
forum: Networking &amp; Wireless
---

### Post by JSchiffman on 2009-03-12
Hi; Newbie here.

I've managed to get Ubuntu 8.1 running and doing most of what I want. I'm trying to connect to a SOHO network workgroup of MS Win XP machines. The workgroup is behind a Netgear router, the Win machines work fine, I share and move files between them at will. I can access the internet from the Ubuntu platform. 

I understand I need Samba to share files between the computers. In various Samba docs I've read, I understand I need to edit the smb.conf file in etc/samba, and I think I understand the edits needed. I get that I should edit a copy & keep the original intact. Can't do it, don't have permission. 

The file is permissioned for user-root, group-root. How do I get at the file to make the edits. I can't figure out how to log into root. Do I create a new user for group-root?

Thanks in advance

---

### Post by dmizer on 2009-03-12
> **JSchiffman said:**
> Hi; Newbie here.

I've managed to get Ubuntu 8.1 running and doing most of what I want. I'm trying to connect to a SOHO network workgroup of MS Win XP machines. The workgroup is behind a Netgear router, the Win machines work fine, I share and move files between them at will. I can access the internet from the Ubuntu platform. 

I understand I need Samba to share files between the computers. In various Samba docs I've read, I understand I need to edit the smb.conf file in etc/samba, and I think I understand the edits needed. I get that I should edit a copy & keep the original intact. Can't do it, don't have permission. 

The file is permissioned for user-root, group-root. How do I get at the file to make the edits. I can't figure out how to log into root. Do I create a new user for group-root?

Thanks in advance

In order to perform actions as root, temporarily assign root privileges to your account by prefixing commands with the "sudo" command via CLI, like so:
```
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf-backup
```

For more specific information on how to configure samba, see the first link in my sig.

---

