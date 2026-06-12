---
title: "[SOLVED] Fritzed my user group membership's"
date: 2008-07-01
forum: Mythbuntu
---

### Post by sikk on 2008-07-01
Hello,

It appears I have managed to fry at least my mythbuntu box's "admin" group memberships. The user (user123) which my host (mythtv) uses to login and consequently run mythtv does not appear to be a member of any groups other than mythtv.

The lack of "admin" ,membership means I cannot run sudo to further troubleshoot my issues. I have a way around this....

[http://ubuntuforums.org/showthread.php?t=136097](http://ubuntuforums.org/showthread.php?t=136097)

Could someone run a "id" on the user that they use to login and post the groups that user is a member of so I can double check other groups are not fried?

Thanks in advance.

---

### Post by sisco311 on 2008-07-01
Reboot in recovery mode:
```
usermod -a -G adm,dialout,cdrom,floppy,audio,dip,video,plugdev,fuse,lpadmin,admin,YOURUSERNAME YOURUSERNAME
init 2
```

---

### Post by sikk on 2008-07-01
Sisco,

Thankyou very much. That sorted me out. 

One of the problems I was troubleshooting was the lack of audio on boot (worked once I got sudo running, so I could run mythfrontend with a "sudo mythfrontend", before you posted). This has resolved that issue for me.

Solved.

---

