---
title: "How can I copy files to my camera via USB?"
date: 2010-04-01
forum: Multimedia Software
---

### Post by MacUntu on 2010-04-01
I deleted files from my camera (SDHC via USB) which I now want to copy back but I don't know how.

The camera is mounted in ~/.gvfs and the target folder is owned by my user with read/execute permissions. Couldn't change the folders permission.

I tried to mount the camera using 'gksu nautilus', but the camera didn't show up in the side panel. Unfortunately I don't know how to mount the camera from the command line, so I'm stuck.

Heeeeelp, plz! :P

PS: the only available card reader doesn't recognize SDHC cards, so that's not an option. And no, I won't boot Windows for that task. :P

---

### Post by Chronon on 2010-04-01
Here's a related topic: [http://ubuntuforums.org/showthread.php?t=1136626](http://ubuntuforums.org/showthread.php?t=1136626)

The last post might be useful.

---

### Post by MacUntu on 2010-04-01
Unfortunately that didn't help. I was able to browse the camera's content using```
$ gvfs-tree gphoto2://[usb:001,018]
```

I was able to unmount the camera using gvfs-mount, but I couldn't mount it to a mount point where I had write permission. I also tried to set the 'can-write' attribute I found with:
```
$ gvfs-info gphoto2://[usb:001,018]/DCIM
display name: DCIM
name: DCIM
type: directory
size:  0
attributes:
  standard::type: 2
  standard::is-hidden: FALSE
  standard::name: DCIM
  standard::display-name: DCIM
  standard::icon: folder
  standard::content-type: inode/directory
  standard::size: 0
  id::filesystem: gphoto2:host=%5Busb%3A001%2C018%5D
  access::can-read: TRUE
  [COLOR="Red"]access::can-write: FALSE[/COLOR]
  access::can-execute: TRUE
  access::can-delete: TRUE
  access::can-trash: FALSE
  access::can-rename: FALSE

$ gvfs-set-attribute gphoto2://[usb:001,018]/DCIM access::can-write TRUE
Error setting attribute: Operation not supported by backend
```

---

### Post by MaskedMarauder on 2011-03-01
Is there a fix for this yet?

I'm using maverick and I can't read .avi files on my canon from any application at all.  Not even 'cp' or 'file' can work from the cli.  Not even if I login as root.  I only want to copy them into another directory for editing.

How does anyone get this to work?

   MM

---

