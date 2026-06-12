---
title: "FTP Server - Setting default directory per user"
date: 2010-06-21
forum: Networking &amp; Wireless
---

### Post by cj.surrusco on 2010-06-21
I am using VSFTPD as my FTP daemon. I want it to be set up so that my user (cj) will have a default directory of / when I log on to the FTP server and I want the secondary account (guest) to have it's home directory as the default location without any access to the root of the drive.

I need my account to have the default as / because the FTP client that I use in Windows won't go up to the parent directory of the default. Therefore, I cannot access the rest of my drive. 

When I set "local_root" to "/" , it brings both users to the / directory when they sign in, even though the guest account is set to open the home directory with the "chroot_list_enable". It seems like the local_root option overrides the chroot_list_enable option.

Is there any way to set the default directory for each local user separately?

Also, Let me know if this is impossible with this FTP daemon and maybe suggest one that would allow this.

Thanks in advance.

---

### Post by cj.surrusco on 2010-06-22
bump

---

### Post by cj.surrusco on 2010-06-23
What's really happening here is that the "local_root=/" string is overriding the "chroot_list_enable" option.

So, even users that are supposed to be locked in their home directory have access to the root of the drive.

I would really appreciate some help with this.

---

