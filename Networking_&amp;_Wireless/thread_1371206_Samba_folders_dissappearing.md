---
title: "Samba folders dissappearing"
date: 2010-01-03
forum: Networking &amp; Wireless
---

### Post by caleb2003 on 2010-01-03
Hi I keep having failures with samba mainly that each day the /var/run/samba folder seems to dissapear so Samba doesn't start, normally I can just add the folder back and samba will start and work ok but today it fails.

Does anyone know why this folder may just dissapear and if there is something I can do to get Samba working?

Thanks

---

### Post by dmizer on 2010-01-03
> **caleb2003 said:**
> Hi I keep having failures with samba mainly that each day the /var/run/samba folder seems to dissapear so Samba doesn't start, normally I can just add the folder back and samba will start and work ok but today it fails.

Does anyone know why this folder may just dissapear and if there is something I can do to get Samba working?

Thanks

Exactly what folder disappears, from where, and exactly how do you add it back in?

Include screenshots if necessary. :)

---

### Post by caleb2003 on 2010-01-03
> **dmizer said:**
> Exactly what folder disappears, from where, and exactly how do you add it back in?

Include screenshots if necessary. :)


Hi, the /var/run/samba folder  is the one that dissapears I attached a screenshot of what i then did here [http://yfrog.com/18screenshot1rip](http://yfrog.com/18screenshot1rip)    I added the folder back but starting samba just fails.

---

### Post by caleb2003 on 2010-01-03
Also I need to add that in var/log/samba there is nothing in the samba log file since 13/12/09 even though I used samba only 3 days ago (I mainly shgare to an original xbox)
the log.winbindd and log.smbd are there though  the log.nmbd for instance has this in:
[2010/01/03 20:24:42,  0] nmbd/nmbd_become_lmb.c:395(become_local_master_stage2)
  *****
  
  Samba name server MAINPCLINUX is now a local master browser for workgroup MSHOME on subnet 192.168.0.4
  
  *****
[2010/01/04 00:57:27,  0] nmbd/nmbd.c:71(terminate)
  Got SIGTERM: going down...

---

### Post by caleb2003 on 2010-01-09
Did a full reinstall of samba and it worked great but once again after reboot something has deleted my /var/run/samba folder, Anyone got any ideas?

Please!

---

### Post by dmizer on 2010-01-09
I am still not sure what your problem could be, or could be related to.

[s]Please post your /etc/samba/smb.conf file.[/s]

Edit:
No ...

You need to start the samba server with root permissions. Try this instead:
```
[COLOR="Red"]sudo[/COLOR] /etc/init.d/samba start
```

---

### Post by caleb2003 on 2010-01-09
Hi, thanks that does indeed start samba succesfully and I can see the shares from other PCs although there is one share I cannot see and maybe it is this that is the problem.
My pc is partitioned with Windows and Ubuntu and I am sharing a folder from the windows partition via Ubuntu but this has actually stopped sharing this particular folder as well and it also has done it this time too. 

It seems to be related to this but I don't know why?

---

### Post by dmizer on 2010-01-09
> **caleb2003 said:**
> 
It seems to be related to this but I don't know why?

Yes, this is related. Here is a thread in which that issue was resolved. It includes directions on how the problem was resolved as well: [http://ubuntuforums.org/showthread.php?t=1367919](http://ubuntuforums.org/showthread.php?t=1367919)

---

