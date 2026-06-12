---
title: "Jaunty and SSHFS"
date: 2009-05-19
forum: Networking &amp; Wireless
---

### Post by afkaos on 2009-05-19
I'm having some issues with SSHFS on Jaunty. 

I'll execute the following command:
'sshfs user@server:directory directory'
It will ask me for the password to the server, and then hang there doing nothing after I enter it.

This guide didn't work:
[https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS) 

And most other guides include a line to do 'sudo modprobe fuse' which results in a FATAL: Module fuse not found.

I was wondering if anyone else has had this problem and if there is a fix? Much appreciated.

---

