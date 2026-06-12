---
title: "Unable to mount location failed to retrieve list from server"
date: 2011-06-19
forum: Networking &amp; Wireless
---

### Post by cmann_97 on 2011-06-19
I loaded 9.10 version on a test pc. Immediately after the installation and reboot, all of the windows PC's and NAS drives I have (13) showed up under network in Ubuntu. I then proceeded to assign static addressing and loaded updates, Then I couldn't see the windows machines anymore. And this was BEFORE I started modifying the smb.conf file. My Windows workgroup name is not "workgroup". It's odd that all the Win PC's and NAS drives were visible from the out of the box 9.10 install....

---

### Post by capscrew on 2011-06-19
> **cmann_97 said:**
> I loaded 9.10 version on a test pc. Immediately after the installation and reboot, all of the windows PC's and NAS drives I have (13) showed up under network in Ubuntu. I then proceeded to assign static addressing and loaded updates, Then I couldn't see the windows machines anymore. And this was BEFORE I started modifying the smb.conf file. My Windows workgroup name is not "workgroup". It's odd that all the Win PC's and NAS drives were visible from the out of the box 9.10 install....

Did you install Samba *server* yourself?  Did you map the IP address to the hostname on Ubuntu?

The workgrop just visually associates the samba shares in a group setting you can have as many workgroups as you like.

---

