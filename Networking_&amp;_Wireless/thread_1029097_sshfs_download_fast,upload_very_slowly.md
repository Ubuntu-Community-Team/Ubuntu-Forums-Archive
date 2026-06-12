---
title: "sshfs download fast,upload very slowly?"
date: 2009-01-03
forum: Networking &amp; Wireless
---

### Post by tony755 on 2009-01-03
i have 2 machines

one is client (ubuntu 8.04 desktop),other is server (ubuntu 8.04 server)

both have 1000mbs nic,i make them link by wire directly(no ruter no switch).

i use "sshfs" mount the server "/" from cilent 

my command is
"sudo sshfs username@ipadrees:/ /mnt/remote -o sshfs_sync -o default_permissions,allow_other,kernel_cache,hard_remove
"

when i copy files from server to client ,its speeds 50MB/s

but i copy files from client to server ,its only 6~7MB/s

why?

and can i  configure the sshfs speed? 

in server iptables rule,i accpet the 22.23 port input
in client iptables rule,i doesn't accpet ssh ports input

---

### Post by tony755 on 2009-01-03
but i use "scp" copy files from client to server ,its speed fast ,too

i think the fuse/sshfs have a problem

---

### Post by tony755 on 2009-01-03
anybody help me?

---

