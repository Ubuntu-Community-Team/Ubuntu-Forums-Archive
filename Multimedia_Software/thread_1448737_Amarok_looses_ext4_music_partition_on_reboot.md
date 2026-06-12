---
title: "Amarok looses ext4 music partition on reboot"
date: 2010-04-07
forum: Multimedia Software
---

### Post by houserparker on 2010-04-07
I have just switched to Kubuntu from Ubuntu after about a year or so.

Every time I reboot Amarok looses the location of my ext4 music partition and I have to manually add it again.

when I use the command

```
 ls /etc/sta2 
```

It returns "cannot access: no such file or directory" which as far as i know means that the partition is already open and I can see the partition inside Dolphin just after it boots.

Can anyone help?

---

### Post by houserparker on 2010-04-07
> **houserparker said:**
> I have just switched to Kubuntu from Ubuntu after about a year or so.

Every time I reboot Amarok looses the location of my ext4 music partition and I have to manually add it again.

when I use the command

```
 ls /etc/sta2 
```

It returns "cannot access: no such file or directory" which as far as i know means that the partition is already open and I can see the partition inside Dolphin just after it boots.

Can anyone help?
Anyone have any ideas?

---

### Post by houserparker on 2010-04-07
Problem solved. Worked out that I needed to add the following line to fstab

/dev/sda2 /media/Data ext4 defaults 0 2

---

