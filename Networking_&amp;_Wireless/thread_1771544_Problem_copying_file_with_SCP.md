---
title: "Problem copying file with SCP"
date: 2011-05-30
forum: Networking &amp; Wireless
---

### Post by Thyagaraj on 2011-05-30
I have problem copying files to cloud servers with SCP from my office. When I do scp of 17MB war file its says STALLED and then reconnect and again says stalled like the one below:

```
#scp Desktop/myapp.war user1@204.x.x.x:/tmp/

user1@204.x.x.x's password: 
myapp.war                                         12% 2112KB 736.4KB/s - stalled -^
```
I checked if it the problem with my ISP but, checking the upload speed they said everything is fine from their side and personally I checked attaching the file in the gmail and it uploaded fine in 3mins usually. So I think no issue from the ISP side.

Contacted the cloud server technician if they could help, and they proved sending files between cloud servers and said everything is fine from their side.

I tried other cloud servers, tried winSCP, tried rsync but the result is same. Somehow I have to make this work as how it was, because the web-developers are waiting for the production deployment.

Today, I took someones help to copy to the Staging cloud server allowing his ip in iptables. This means only from my office the scp stalls but from outside if you have access then everything works fine.

I'm not knowing how I could solve this issue. I think I should have very good network side knowledge. Anybody came across this?, how it could be solved?.

Please need help. Thanks you!

---

### Post by Thyagaraj on 2011-05-30
Anybody has any idea?

---

