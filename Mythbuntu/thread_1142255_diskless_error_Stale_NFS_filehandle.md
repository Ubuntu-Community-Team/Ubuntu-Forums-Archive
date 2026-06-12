---
title: "diskless error Stale NFS filehandle"
date: 2009-04-29
forum: Mythbuntu
---

### Post by map7 on 2009-04-29
I'm using mythbuntu 8.10 and when I create a diskless build image and try and boot off it using a PXE thin client I get the error message:

mount call failed: 13
mount: Mounting /cow/002354c1f378 on /root/cow failed: Invalid argument
run-init: overmounting root: Stale NFS filehandle
[   9.550831] Kernel panic - not syncing: Attempted to kill init!

How do I remove a Stale NFS filehandle for a PXE client?

---

### Post by map7 on 2009-05-06
$ sudo dpkg-reconfigure mythbuntu-diskless-server
Answer 'yes'
enter 192.168.1.0/24 (what ever your IP is)

I have to do this if the server crashes.

---

### Post by walterdf00 on 2009-05-25
Thanks, map7!  This got me over the last hump to finally seeing X on my PXE client.

---

