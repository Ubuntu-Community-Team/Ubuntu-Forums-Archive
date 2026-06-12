---
title: "Gray &quot;apply&quot; button in NetworkManager openvpn connection window"
date: 2010-11-19
forum: Networking &amp; Wireless
---

### Post by cthlhu1987 on 2010-11-19
I installed all the necessary packages for the networkmanager-openvpn function to function. The openvpn-connection-setting are successfully imported into the networkmanger via the conf file but the apply button is grayed out, so that actually saving and using the connection isn't possible? Does anyone know, where the problem is?
It's a fresh install of Ubuntu 10.10 after the upgrade from 10.04 sent the networkmanger down the drain.

---

### Post by Jethro_uk on 2010-11-19
Sounds like a policy issue.

read this thread:

[http://ubuntuforums.org/showthread.php?t=1616355](http://ubuntuforums.org/showthread.php?t=1616355)

look carefully in the file mentioned, at the <active> element. What is there ? "No" will cause the action detailed to be unavailable. Ideally "yes" or "auth_admin_keep" should be there. They will either allow all access, or prompt for a admin password.

---

### Post by cthlhu1987 on 2010-11-21
Shame on me, that is an "dumb user :oops: ](*,) :oops: :oops: ](*,) :oops::oops: ](*,) ) issue". I filled ALL the file don the first tab and voila; all works. SHAME ON ME

---

