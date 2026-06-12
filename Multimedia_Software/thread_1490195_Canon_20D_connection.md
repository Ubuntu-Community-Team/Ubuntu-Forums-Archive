---
title: "Canon 20D connection"
date: 2010-05-21
forum: Multimedia Software
---

### Post by emanresu on 2010-05-21
I cannot connect my Canon 20D to my Ubuntu partition. It connects fine under Windows. Can someone suggest an app or something to get me connected, please?

---

### Post by joshedmonds on 2010-05-22
> GPhotoFS is a filesystem client based on libgphoto2 that exposes
supported cameras as filesystems; while some cameras implement the USB
Mass Storage class and already appear as filesystems (making this
program redundant), many use the Picture Transfer Protocol (PTP) or
some other custom protocol. But as long as the camera is supported
by libgphoto2, it can be mounted as a filesystem using this program.

gphotofs is available in the universe repository

Basic syntax is available on the man page at [URL="http://manpages.ubuntu.com/manpages/jaunty/man1/gphotofs.1.html"]
http://manpages.ubuntu.com/manpages/jaunty/man1/gphotofs.1.html[/URL]

Some tips for using gphotofs will be found by reading existing threads on these forums. e.g. [http://ubuntuforums.org/showthread.php?t=1273513]("http://ubuntuforums.org/showthread.php?t=1273513")

---

### Post by emanresu on 2010-06-03
i don't think i was clear. when i plug in my camera the following window opens up.
"you have just inserted a medium with digital photos. choose what application to launch. 

select how to open 'Canon Inc EOS 20D' and whether to perform this action in the future for other media type 'digital photos.' "

then below that the window has an "unmount", "cancel", and "open" button. so the camera appears to mount. what i'd like is some kind of app to let me transfer and manage the pictures on it. 

GPhotoFS appears to just mount the camera. i can't tell what drive it is mounted to.

---

### Post by tgalati4 on 2010-06-03
You should already have f-spot installed, if not then open a terminal:

sudo apt-get install f-spot

To see related photo programs:

apt-cache search photo

Plug the camera in and choose open.

---

### Post by emanresu on 2010-06-06
i had to install f-spot. it worked, thank you.

---

### Post by emanresu on 2010-06-25
Is there an app besides f-spot that works more like the MS camera wizard. for example that app lets me delete photos from the camera after i've copied them to the computer. it also gives me more flexibility in which folder i can transfer the pics to. f-spot only lets me use established folders and then, only certain ones in my home directory.

---

### Post by fancy_ninja on 2010-09-22
> **tgalati4 said:**
> You should already have f-spot installed, if not then open a terminal:

sudo apt-get install f-spot

To see related photo programs:

apt-cache search photo

Plug the camera in and choose open.
Thank you so much!! This just helped me out too =)

---

