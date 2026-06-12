---
title: "Strage mounting issues"
date: 2009-09-02
forum: Networking &amp; Wireless
---

### Post by sa125 on 2009-09-02
Hi - I'm mounting a network drive on two machines (w/ exportfs). One is a 64-bit server running Intrepid, and the other is a 64-bit desktop station running Jaunty. The mounted folder sits on a 64-bit server running Dapper (I think).

I found that on occasion, the Intrepid server is not showing some of the files that I can see on the desktop and the host server. Re-mounting the folder doesn't seem to help, and I'm using the same configuration for both machines when mounting:

the /etc/exports file on the Dapper server has the following:
```

# the 64-bit server
/files/logs 10.60.10.14(rw,rw,no_root_squash,async)
# the desktop machine
/files/logs 172.30.22.12(rw,rw,no_root_squash,async)

```

All machines are on an intranet. This doesn't happen to all files, and I can't isolate the difference between the ones that show and the others that don't. I looked into file permissions (all have 544) and file sizes (all around 50-500 kb).

Any clue why this happens and how to solve this?

---

### Post by sa125 on 2009-09-03
It seems to be some FS indexing issue. The particular folder with the invisible files is pretty crowded (30k+ files), so perhaps that's what is weighing it down.

Since I'm scanning that folder using a script (python), I resorted to a temporary solution of "touching" a file in that folder that seems to refresh the index and reveal the missing items. So for now, this works. If anyone knows of another way to approach the problem, I'd be glad to hear about it.

---

