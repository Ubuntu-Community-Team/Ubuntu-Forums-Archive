---
title: "Mounting a Windows share (password protected) in fstab"
date: 2009-11-17
forum: Networking &amp; Wireless
---

### Post by mattlindsay on 2009-11-17
Dear all,

As a "starter" linux user, I'm struggling to get my system to mount a windows share at logon. I think I'm close because it mounts it, but it doesn't give me RW access unless I "open as root".

I don't think I'm all that far from the solution, but it's driving me mad... can anyone help?

The line I have is:

```
//myserver/users/matt /media/matt  cifs rw,noauto,user,sync 0  0
```

Can I add in my Windows user logon credentials in this line so it logs me on with Read/Write priviledges?

Many thanks in advance

Matt

---

### Post by mattlindsay on 2009-11-18
Good news! I think I fixed it.

For future users I used:

```

//jenna/users/matt /media/matt cifs auto,username=MyUsername,password=MyPassword,workgroup=MyWorkgroup,gid=MyUsername,uid=MyUsername,rw       0       0
```

Hope that helps someone.

---

### Post by sleeeves on 2009-11-18
> **mattlindsay said:**
> Good news! I think I fixed it.

For future users I used:

```

//jenna/users/matt /media/matt cifs auto,username=MyUsername,password=MyPassword,workgroup=MyWorkgroup,gid=MyUsername,uid=MyUsername,rw       0       0
```

Hope that helps someone.


Thanks for this, it works great!  I've been using a similar line in my fstab (//server/r$ /media/r-server cifs user=user,password=password,rw 0 0), but it was always rather hit or miss.  The syntax you used works perfect!  MUCH simpler than all the other crazy "fixes" out there.  Thanks again!

---

### Post by eklikeroomys on 2011-09-26
Awesome! Instant fix! Thank you

---

### Post by TechMeOutTV on 2013-01-10
This is actually not working for me... it mounts just fine but when i try "touch test" i still get permission denied. 

:(

---

### Post by eklikeroomys on 2013-01-11
Hi TechMeOutTV,

The following works for me in Ubuntu 12.04:

```
//<SHARE_IP_ADDRESS>/share /mnt/Share cifs domain=<WORKGROUP>,username=<WORKGROUP/USERNAME>,password=<PWD>,rw,uid=<USERNAME> 0 0
```

The above line should be placed in your /etc/fstab file. You are free to change the location of the mount point (/mnt/Share in example above), just ensure that the mount point exists.
Replace the following data:

<SHARE_IP_ADDRESS> is the IP address of your windows share.
<WORKGROUP> is the workgroup of your windows share.
Note that the username is specified as WORKGROUP/USERNAME (eg. workgroup/chris).

Hope this helps.:popcorn:

---

