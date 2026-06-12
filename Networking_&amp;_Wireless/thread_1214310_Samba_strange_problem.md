---
title: "Samba strange problem"
date: 2009-07-15
forum: Networking &amp; Wireless
---

### Post by el.demiurgo on 2009-07-15
Hello All,
I've been using Ubuntu for quite some time now.

I have a 9.04 installation with samba that worked ok.

Yesterday I've installed openssh server and it seems that somehow all shared folders seem to "unshare" randomly.

For example, if you refresh 5 or 6 times de explorer window a new share goes unshared.....

I uninstalled openssh server to no effect.

Could you help me?

Thank you!

---

### Post by dmizer on 2009-07-16
What did you do in order to share folders?

Please post your current /etc/samba/smb.conf file.

---

### Post by el.demiurgo on 2009-07-16
Hi dmizer,
To share a folder I just right clicked on the folder and create a share. Of course I've had to modify the smb.conf.

The only modification is this line: "usershare owner only = false"

The funny thing is that I've been using ubuntu since 2006 this way and only after I've played with OPEN SSh and VNC the system went wrong.

Thank you for your help.

---

### Post by dmizer on 2009-07-16
I always add ssh to all of my systems. It's one of the first things I do, so I doubt that has anything to do with your problem.

Please post the output of:
```
sudo iptables -L
```

---

