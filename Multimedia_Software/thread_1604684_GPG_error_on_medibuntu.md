---
title: "GPG error on medibuntu"
date: 2010-10-24
forum: Multimedia Software
---

### Post by jimbob on 2010-10-24
I get the following error on all my updates:

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

How to fix this?

---

### Post by TODDMAN on 2010-10-26
Same problem after upgrading from 10.4

---

### Post by jimbob on 2010-10-26
I did a couple of things but I believe what finally fixed it for me was this;

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2EBC26B60C5A2783

Before I did that I did sudo apt-get update && apt-get upgrade and I noticed it generated a new initrd module so that may have somethng to do with it on mine.

Let me know if it fixes it for you and I'll mark this as solved.

---

