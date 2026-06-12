---
title: "error writing to files in cifs-mounted folders"
date: 2009-11-21
forum: Networking &amp; Wireless
---

### Post by robodesign on 2009-11-21
Hello everyone!

I am having some new problems since I upgraded from Ubuntu 9.04 to 9.10.

I have cifs mounts since I started using Ubuntu four years ago. Here are the mount options I use:

```

mount //windows-xp-system/share-name /mnt/my-share-folder -t cifs -o credentials=/root/.secretfile,iocharset=utf8,uid=myUserName,noacl,nosetuids,noperm,dir_mode=0755,file_mode=0644

```

This worked fine until now, when I upgraded to Ubuntu 9.10.

The situation is as follows: the shares are mounted fine, no issues. I can list files and folders, I can browse the mounted share. I can write files, I can read files.

However, randomly when writing files in vim it freezes waiting for the cifs mount. The only way to unfreeze vim is to unmount the folder. Thus the file write fails. While vim is freezed any attempt to list folders / read files with other programs will cause the same to happen: freeze. Even the ls command never completes.

After remount things are fine again, which is weird.

Other times vim fails to write files with the error "file is a folder" - very weird again.

I should mention that even when I open new gnome-terminal tabs they fail to remember the folder I was in - if I was in a cifs-mounted folder.

What can I do? Is there a bug report about this?

Thanks!

---

