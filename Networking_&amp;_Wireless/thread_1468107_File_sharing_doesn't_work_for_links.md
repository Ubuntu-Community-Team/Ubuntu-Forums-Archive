---
title: "File sharing doesn't work for links"
date: 2010-05-01
forum: Networking &amp; Wireless
---

### Post by peterdm on 2010-05-01
I am trying to share a folder in my home dir which is a symlink to a folder somewhere else, but it doesn't work. When a share a folder which is not a link, it works. I have tried by completely removing nautilus-share and samba and reinstalling them, to no avail.

Procedure:
In nautilus, I right-click on the folder, "Sharing options", and enable sharing for the folder with "Guest access" enabled. Nautilus appears to have done what I asked, and decorates the folder icon with a green arrow. But when I browse the network, I don't see the share. Note that this works for "regular" folders, but not for my "symlink" folder.

What is special about this folder:
- It is a symlink
- The symlink points to a "public" folder which is locally shared using bindfs.

Is there a way to get this to work properly?

---

### Post by peterdm on 2010-05-01
I've found a workaround: I run "sudo nautilus" and share the folder (not the symlink) which is in the root dir.

So this is my setup:

- "/root/Video" contains the actual content
- "/home/public/Video" is the bindfs mount point pointing to "/root/Video" that is accessible to all users, all users see themselves as owner of the files
- "/home/user/Video" is a symlink to "/home/public/Video" for the user
- Sharing "/home/user/Video" via nautilus does not work
- Sharing "/root/Video" via nautilus as super user works! (sudo nautilus)

---

