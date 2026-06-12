---
title: "Impersonation in Samba server"
date: 2011-01-19
forum: Networking &amp; Wireless
---

### Post by michael_f on 2011-01-19
Hi,

I've setup a Samba server on Ubuntu 10.10 and can login to the server and read/write/create files.

I want to allow only users in a certain unix group to be allowed to login to Samba and this is now working.

I have also installed acl and setup permissions for the shared directory for the users.

However, when users connect to the Samba share, they are given access based on the permissions of which the Samba server process is running under, not the user's permissions.

I want the server to impersonate the users and grant them access to the individual files/folders in the shared directory as per the acl permissions.

Does anyone know how to fix this?

Thanks.

---

