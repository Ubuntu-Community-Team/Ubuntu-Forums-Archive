---
title: "Samba, Authentication shares against AD groups"
date: 2010-01-25
forum: Networking &amp; Wireless
---

### Post by jld1989 on 2010-01-25
I have configured a samba server on ubuntu 9.10 to the point where I can log in with an AD account and from a remote machine connect to a share and have it authenticate an individual AD user to the share. I need to be able to authenticate an AD group to the share. The resources I have looked over suggest creating a unix group, adding the AD users to the group in the /etc/group file, then running a command to map the AD group to the unix group and setting the valid users parameter equal to @group with group being the unix group. I have gone through this process with no results. Whether I am just overlooking something or the process is wrong I am not sure. Is there anyone out there familiar with the topic that is able to give step by step instructions to accomplish this?

---

### Post by jld1989 on 2010-01-28
Bump

---

