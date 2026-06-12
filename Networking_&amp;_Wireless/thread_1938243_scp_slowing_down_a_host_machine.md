---
title: "scp slowing down a host machine"
date: 2012-03-09
forum: Networking &amp; Wireless
---

### Post by josir on 2012-03-09
Hi folks,

Frequently, I need to copy a huge file (8Gb) between 2 machines but during the copy, the host machine became very slow and other users complained about it.

I tried to use

[INDENT][FONT="Lucida Console"]  nice -n 19 scp backup.tar.gz oracle@192.168.0.12:/mnt/disco2[/FONT][/INDENT]

but machine became slow anyway. 

Does somebody has any suggestion on how to slow down the copy ?

---

### Post by Jon Monreal on 2012-03-09
By all indications, [performance with scp is awful]("http://www.spikelab.org/transfer-largedata-scp-tarssh-tarnc-compared/") for large files to begin with.

With rsync, you can use the perameter --bwlimit= with an amount in KBPS to limit the speed. I'm not sure if this might help.

---

### Post by gmargo on 2012-03-09
According to the fine man page, there is also a bandwidth limiting option for **scp**:
> 
     -l limit
             Limits the used bandwidth, specified in Kbit/s.
Although I personally prefer **rsync** because it can be interrupted and restarted without losing data already transfered, unlike **scp**.

---

### Post by codemaniac on 2012-03-09
+1 for rsync .. :)

---

