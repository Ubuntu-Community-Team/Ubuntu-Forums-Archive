---
title: "Give Remote User Write but no Copy - Securely"
date: 2009-02-18
forum: Networking &amp; Wireless
---

### Post by mjzap on 2009-02-18
Not sure if this is where I should post as it covers several different topics (potentially) - in any case, here we go...

Basically, I am trying to set up a server where a single user/key will be used to allow remote clients to send their backup files to. Since this will be a global user/key, we only want to allow the clients to write to this directory and not copy the files back out.

We have explored using scponlyc and put this user in a jail but they still have copy permissions. sftp works the same way - put and get unrestricted. Yes, we would like the files to be encrypted for security.

Is there any way to accomplish this rather simply? (no extra scripts etc) Am I just missing something very obvious with what I have already?

Any help would be appreciated!!

---

