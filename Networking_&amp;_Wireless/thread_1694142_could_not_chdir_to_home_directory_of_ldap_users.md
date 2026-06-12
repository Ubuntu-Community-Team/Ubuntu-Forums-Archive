---
title: "could not chdir to home directory of ldap users"
date: 2011-02-23
forum: Networking &amp; Wireless
---

### Post by satya1225 on 2011-02-23
Hi all,
I am satya.
I am new to ubuntu.
I am using 10.04 ubuntu server.
I configured the ldap server.
I configure the client machine to contact the ldap server for authentication.
But if i tried to ssh john@localhost, it says could not chdir to home directory /home/john: no such file or directory.
pls help me how to do it.

Thank you and regards
- Satya.

---

### Post by luvshines on 2011-06-19
Did you set the homeDirectory attribute for the users you are trying to ssh with ?
I think you can go with following options for user's home directory:
1. Let the home directories reside on a remote server and setup auto mount of the directories on login (NFS server should do fine)
2. Override the home directories parameter for all users and let them all login to a common directory on the server. You'll have to search for how to override homedirectory parameter. Since I still use the old way of slapd.conf , my method wouldn't be of any use if you are not using slapd.conf
3. Use make_home_dir in PAM to create home directories on the server whenever the users login to the system for the first time.

---

