---
title: "[SOLVED] Throttle Bandwidth on SSHFS"
date: 2008-12-30
forum: Networking &amp; Wireless
---

### Post by Kissell on 2008-12-30
I have mounted a remote file server over the internet using SSHFS and I have a script that runs a file backup to that remote server for disaster recovery purposes.

However, the internet upstream at this site to be backed up is very slow...  DSL speeds...  and during this transfer the internet comes to a crawl for the handful of computer users at that site.  It is normally not a problem, except when a new large file needs backed up, then sometimes the backup spills over into the morning when they come in for work.

Right now, it's just doing a file copy, and using as much bandwidth as it wants...  I want to be able to limit the bandwidth for that copy process...  to ensure I leave 5KB/sec or so unused in case someone needs to use internet web browsing and not complain about it being slow.

Any ideas on what would be best for me to use?

---

### Post by mpokrywka on 2008-12-30
You can use traffic control on your computer (that mounts sshfs) - simple rules that limit upload to server ip and port 22 should suffice.
Something like:
```

DEV=eth0
DEV_MAX=100Mbit
SSH_UPLOAD=220kbit
SERVER_IP=1.2.3.4/32
SERVER_PORT=22
tc qdisc del dev $DEV root
tc qdisc add dev $DEV root handle 1: htb default 10
tc class add dev $DEV parent 1: classid 1:5 htb rate $DEV_MAX
tc class add dev $DEV parent 1:5 classid 1:10 htb rate 128kbit ceil $DEV_MAX
tc class add dev $DEV parent 1:5 classid 1:20 htb rate 128kbit ceil $SSH_UPLOAD
tc qdisc add dev $DEV parent 1:10 handle 10: sfq
tc qdisc add dev $DEV parent 1:20 handle 20: sfq
tc filter add dev $DEV parent 1: protocol ip prio 5 \
  u32 match ip dst $SERVER_IP \
      match ip dport $SERVER_PORT 0xffff classid 1:20 

```

---

### Post by Kissell on 2008-12-31
Cool, thanks!

I didn't know about traffic control, I looked for it in the repositories, but turns out its already installed natively as command "tc".

Your script appears to have worked for me...  

although, 1) I couldn't use a hostname, had to give it the IP...  and 2) I have no idea if its really working, i'll have to go test it... cause those commands aren't human intuitive, at least not to me...  it'd be nice in this case if there were a simple bandwidth limiter GUI that did these commands for you...  although, assuming the script worked, this will solve my problem.  Thanks!

---

### Post by Kissell on 2008-12-31
That script for tc is so useful!!

I had another problem where long sustained samba file transfers to an encrypted file server were causing the server to become very slow and unresponssive at times, because the processor couldn't keep up with the demands of the encryption.  

The system monitor was telling me network traffic was at around 40MB/sec on the box during the transfer, so I used the script you gave me, and limited port 445  (microsoft-ds) to 163840 (20MB/sec), and instantly after executing the script on the sending computer, it dropped the transfer rate...  limiting it, and causing the CPU to work less (less files to write and encrypt during the same duration of time).  This bandwidth limitation on port 445 limited samba to slow disk writes and encryption, to free up CPU usage to make the server bearable to use while the file transfer was going on.  very cool..  still wish tc was a little more human friendly, but this script works great!

---

