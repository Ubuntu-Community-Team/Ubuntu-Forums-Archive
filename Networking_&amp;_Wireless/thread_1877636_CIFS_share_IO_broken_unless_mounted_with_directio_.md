---
title: "CIFS share IO broken unless mounted with directio enabled"
date: 2011-11-08
forum: Networking &amp; Wireless
---

### Post by hitausmomentti on 2011-11-08
I updated from Maverick to Oneiric by doing a complete reinstall, after which I've been unable to use remote CIFS shares properly. They always mount without any errors, but all write operations either silently corrupt data or complain about "Input / Output Error". Timestamps of open files are sometimes set to the Unix epoch. There's nothing in dmesg or the logs on the server. The shares work fine using a different computer that has Ubuntu 10.10 installed. 

I tried various combinations of different options, and the only one that made any difference was directio, which made writing on the shares possible. I tried NFS to see if it would be better and it works without breaking anything, but any large transfer causes ~100% iowait load on 2-3 cores, which makes the whole system feel like it's swapping to an old hard drive.

Using directio with CIFS seems to be a reasonable workaround, but I'd like to have my filesystem cache back.

---

### Post by hitausmomentti on 2011-11-14
It seems that even the directio option didn't help all that much The same problems started appearing, it just took a little longer. I also tried another NIC, which also looked like it worked, but the problems just took a little longer to appear. Changing the NIC didn't help with the NFS iowait problem either. Any ideas how this could be fixed?

---

### Post by hitausmomentti on 2011-11-15
Looks like this isn't just an Ubuntu problem, i tried the Fedora LiveCD and the problem was exactly the same in every way. I'll have to try an older kernel next.

---

### Post by hitausmomentti on 2011-11-15
I installed 2.6.35 from the mainline kernel PPA, and it seems to have fixed all my problems. CIFS works the way it's supposed to and NFS seems to be fine too. Has anyone else had similar issues and did you find better solutions to them?

---

### Post by hitausmomentti on 2011-11-22
I should have looked at my traffic with Wireshark earlier. For some reason the client and the server (OpenIndiana 148) negotiate it wrong and use 126976 (or 31 * 4096) bytes, which the server seems to complain about. I seem to be able to use the CIFS mounts at least a bit when I mount them with wsize=57344.

---

### Post by bexamous on 2011-11-26
Huh...  I think I may be running into same issue?  I too happen to be mounting a OpenIndiana share, and no idea how you came up with wsize=57344 but adding that everything appears to work....  no more constant input/output errors copying files.  Something is messed up though.  I have no problems with Windows systems accessing the same shares on OI.

:/

---

### Post by hitausmomentti on 2011-12-11
The default wsize was 57344 before Linux 3.0, according to the mount.cifs man page. I don't know why the hosts negotiate a value they can't use, but forcing it to the old default seems to work. I might dump some traffic between the OI server and Windows and see what wsize they use. I updated the server to OI151, which might do something too. 

Anyway, I get ~2x better performance with NFS, but I have to use an old kernel because NFS has some issues in newer kernels.

---

