---
title: "Audacity already running error ubuntu / kubuntu"
date: 2015-11-04
forum: Multimedia Software
---

### Post by Cinderboot on 2015-11-04
So I couldn't reply to some threads, and it seemed like it was a simple lock file problem.

Symptom: Start Audacity -> Get annoying message saying that it's already running.

Do ps a |grep audacity -> nothing.

Found temp folder path in my home directory.


Solution: Go to /var/tmp/audacity-<username> and remove audacity-lock-<username>


All good.

---

