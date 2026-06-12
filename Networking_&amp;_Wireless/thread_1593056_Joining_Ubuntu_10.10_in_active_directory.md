---
title: "Joining Ubuntu 10.10 in active directory"
date: 2010-10-11
forum: Networking &amp; Wireless
---

### Post by guimenez on 2010-10-11
i've join my new ubuntu 10.10 to AD but i can't login.
I'm using them same configurations like in the 10.04(that works perfectly) but when i login, it always give me autentication failed.
Even if i put DOMAIN\user

-----------------------------------------------------------
this is my configuration files:

---------------- /etc/pam.d/common-auth ---------------
auth	[success=2 default=ignore]	pam_unix.so nullok_secure
auth	[success=1 default=ignore]	pam_lsass.so try_first_pass
auth	requisite	 pam_deny.so
auth	required	 pam_permit.so
auth	optional	 pam_mount.so 
session	optional	 pam_mount.so 


---------------- /etc/pam.d/common-session -------------
session	[default=1]	 pam_permit.so
session	requisite	 pam_deny.so
session	required	 pam_permit.so
session	required	pam_unix.so 
session	sufficient	pam_lsass.so 
session	optional	pam_mount.so 
session	optional	pam_ck_connector.so nox11


--------------- /etc/pam.d/login ------------------------
auth optional pam_faildelay.so delay=3000000
auth required pam_securetty.so
auth requisite pam_nologin.so
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so close
session required pam_env.so readenv=1
session required pam_env.so readenv=1 envfile=/etc/default/locale
@include common-auth
auth optional pam_group.so
session required pam_limits.so
session optional pam_lastlog.so
session optional pam_motd.so
session optional pam_mail.so standard
@include common-account
@include common-session
@include common-password
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so open
session optional pam_mount.so 
auth optional pam_mount.so try_first_pass


----------------- /etc/security/pam_mount.conf.xml ------------------
<volume
user="*"
server="servername.domain.local"
path="UserShares"
mountpoint="home"
fstype="cifs"
/>

<cifsmount>mount -t cifs //%(SERVER)/%(VOLUME)/%(USER) %(MNTPT)/%(USER) -o "user=%(USER),uid=%(USERUID),gid=%(USERGID)%(befor e=\",\" OPTIONS)"</cifsmount>

------------------------------------------------------------------

Like i said, the same config works in Ubuntu 10.04

many thanks

---

