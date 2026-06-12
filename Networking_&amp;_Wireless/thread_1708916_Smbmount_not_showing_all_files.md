---
title: "Smbmount not showing all files"
date: 2011-03-17
forum: Networking &amp; Wireless
---

### Post by joaopcrodrigues on 2011-03-17
I have a Ubuntu 10.10 all updated on a Quad core with 4gbs of Ram.

Accessing by ssh to a server (2.6.11-gentoo-r6 i686 Intel(R) Xeon(TM) CPU 3.20GHz) I have 30 folders with 771 mpeg files each folder.
```
server$ output #  ls 004 |wc -l
771
```

Accessing and mounting by Places -> Connect to server... I can see my 30 folders with all respective files.

If I mount it with terminal using smbmount, it mounts correctly, 
```
sudo mount -t smbfs //server/output mountfolder/ -o user=xxx,domain=xxx,pass=xxx
```
I can see my 30 folders [SIZE="2"]**but can only**[/SIZE] see 107 files in each folder.
```
my_machine/mountfolder$ ls 004 |wc -l
107

```

All files have the same permissions and there are no links.
Could it be cache?
Samba configuration?
Any ideas?

---

### Post by MysticHLE on 2011-03-23
I have a similar error. I didn't try mounting on the terminal, but I can verify that SMB is not showing all the files.

Running Maverick 64 bit on Quad Core with 4GB of RAM as well.

---

