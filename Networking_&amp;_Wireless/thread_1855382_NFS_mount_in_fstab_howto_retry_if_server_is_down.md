---
title: "NFS mount in fstab: howto retry if server is down"
date: 2011-10-06
forum: Networking &amp; Wireless
---

### Post by brickZA on 2011-10-06
Hi,

When cold starting an sever and its clients, it seems that the clients don't retry the mount if the server is still down (or the nfs server process has not started yet) when they boot. In the client fstab I have:

server:/var/kat/katstore /mnt/katstore nfs size=8192,wsize=8192,timeo=14,intr,bg

I added the 'bg' option in the hope that it would continue re-trying after the initial mount failed, but it never seems to get mounted.

If the server is ready before the client boots, the client does the mount with no problems.

Both the server and the client are running Ubuntu 10.04.2 LTS

How can I get the client to continue re-trying the mount until the server is ready?

Thanks
Neilen

---

### Post by Noldoaran on 2011-10-08
bump. 
I would like to know the answer to this question also. 
I have a desktop and a laptop running Ubuntu 11.04.

---

### Post by brickZA on 2011-10-14
Just an update. Someone suggested I specify a value for the 'retry'option, so I tried adding 'retry=1000' to the options. Since the default value of retry is already 10000, it did not make any difference as one would expect.

---

### Post by brickZA on 2011-10-14
Well, it seems, as far as I can tell, that just about every linux distribution out there is fundamentally broken w.r.t. handling boot time nfs mounts :)  

In any case, a work around is presented in [https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/836533/](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/836533/) I skipped the upstart bit, and just made my /etc/rc.local call the ensure-nfs-mounted script attached to that issue.

---

