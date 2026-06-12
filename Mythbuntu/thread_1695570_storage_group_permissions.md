---
title: "storage group permissions"
date: 2011-02-26
forum: Mythbuntu
---

### Post by sdredwingsfan on 2011-02-26
So I have a Openfiler NAS that I'm using for my storage group (cifs) on my mythbuntu I've created a user account by name and uid and mounted it, added it as a storage group and matched up to a mythbuntu user but I'm not getting rw permissions on the share.  I'm sure this is somewhat petty but ownership and rw privleges are failing.  Even when I add the storage group, it says it can not create a temp file to test rw permissions.  

On Openfiler i have:
membership = gp uid 500 (primary group with rw permissions)
home network subnet has rw smb/cifs permissions

On Mythbuntu fstab i have:
//openfiler/media     /home/xx/mnt/   cifs  rw,d_mode=777,f_mode=777,credentials=/home/xx/.credentials

Additionally, should other myth frontends just show all storage groups that the master backend has?  Or should the frontends automatically show storage groups from the backend?  Basically i'm referencing a directory structure of iso's on my nas that was a linuxmce media content.

Mythbuntu 10.04
Openfiler Kernel Version	2.6.26.8-1.0.11.smp.pae.gcc3.4.x86.i686 (SMP) (usb bootup)

---

### Post by tgm4883 on 2011-02-26
> **sdredwingsfan said:**
> So I have a Openfiler NAS that I'm using for my storage group (cifs) on my mythbuntu I've created a user account by name and uid and mounted it, added it as a storage group and matched up to a mythbuntu user but I'm not getting rw permissions on the share.  I'm sure this is somewhat petty but ownership and rw privleges are failing.  Even when I add the storage group, it says it can not create a temp file to test rw permissions.  

On Openfiler i have:
membership = gp uid 500 (primary group with rw permissions)
home network subnet has rw smb/cifs permissions

On Mythbuntu fstab i have:
//openfiler/media     /home/xx/mnt/   cifs  rw,d_mode=777,f_mode=777,credentials=/home/xx/.credentials


Don't put the mount in a home directory. MythTV usually doesn't like that and thats why it may be complaining.

> **sdredwingsfan said:**
> 
**Additionally, should other myth frontends just show all storage groups that the master backend has?  Or should the frontends automatically show storage groups from the backend?**  Basically i'm referencing a directory structure of iso's on my nas that was a linuxmce media content.

Mythbuntu 10.04
Openfiler Kernel Version	2.6.26.8-1.0.11.smp.pae.gcc3.4.x86.i686 (SMP) (usb bootup)

Can you rephrase the bolded section. It may just be because I just woke up, but I've read that 4 times and it looks like both sentences mean the same thing and I don't know what your asking.

---

### Post by sdredwingsfan on 2011-02-26
sorry, my basic question was if i correctly configure the videos storage group on the backend will the frontends automatically see the stored videos?  thanks!

---

### Post by tgm4883 on 2011-02-26
> **sdredwingsfan said:**
> sorry, my basic question was if i correctly configure the videos storage group on the backend will the frontends automatically see the stored videos?  thanks!

Yes this is the case

---

