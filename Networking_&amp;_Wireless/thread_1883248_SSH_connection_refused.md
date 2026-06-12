---
title: "SSH connection refused"
date: 2011-11-18
forum: Networking &amp; Wireless
---

### Post by ivarmedi on 2011-11-18
I recently upgraded a server of mine using apt-get dist-upgrade over an SSH connection. When I did this, I had planned to go to the co-location hall in the near future - in case something went wrong. 

Problem is it did, and the trip got interrupted due to personal reasons.. I can't access the server over SSH, getting immediately the error "Network error: Software caused connection abort". It doesn't even seem to try to connect.

The thing is I still have Subversion access to the server, with an automatic post-commit hook. So I can upload any PHP file of choice to it and access it. I've tried phpshell, but due to it's limitations with su/sudo I haven't really gotten anywhere..

The sshd process is running, so it must have something to do with a firewall or something.. 

I have the root password, of course. And I can sudo -S with php system(), it's just an extremely irritating way to test commands..

Suggestions?

---

