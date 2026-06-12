---
title: "I'm Afraid I Gorked My Network"
date: 2012-03-24
forum: Networking &amp; Wireless
---

### Post by PipeBoss on 2012-03-24
Please Delete Thread

---

### Post by agillator on 2012-03-24
You mention that both computers are running Ubuntu 10.04, but the methods you are using sound like windows based procedures. I think the easiest way to connect the two over a network is by mounting each directory on the other computer in Linux. I have never seen Windows shares work smoothly, even in Windows much less in Linux. Assume for the moment computer #1 has an ip address of 192.168.1.1 and the directory is /home/sam/dir1; computer #2 has an ip address of 192.168.1.2 and the directory is /home/fred/dir2. On computer 1 create a mount point (destination directory) for the computer 2 directory, say /mnt/computer2. In /etc/fstab add a line '//192.168.1.2/home/fred/dir2 <tab> /mnt/computer2 <tab> <fs type> <tab> defaults <tab> 0 <space> 0'. The <fs type> is the file system type of the directory on computer 2: probably ext3 or ext4 if linux, cifs if windows (FAT of some type or NTFS). The <tab> may be a <space> and vice versa. Now 'sudo mount /mnt/computer2' will mount the directory onto computer 1. When you have that working, make a similar entry in computer 2's fstab to mount computer 1's directory. That should do it. And, as a side note, when the computers are rebooted the mounts should happen automatically.

---

### Post by PipeBoss on 2012-03-24
Thank you very much for that reply.  You must've been typing it while I was editing my post.  I did finally get it figured out - it was a stupid firewall issue, now corrected.  I did copy/paste your reply in a document and will take that under advisement - it would be much more convenient to have them mounted like that.  

Thank you for the reply!

---

### Post by agillator on 2012-03-24
You are right, I was typing when you edited. Doesn't matter, as long as your problem is solved to your satisfaction. Please do mark the thread 'SOLVED' in that case.

---

