---
title: "Slow NFS (hangs when writing), but OK with CIFS, SSH, Netcat"
date: 2013-04-03
forum: Networking &amp; Wireless
---

### Post by Sitron_NO on 2013-04-03
I had this problem on my server (10.04 LTS) and now after upgrading (12.04 LTS), with 12.04 as clients. I mount directories via NFS4, and while reading files is no problem and has almost the same speed as ssh/scp and cifs, writing to the NFS-directory is troublesome:
- It stars out with great speed (faster-than-network), but then goes to "normal" speed. After some seconds, it halts completely (0kbps).
- While this hangs, Firefox, Thunderbird and other programs is none-responsive. However, existing terminals (Gnome terminal) works without problems, also the ones logged on the NFS-server.
- Network connection to the NFS-server is not lost, a continuous ping is acting normal, good responsetimes and no packet-loss.
- After about 30-60 seconds of hang, the write-speed normalizes, Firefox and Thunderbird is responsive, and everything is fine... for about 30 seconds. Then a new hang, and so on...

While this hang is happening, the load on the client goes up, but the server has no problems at all (as far as I can tell). I have tested this on two different clients, wireless and wired connections, and a various of network-speeds. No differences, except the length of hangs.

However, trying to copy files via CIFS, ssh (scp) and/or netcat does not have this problem. The transfer-rate is a bit higher than with NFS, but that does not bother me. But that a NFS write makes my client just hang and become totally unresponsive is a major problem!


```
/etc/exports:
/opt/exports/nfs        192.168.10.10/32(rw,fsid=0,no_root_squash,insecure,no_subtree_check) 192.168.10.14/32(rw,fsid=0,no_root_squash,insecure,no_subtree_check)
/opt/exports/nfs/home        192.168.10.10/32(rw,no_root_squash,insecure,no_subtree_check,sync) 192.168.10.14/32(rw,no_root_squash,insecure,no_subtree_check,sync)
/opt/exports/nfs/public        192.168.10.10/32(rw,all_squash,insecure,subtree_check,sync,anonuid=150,anongid=100) 192.168.10.14/32(rw,all_squash,insecure,subtree_check,sync,anonuid=150,anongid=100)
```
(I have tried both async and sync - No difference)

Does anyone know what the problem can be? Or any ideas how to debug?

---

### Post by SeijiSensei on 2013-04-03
Try adding "async" to the options for the server in /etc/exports.  This can lead to data loss if the server were to suddenly fail but is otherwise quite safe.  I have my server connected to an uninterruptible power supply to protect against brownouts and blackouts.

Sorry, I missed the part about trying async.  That has always solved this problem for me.  The behavior you describe is symptomatic of issues with sync, too.

What if you put each declaration in /etc/exports on a single line?  Or, unless you really have to limit access by specific host IP and not a subnet, use a single "192.168.10.0/24" entry instead?

On the client, how big are rsize and wsize set to?  I use 32768 on 100 MBbit or wifi.

---

### Post by Sitron_NO on 2013-04-03
Well, after a full set of tests, I discovered that my test was flawed! :-(

This command, which I believed to be a OK test, was indeed not a very good test, and just made the clients (all of them) hang:
```
cat /dev/zero | pv > /mnt/public/tmp/zero.data
```

However, this was a much better test:
```
dd if=/dev/urandom of=random.data bs=1M count=512
pv random.data > /mnt/public/tmp/random.data
```

When running the above command, it would write all data at once, with faster-then-network speed, and then just do nothing.. But in reality is saw the file grew on the server until it was done and the command (pv) exited normally.

---

