---
title: "sshfs for cellphone"
date: 2009-06-30
forum: Networking &amp; Wireless
---

### Post by mightyiam on 2009-06-30
Dear friends,

I'm looking for software that will allow me to mount ssh on a cell phone!

I haven't found anything like this, though.

Does anyone know anything, please?

---

### Post by jhannah on 2009-06-30
I'm assuming you are using your cellphone as the modem to connect you to the internet, not as the actual platform you wish to mount or have mounted, is that correct? If so, sshfs is probably the best option but I would recommend you enable compression using the '-C' flag (if your using the sshfs binary to mount the file system) or '-o compression=yes' if you are using mount/fstab. NFS might also be a suitable option but it is a little more complicated to get setup. If you wish to go that route, [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo) should point you in the right direction.

---

### Post by mightyiam on 2009-07-01
> **jhannah said:**
> I'm assuming you are using your cellphone as the modem to connect you to the internet, not as the actual platform you wish to mount or have mounted, is that correct?

Dear jhannah,

Nope - It is indeed my intension to mount via ssh *on* the cell phone itself.

Many blessings.

---

