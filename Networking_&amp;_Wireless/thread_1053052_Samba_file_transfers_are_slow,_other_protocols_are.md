---
title: "Samba file transfers are slow, other protocols are not"
date: 2009-01-28
forum: Networking &amp; Wireless
---

### Post by jcantara on 2009-01-28
I'm having a problem with file transfers over samba. I've done some research and found that it seems a lot of people are having the issue, but there are very few solutions.

Here's the description:
I have a very simple samba share set up on the Ubuntu server (8.10). Accessing this share from any shape and variety of other machine (Windows XP, MacOS, a different Ubuntu machine) is slow, as in files take forever to transfer, I get approximately 200 Kbit per second. 

Accessing the exact same file via any other means from any of the above other machines (sftp, nfs) is quite fast, about 50 Mbit per second. 

Some of the explanations I have read say to look at:
1) The filesystem, EXT3. I am certain it isn't this, because the file transfers are fast through all other protocols, and the speed of the disks on the local filesystem (moving from disk to disk) is plenty fast. 

2) The network setup. I have an extremely simple setup. One gigabit switch, one client, one server, all wired. Client has gigabit networking hardware, server has 100 megabit hardware. 

3) Many people point to the networking drivers/module used, and have successfully solved the problem by either replacing the network card, or using a different kernel module. Every case I have seen involves Realtek networking. In my server setup, I am using the onboard NIC, and there is only one PCI slot (Mini-ITX board) which is occupied by the SATA controller card, so I cannot try a replacement NIC. The onboard nic is listed by lspci as:
```
VIA Technologies, Inc. VT6102 [Rhine-II] (rev 51)
```
and the modules loaded:
```
via_rhine              30216  0
mii                    13440  1 via_rhine
```
I have seen one or two similar complaints with the Rhine card, rather than the Realtek one, but far far less. I also don't see any options for alternative modules to use for the rhine card... It appears that I am using the one-and-only available module. 

4) Samba conf file. I am using the supplied smb.conf only with changes to the shares (just one simple share, so I can isolate things while testing). 

5) Log files. The only strange thing I'm seeing in the log files is:
```
[2009/01/28 10:46:37,  1] winbindd/idmap_tdb.c:idmap_tdb_alloc_init(371)
  idmap uid range missing or invalid
  idmap will be unable to map foreign SIDs
[2009/01/28 10:46:37,  0] winbindd/idmap.c:idmap_alloc_init(831)
  ERROR: Initialization failed for alloc backend, deferred!
```
in the file /var/log/samba/log.winbindd-idmap. It repeats a couple times a minute; but after looking it up online I believe it has to do with authentication and not speed issues. All of the other log files just show normal access notes and such.

So, I'm very stuck at the moment. I don't know what I should try, or if I can try anything. 

Any advice would be hugely appreciated. I realize this issue has been posted about before, but any solutions provided before do not seem to apply to my setup.

Thanks,
-Jesse

---

### Post by Saghaulor on 2009-01-28
My brother seems to be having a similar problem when transferring files to his Vista desktop from his Ubuntu netbook.

---

