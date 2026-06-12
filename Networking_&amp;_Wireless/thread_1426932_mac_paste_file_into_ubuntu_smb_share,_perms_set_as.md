---
title: "mac paste file into ubuntu smb share, perms set as 0700"
date: 2010-03-10
forum: Networking &amp; Wireless
---

### Post by stevewasiura on 2010-03-10
We setup a xubuntu server on our lan to do some web dev testing in drupal.
We have a mac and a winxp comp connected to the samba share
the winxp comp can paste a file into the samba share, and it has the perms 0755 - great.
the mac comp pastes a file into the samba share, but it's perms are 0700
 
the mac is connected to the samba share using smb://ubuntuserver/sharename
it doesn't prompt me for a login, i think it is already stored in the mac keychain
 
the auth.log shows the mac connected with the valid ubuntu account, same acct used by winxp comp
 
the mac can created a new file in the samba share and the perms are 0755, but when the file is pasted, the perms are set to 0700
 
any ideas?

---

