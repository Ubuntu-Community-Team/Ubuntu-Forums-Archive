---
title: "Connecting to Mac via ssh"
date: 2009-10-10
forum: Networking &amp; Wireless
---

### Post by gmarton on 2009-10-10
All up to date on Jaunty, no longer can connect to a mac via ssh. I can connect to another ubuntu box but not mac. 
ssh -vvv shows it is stuck on :
Next authentication method: gssapi-with-mic
Anyone else having this issue?

---

### Post by gmarton on 2009-10-12
In case anyone else had same issue:
Edited /etc/sshd_config on the server side to include 
> GSSAPIAuthentication no

Then restarted the server:
> sudo SystemStarter -v restart SSH
Now I can connect to the macs again.

I hope this will save someone a few hours of frustration.

---

