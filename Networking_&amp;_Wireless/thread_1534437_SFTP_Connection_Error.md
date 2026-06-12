---
title: "SFTP Connection Error"
date: 2010-07-19
forum: Networking &amp; Wireless
---

### Post by imgrumpy on 2010-07-19
I recently started receiving "SFTP connection error" when I tried to connect from a SFTP client. I was working correctly until a few weeks ago. I am not sure if an update broke my system. I have another system that is pretty much identical even updates, but it has continued to work. I cannot find any helpful info in the logs. Here is a snippet from auth.log:

Jul 19 14:43:48 revproxy sshd[28788]: Accepted password for bdaddy from 10.10.10.100 port 3690 ssh2
Jul 19 14:43:48 revproxy sshd[28788]: pam_unix(sshd:session): session opened for user bdaddy by (uid=0)
Jul 19 14:43:48 revproxy sshd[28796]: subsystem request for sftp
Jul 19 14:43:48 revproxy sshd[28796]: Received disconnect from 10.10.10.100: 11: Session closed ok
Jul 19 14:43:48 revproxy sshd[28788]: pam_unix(sshd:session): session closed for user bdaddy
I am using CoreFTP lite as a client, but I have tried other products as well. SSH is working and I am connecting via putty.
Thanks,
Tommy

---

