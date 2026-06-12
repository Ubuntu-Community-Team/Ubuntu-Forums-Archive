---
title: "Difficulties with multiple ssh key logins"
date: 2009-11-23
forum: Networking &amp; Wireless
---

### Post by malluen on 2009-11-23
I recently have been setting up my file server which I would like to share with my friends and family via ssh. All users will be using the same username on the server as there PC for simplicity. Anyways I've created the public and private keys. Copied them over to the server via scp and renamed it authorized_keys2 as standard. After checking user permissions 600 for authorized_keys2 and 700 for the .ssh folder I run ssh-add on the client side. Still nothing. Only password entry thus far. I've been pounding my head for about 3 days straight (strangely enough I've gotten my own machine to quick login correctly, but no other) and could use a outsiders opinion on what I am doing wrong or possibly not at all.

---

### Post by falconindy on 2009-11-23
I suspect you haven't changed the sshd_config to point to the authorized_keys2 file (and make sure RSA/PubKeyAuth is enabled). If you'll be connecting by key rather than password, you should also disable password logins.

---

### Post by malluen on 2009-11-23
Ok it turns out a night of absolutely no sleep can do massive damage on the brain and cause frustration at the same time. I mistyped my file permissions several times in a row =P

---

