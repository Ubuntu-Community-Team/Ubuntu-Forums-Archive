---
title: "fbi on tty1 through init, how?"
date: 2010-11-04
forum: Multimedia Software
---

### Post by Tee.Gee on 2010-11-04
Hi,
I'm trying to set a lucid installation up so that it automatically launches an instance of fbi (framebuffer imageviewer) on tty1 after (re)booting.
My console is already framebuffer enabled, so there's nothing to do there. For the rest, I edit /etc/init/tty1.conf and replace
```
exec /sbin/getty -8 38400 tty2
```with
```
exec /usr/local/bin/run-fbi
```which contains the following two lines:
```
setterm -blank 0
/usr/bin/fbi -a -t 10 -cachemem 0 -noverbose /path/to/pix/*.png
```I test it by logging in and executing run-fbi manually. It works.
Now try the real thing:
```
# restart tty1
(no luck, syslog says:)
Nov  5 09:18:22 traalet init: tty1 main process (9545) terminated with status 1
Nov  5 09:18:22 traalet init: tty1 main process ended, respawning
...
Nov  5 09:18:22 traalet init: tty1 main process ended, respawning
Nov  5 09:18:22 traalet init: tty1 main process (9555) terminated with status 1
Nov  5 09:18:22 traalet init: tty1 respawning too fast, stopped
```Just to make sure, I set
```
chmod a+rw /dev/fb0
```but that didn't change anything.
Putting the call to fbi straight in tty1.conf didn't work either.
What am I doing wrong?

Cheers

---

### Post by Tee.Gee on 2010-11-09
Ok, I kept getting errors from fbi like: ioctl VT_GETSTATE: Inappropriate ioctl for device
Starting it with -T 1 and -d /dev/fb0 sort of worked but I ended up with 8 instances of fbi. Must be some sort of weird respawn thing init does.

Anyway, I finally got what I wanted using a slightly different approach.
I installed xorg, nodm and feh
And put the following in the user's .xsessionrc
```
while [ 1 ]; do
        feh -Z -F -x -D 7 -N --hide-pointer /path/to/pics/*.png
done

```
Works.

---

