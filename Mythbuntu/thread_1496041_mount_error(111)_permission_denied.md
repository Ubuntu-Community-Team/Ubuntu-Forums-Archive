---
title: "mount error(111) permission denied"
date: 2010-05-28
forum: Mythbuntu
---

### Post by GROwen on 2010-05-28
Hi all,

I'm attempting to connect to an smb share which I've had success doing under Ubuntu 9.10 using this [tutorial]("http://ubuntuforums.org/showthread.php?t=288534")

I've now switched to running Mythbuntu and using exactly the same steps I can't connect to the share. Instead I get;

mount error(111)

Could this be to do with a ports conflict with MythTv?

Thanks in advance for any help anyone can give me with this.

---

### Post by GROwen on 2010-05-28
Hi all,

I'm attempting to connect to an smb share which I've had success doing  under Ubuntu 9.10 using this [tutorial]("http://ubuntuforums.org/showthread.php?t=288534")

I've now switched to running Mythbuntu and using exactly the same steps I  can't connect to the share. Instead I get;

mount error(111)

Could this be to do with a ports conflict with MythTv?

Thanks in advance for any help anyone can give me with this.

---

### Post by cariboo on 2010-05-28
Please don't create multiple threads on the same subject. I have merged your two threads.

---

### Post by GROwen on 2010-05-29
Sorry about that, just wasn't sure if the Mythbuntu or the networking section was more appropriate.

---

### Post by ian dobson on 2010-05-29
HI,

The best thing to do is firstly get the mount working from the terminal prompt with something like:-

mount -t cifs -o  username=USER,password=PASSWORD,rsize=8192,wsize=8192,noatime  //192.168.0.2/Data /mnt/video

and when thats working add the line to your /etc/rc.local.

Regards
Ian Dobson

---

### Post by tgm4883 on 2010-05-29
> **ian dobson said:**
> HI,

The best thing to do is firstly get the mount working from the terminal prompt with something like:-

mount -t cifs -o  username=USER,password=PASSWORD,rsize=8192,wsize=8192,noatime  //192.168.0.2/Data /mnt/video

and when thats working add the line to your /etc/rc.local.

Regards
Ian Dobson

I don't use cifs, so I may be wrong. Ian, there is a space in your wsize=8192. Looks like it might be a forum issue though, you should stick that in code blocks. I imagine it is supposed to be this

```
mount -t cifs -o  username=USER,password=PASSWORD,rsize=8192,wsize=8192,noatime  //192.168.0.2/Data /mnt/video
```

---

### Post by ian dobson on 2010-05-29
> **tgm4883 said:**
> I don't use cifs, so I may be wrong. Ian, there is a space in your wsize=8192. Looks like it might be a forum issue though, you should stick that in code blocks. I imagine it is supposed to be this

```
mount -t cifs -o  username=USER,password=PASSWORD,rsize=8192,wsize=8192,noatime  //192.168.0.2/Data /mnt/video
```

Hi,

That looks like a forum error.I copied the line from my rc.local and only edited the name/password.

Regards
Ian Dobson

---

### Post by GROwen on 2010-05-30
Thanks for your help all, restarted the whole process of adding the share and got it working but have since discovered that the winbind pkg causes Boxee to stop working, which was the reason I was after the share, ha, oh well...

---

