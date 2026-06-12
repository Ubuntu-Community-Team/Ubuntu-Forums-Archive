---
title: "LDAP and sudoers not working in gui"
date: 2011-10-12
forum: Networking &amp; Wireless
---

### Post by Bufke on 2011-10-12
I've made a group in LDAP for sudo users. I then added in sudoers

%faculty ALL=(ALL) ALL

faculty is my group name. I use pam_ldap with OpenLdap. Now on command line the users can use sudo, but in any gui such as update manager they can't select themselves. They can only select the local sudo users. Any idea what's happening? The groups command for a ldap user gives me 

faculty adm dialout cdrom plugdev lpadmin admin sambashare it_admins students

---

