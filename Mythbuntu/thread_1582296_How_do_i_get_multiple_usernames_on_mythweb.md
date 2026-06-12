---
title: "How do i get multiple usernames on mythweb"
date: 2010-09-26
forum: Mythbuntu
---

### Post by geekyhawkes on 2010-09-26
Pretty much as per the title really, is there a way i can make several user names / passwords for my mythweb setup?

Thanks

---

### Post by ian dobson on 2010-09-26
Hi,

Webweb doesn't support multiple users with different levels at the moment, I think something is planned for .25

Currently mythweb uses the .htaccess files from apache to only allow users to access mythweb. So the only way to limit access to mythweb is to create sveral accounts. Have a look at /etc/mythtv/mythweb-htaccess in the section:-

AuthName "MythTV"
AuthType basic
AuthUserFile /PATH/TO/.htpasswd
require valid-user

The file .htpasswd contains a list of users and passwords.

Hope this helps
Regards
Ian Dobson

---

