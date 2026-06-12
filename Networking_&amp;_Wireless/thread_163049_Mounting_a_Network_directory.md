---
title: "Mounting a Network directory"
date: 2006-04-20
forum: Networking &amp; Wireless
---

### Post by utab on 2006-04-20
Dear all,

I would like to mount a network directory which is used as a pool by all the workers in  my office.

When I type

sudo mount -t smbfs -o username=user,password=passwd //filesrv/pool /home/utab/documents/MECH_POOL/

It is mounted and I can read and write to this shared directory pool. However, when I reboot I have run the same command above to mount that directory to the file system again. How can I mount this file to the system permanently?

Thx in advance.

---

### Post by CameronCalver on 2006-04-20
hey i would like to do that with 2 machines running ubuntu would

sudo mount -t smbfs -o username=user,password=passwd //filesrv/pool /home/utab/documents/MECH_POOL

work with 2 ubuntu computers

---

### Post by Wyrm_1972 on 2006-04-20
See the Wiki here... worked perfectly for me...

[https://wiki.ubuntu.com/SettingUpSamba?highlight=%28samba%29](https://wiki.ubuntu.com/SettingUpSamba?highlight=%28samba%29)

---

