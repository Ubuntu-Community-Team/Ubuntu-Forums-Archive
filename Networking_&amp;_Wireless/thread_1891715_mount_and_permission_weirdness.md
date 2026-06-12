---
title: "mount and permission weirdness"
date: 2011-12-06
forum: Networking &amp; Wireless
---

### Post by gnulab on 2011-12-06
Hi guys,

I'm sharing, and hoping someone could shed a light what actually went wrong with what I had experienced.

I have a NAS, Qnap that is used as a file server. After I had upgraded all the clients from Ubuntu 11.04 to 11.10 by wiping the partition off and installing a clean one, then I encounter problem with mount the network share.

At this point, as far as I know, there are 2 ways to mount a network share. 1) is through /etc/fstab; 2) is by using nautilus.

Using method 1).

Initially I input this entry into /etc/fstab
//192.168.2.100/share1 /home/user/mount/share1 credentials=/home/user/.smbpasswd 0 0

Result is I can see that the Share1 is mounted through nautilus but I cannot create, edit, delete any file. This is definitely not a permission problem, I can assure you.

Using method 2).

Is very easy. However, it turns out that when I try to attach a file through firefox at gmail, I cannot find the mounted network share. Yet, via nautilus, I can create, edit, delete files that reside Share1.


So after some digging and trying various options in /etc/fstab, I came across the option fmask=777,dmask=777. From what I read, those options force the Share1 to adopt local client permission.

That I'm puzzled. Isn't it when one request to read the content of Share1, it is "allowed" through the credentials option? And since the user in the credential is the owner of the directory (and all the files contain within), why do the user still need to explicitly put those options?

---

