---
title: "mythbuntu 810 ltsp-build-client failed"
date: 2009-04-28
forum: Mythbuntu
---

### Post by map7 on 2009-04-28
Whenever I try and run the build image with 'Allow unsigned packages' checked I get the following error:

**Error building image**
 ltsp-build-client failed with exit code 1.
Maybe you need to enable the "Allow unsigned
packages" checkbox?

What is going wrong here?
Is it bombing out on some package?

Does mythbuntu-control-center use any options when running the command 'ltsp-build-client'?

---

### Post by adelie on 2009-04-28
I am having the same issue.

---

### Post by adelie on 2009-04-28
I ran 

/bin/sh -c /usr/sbin/ltsp-build-client --mythbuntu --mythbuntu-copy-user-credentials --copy-sourceslist --arch i386 --base /opt/ltsp/ --accept-unsigned-packages

which I believe the mythbuntu GUI runs when creating the image. That completed successfully for me. Not sure if there are any more steps to complete.

---

### Post by map7 on 2009-04-30
Thank you, I've run that command as well and got it working.

Whilst testing this I used 'approx' to save some bandwidth every time I go and test.

---

