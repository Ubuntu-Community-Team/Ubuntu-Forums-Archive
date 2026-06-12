---
title: "pam_mount not working with likewise-open"
date: 2010-12-03
forum: Networking &amp; Wireless
---

### Post by ssalman.mansoor on 2010-12-03
I have installed likewise-open to authenticate on Active Directory and pam_mount for mounting folders.
Now when I logon to local user 

Dec  3 17:10:38 ltsp-server3 sshd[8742]: pam_mount(pam_mount.c:364): pam_mount 2.3: entering auth stage
Dec  3 17:10:38 ltsp-server3 sshd[8724]: Accepted keyboard-interactive/pam for salman from 10.199.104.45 port 3250 ssh2
Dec  3 17:10:38 ltsp-server3 sshd[8724]: pam_unix(sshd:session): session opened for user salman by (uid=0)
Dec  3 17:10:38 ltsp-server3 sshd[8724]: [module:pam_lsass]pam_sm_open_session failed [login:salman][error code: 40081]
Dec  3 17:10:38 ltsp-server3 sshd[8724]: pam_mount(pam_mount.c:553): pam_mount 2.3: entering session stage
Dec  3 17:10:38 ltsp-server3 sshd[8724]: pam_mount(misc.c:38): Session open: (uid=0, euid=0, gid=0, egid=0)
Dec  3 17:10:38 ltsp-server3 sshd[8724]: pam_mount(pam_mount.c:612): no volumes to mount
Dec  3 17:10:38 ltsp-server3 sshd[8724]: command: 'pmvarrun' '-u' 'salman' '-o' '1'
Dec  3 17:10:38 ltsp-server3 sshd[8760]: pam_mount(misc.c:38): set_myuid<pre>: (uid=0, euid=0, gid=0, egid=0)
Dec  3 17:10:38 ltsp-server3 sshd[8760]: pam_mount(misc.c:38): set_myuid<post>: (uid=0, euid=0, gid=0, egid=0)
Dec  3 17:10:38 ltsp-server3 sshd[8724]: pam_mount(pam_mount.c:440): pmvarrun says login count is 2
Dec  3 17:10:38 ltsp-server3 sshd[8724]: pam_mount(pam_mount.c:643): done opening session (ret=0)
Dec  3 17:10:40 ltsp-server3 sshd[8724]: pam_unix(sshd:session): session closed for user salman
Dec  3 17:10:40 ltsp-server3 sshd[8724]: [module:pam_lsass]pam_sm_close_session error [error code:40081]
Dec  3 17:10:40 ltsp-server3 sshd[8724]: pam_mount(pam_mount.c:691): received order to close things
Dec  3 17:10:40 ltsp-server3 sshd[8724]: pam_mount(pam_mount.c:693): No volumes to umount
Dec  3 17:10:40 ltsp-server3 sshd[8724]: command: 'pmvarrun' '-u' 'salman' '-o' '-1'
Dec  3 17:10:40 ltsp-server3 sshd[8853]: pam_mount(misc.c:38): set_myuid<pre>: (uid=0, euid=0, gid=0, egid=0)
Dec  3 17:10:40 ltsp-server3 sshd[8853]: pam_mount(misc.c:38): set_myuid<post>: (uid=0, euid=0, gid=0, egid=0)
Dec  3 17:10:40 ltsp-server3 sshd[8724]: pam_mount(pam_mount.c:440): pmvarrun says login count is 1
Dec  3 17:10:40 ltsp-server3 sshd[8724]: pam_mount(pam_mount.c:720): salman seems to have other remaining open sessions
Dec  3 17:10:40 ltsp-server3 sshd[8724]: pam_mount(pam_mount.c:728): pam_mount execution complete
Dec  3 17:10:40 ltsp-server3 sshd[8724]: pam_mount(pam_mount.c:115): Clean global config (0)

Which seems ok but when I logon to Domain user


Dec  3 17:10:05 ltsp-server3 sshd[8633]: pam_mount(pam_mount.c:364): pam_mount 2.3: entering auth stage
Dec  3 17:10:05 ltsp-server3 sshd[8630]: Accepted keyboard-interactive/pam for MYDOMAIN\\ssalman.mansoor from 10.199.104.45 port 3247 ssh2
Dec  3 17:10:05 ltsp-server3 sshd[8630]: pam_unix(sshd:session): session opened for user MYDOMAIN\ssalman.mansoor by (uid=0)

Note: It is not even trying to mount share :'(
I have Ubuntu 10.10 installed.

---

### Post by ssalman.mansoor on 2010-12-03
And at last I got it working :). I got reference from [http://ubuntuforums.org/archive/index.php/t-878685.html](http://ubuntuforums.org/archive/index.php/t-878685.html)
Basically the problem was that in common-session I had 

session [default=1]                     pam_permit.so
session requisite                       pam_deny.so
session required                        pam_permit.so
session required        pam_unix.so
session        sufficient      pam_lsass.so
session optional        pam_mount.so
session optional                        pam_ck_connector.so nox11

i.e. sufficient before pam_mount thats why it was not going forward.

Then I just changed the order and it worked.

session [default=1]                     pam_permit.so
session requisite                       pam_deny.so
session required                        pam_permit.so
session required        pam_unix.so
 session optional        pam_mount.so
session optional                        pam_ck_connector.so nox11
session        sufficient      pam_lsass.so

I was wondering why I reinstalled Ubuntu instead of searching the problem :)

---

