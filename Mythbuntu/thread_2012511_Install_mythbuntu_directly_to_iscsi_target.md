---
title: "Install mythbuntu directly to iscsi target"
date: 2012-06-29
forum: Mythbuntu
---

### Post by natomb on 2012-06-29
Hi,

does anyone has experience installing mythbuntu directly onto iscsi target? I think current mythbuntu iso (12.04) does not provide iscsi support. Thus, I tried to come around with Ubuntu 12.04 server and install myth-control-centre. However, when doing so the control centre does not work, i.e. icons are missing, buttons have no effect, etc.

Unfortunately I do not have a spare harddisk to install onto and then transfer onto the iscsi target.

Thanks for support
  Bjoern

---

### Post by tgm4883 on 2012-06-29
> **natomb said:**
> Hi,

does anyone has experience installing mythbuntu directly onto iscsi target? I think current mythbuntu iso (12.04) does not provide iscsi support. Thus, I tried to come around with Ubuntu 12.04 server and install myth-control-centre. However, when doing so the control centre does not work, i.e. icons are missing, buttons have no effect, etc.

Unfortunately I do not have a spare harddisk to install onto and then transfer onto the iscsi target.

Thanks for support
  Bjoern

There shouldn't be any icons missing if you install MCC onto Ubuntu server, if there is, then you need to file a bug so we can fix it.

---

### Post by natomb on 2012-08-20
I solved the problem by installing mythbuntu onto Ubuntu Server via:

```
sudo apt-get install mythbuntu-desktop
```

Now everything is fine (except that I have to adjust the satellite dish :p )

---

