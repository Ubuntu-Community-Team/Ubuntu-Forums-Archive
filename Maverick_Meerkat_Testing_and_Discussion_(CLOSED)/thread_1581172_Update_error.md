---
title: "Update error"
date: 2010-09-24
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Quackers on 2010-09-24
Since last night I have been getting the error in the attached screenshot.
It says
W:GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192, W:Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead.

It still updates plenty of things though.

---

### Post by philinux on 2010-09-24
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/645110](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/645110)

---

### Post by FuturePilot on 2010-09-24
That PPA currently does not have any packages for Maverick. You'll have to disable it until they do. Also, you're missing the gpg key for it which may be due to the bug above.

---

### Post by Quackers on 2010-09-24
Thank you, it's solved.
I was looking for 2 ppa's to uncheck when only one was needed. Apologies.

---

