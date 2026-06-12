---
title: "ldap egroupware"
date: 2009-01-22
forum: Networking &amp; Wireless
---

### Post by peterroots on 2009-01-22
Hi I am running an ldap server and egroupware and wanted to use the ldap server to store the address books and account details.
From various sources I have managed to get up and working but I have one problem left.  I can not edit any of the group address books or my personal address book in egroupware. (but I can read them ok)
I can create accounts and then edit the details of that person in the accounts address book.
I can edit entries in the group and personal address books via Kontact so i am assuming it is something I have done wrong or missed in either the egroupware setup or in slapd.conf
I added an acl file that I found on the internet somewhere that was supposed to give users access to their own address book entries and to group books but I had to change it a bit as the ldap structure they had was different from mine - it appears to have no influence on the ability of the admin (i.e. me) to edit account address details

---

