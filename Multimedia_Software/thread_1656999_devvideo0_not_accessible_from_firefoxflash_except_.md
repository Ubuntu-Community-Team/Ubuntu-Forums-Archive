---
title: "/dev/video0 not accessible from firefox/flash except by root"
date: 2010-12-31
forum: Multimedia Software
---

### Post by RobNY on 2010-12-31
Running Lucid - was an LTS upgrade from 8.04.

I have a usb webcam (off brand).  When installed, /dev/video0 is properly created and I can access the webcam through cheese as a regular user.

```
crw-rw----+ 1 root video 81, 0 2010-12-31 16:00 /dev/video0
```

The regular user is already a member of the video group, and I have checked all permissions under System->Admin->User/Groups->Advanced.

However, when as this regular user, I go to a website that tries to access my webcam via flash (ie, chatroulette or omegle), it does not detect the cam.  (Firefox 3.6.13 with Flash 10)

I've already set the LD_PRELOAD as suggested elsewhere.

HOWEVER, if I LD_PRELOAD and run Firefox as root, all works fine and the flash plugin sees the webcam.

dmesg does show many instances of the following:

```
[ 3394.472721] type=1503 audit(1293830602.818:6887):  operation="exec" pid=12484 parent=12483 profile="/usr/lib/firefox-3.6.13/firefox-*bin" requested_mask="x::" denied_mask="x::" fsuid=0 ouid=0 name="/bin/dbus-daemon"
```

In searching around, I believe this is a udev or acl related issue, but I have no idea how to move forward to fix this.

Any help would be greatly appreciated.

---

### Post by no2498 on 2011-01-02
try installing grease monkey
also make sure in the adobe settings manager you have allow and remember
for the site you use

if that dont help get opera

---

