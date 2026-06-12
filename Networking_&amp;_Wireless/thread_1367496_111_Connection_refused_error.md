---
title: "111 Connection refused error"
date: 2009-12-29
forum: Networking &amp; Wireless
---

### Post by mugwump40 on 2009-12-29
I've been searching all over for a resolution, but can't find any for the 111 Connection refused error.  I can't update or add packages.  Firefox works fine, so I think it is internal.  Looked at all network settings, don't see anything obvious.  Here is what I get whenever I try to add a package in Synaptic:  


W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/Release.gpg](http://archive.canonical.com/ubuntu/dists/hardy/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)



W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dists/hardy/partner/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)



W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)



W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)



W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)



W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)



W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)



W: Some index files failed to download, they have been ignored, or old ones used instead.



Can anyone help with this??  TNX!!

---

### Post by shredder12 on 2009-12-30
the issue is that on update the system is trying to connect to the localhost server i.e. your machine or 127.0.0.1 on port 4001 which is ridiculous and thats why you are getting 111 connection refused error.
But I don't know why is this problem occuring or how to fix it.

---

### Post by iponeverything on 2009-12-30
See:

[https://lists.ubuntu.com/archives/ubuntu-users/2006-May/079426.html](https://lists.ubuntu.com/archives/ubuntu-users/2006-May/079426.html)

---

