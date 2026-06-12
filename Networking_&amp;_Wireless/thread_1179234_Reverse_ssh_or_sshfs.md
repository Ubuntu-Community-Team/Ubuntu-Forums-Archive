---
title: "Reverse ssh or sshfs"
date: 2009-06-05
forum: Networking &amp; Wireless
---

### Post by MoleStrangler on 2009-06-05
Hi all,

I can connect to my MacPro from my office with ssh and sshfs just nicely.  Everything works just as it should because I have configured my wireless router to do the necessary port forwarding etc...

But can I ride the ssh tunnel from my MacPro back into my ubuntu box at my desk?

The tunnel is already connected from my office so all the information is there and the firewall at work has allowed the connection.  But can I ride the tunnel back so I can sshfs and mount volumes?

I cannot do a ssh into work from my MacPro cuz of the firewall, and my ubuntu box dns entry points to our router and not the ubuntu box.

Any ideas.

---

### Post by Brandon Williams on 2009-06-05
The -R flag can be used to open a reverse tunnel over which remote users can connect back to the machine/network that is running ssh. So, if you have sshd running on both sides, host1 and host2, you can run ssh on host1 like this: 'ssh -R2222:localhost:22 host2'. This will allows users on host2 to run 'ssh -p 2222 localhost' in order to get an ssh connect back through the tunnel to host1.

View 'man ssh' and look for the description of the -R flag to get more information.

---

### Post by MoleStrangler on 2009-06-05
Thanks!

---

