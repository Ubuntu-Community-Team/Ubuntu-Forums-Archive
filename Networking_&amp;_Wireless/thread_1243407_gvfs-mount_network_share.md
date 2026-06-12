---
title: "gvfs-mount network share"
date: 2009-08-18
forum: Networking &amp; Wireless
---

### Post by 696f6e6963 on 2009-08-18
I am able to mount smb://server/share using

```
gvfs-mount smb://server/share
``` However, I want to mount smb://server/share/$USER and if I do ```
gvfs-mount smb://server/share/john
``` it still only mounts smb://server/share

If I cant mount it directly I am open to suggestions, but I **need **a link to smb://server/share/$USER on everyone's desktop.

---

### Post by dmizer on 2009-08-18
Syntax of a mount is thus:

//server/share

So if you want to mount as $user, then you will have to configure the shares as $user on all the desktops. Then you can mount:
//server/$user

---

### Post by 696f6e6963 on 2009-08-18
I'm not sure I follow. //server/$user does not exist, and changing the directory structure on the server from //server/share/$user to //server/$user not a viable option.

---

### Post by dmizer on 2009-08-18
On the server you don't have to change the directory structure, just the share name. They are not the same thing.

What OS is the server(s) running?

---

### Post by 696f6e6963 on 2009-08-18
Windows 2003. Just to be clear $user is a variable for all our users who login and authenticate with our active directory. Are you saying that I have to share all their directories?

---

### Post by dmizer on 2009-08-18
I'm just trying to get a picture of what your situation is in order to offer a reasonable solution.

The way you worded your first post, it sounded as though you had one Ubuntu computer from which you were attempting to mount multiple shares, where each share was hosted from a different computer.

Also, my experience with AD is limited so I may only be of limited help, but a share mount != directory path. I know of no way to get linux to directly mount a subfolder within a share. That doesn't mean it's not possible, and there are ways to simulate it, but I'm not sure this is what you need.

---

### Post by 696f6e6963 on 2009-08-18
I have one computer which multiple users log on to. Each user has a directory for their files on the server "store" in the shared "students" directory. Their directory is the same as their username. So if "john" logs in, I would like for him to have an icon/directory/link in his home directory or on his desktop pointing to \\store\students\john. If Mary were to log on to this same computer, I would like her to have a link to \\store\students\mary. So, yes, I need my users to have a link to a subfolder within a shared directory. Since there is no way that you know of to do this directly (and you seem to know a lot on this subject), how could I simulate this?

---

### Post by dmizer on 2009-08-18
Ah ha. You need pam mount, not gvfs.

It's still going to have the same problem with sharename != directory path, but at least it's a step in the right direction. Here's a primer: [http://www.kroon.co.za/howto.php?howto=cifs_pam_mount](http://www.kroon.co.za/howto.php?howto=cifs_pam_mount)

Using PAM mount allows you to mount user shares (as with AD shares) upon user login.

Correct me if I'm wrong, but with AD isn't the share name tied to the username anyway?

The only way I know of to simulate what you want to do is to mount the share in a temporary directory, and provide a symbolic link from the desired path within the share to a locally accessable mountpoint. For example:

mount -t cifs //server/share /tmp/mountpoint -o whatever,options,you,need

Then link /tmp/mountpoint/$user to /home/$user/mountpoint

Not sure how I'd automate that though, so I highly suggest looking into PAM mount instead, as I'm positive it can do at least mostly what you want to do.

---

### Post by 696f6e6963 on 2009-08-19
Mount requires root permissions, would I mount the share at boot?

I may have found an alternate solution. Simply use gvfs-mount to mount the share then create a link to /home/$USER/.gvfs/students/$USER - I can't actually test it right now, but I see no reason why it shouldn't work.

---

