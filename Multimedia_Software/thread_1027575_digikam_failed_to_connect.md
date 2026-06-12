---
title: "digikam: failed to connect"
date: 2009-01-01
forum: Multimedia Software
---

### Post by milanvora2 on 2009-01-01
Hi
I'm trying to connect my Canon Ixus65 with Digikam.

What works:

- As soon as i switch the camera, i cna import photos with f-spot photo manager
- I see the media drive mounted
- When i try to connect via digikam, i get an error message: failed to connect

This looks like a digikam specific issue

Any idea how to solve this ?

---

### Post by hansdown on 2009-01-01
Hi milanvora2.
Have you tried libgphoto? It's in synaptic package manager.

---

### Post by milanvora2 on 2009-01-01
Yes. I already have it installed.
This looks like a rights issue.
The media on the canon gets mounted as soon as i connect it.
if i unmount it and then ask digikam to connect then it works.

Any chance how to avoid this annoying step to manualyl unmount the media each time i connect the camera

---

### Post by hansdown on 2009-01-01
Hi milanvora2.
Do you have a card reader? I have a samsung that gives me problems connecting, so I read directly from my memory card.

---

### Post by milanvora2 on 2009-01-01
i have a card reader too. but i really want to solve this in digikam instead of trying workarounds

---

### Post by hansdown on 2009-01-01
I admire your persistence milanvora2.
I'll keep looking as well.

---

### Post by hansdown on 2009-01-01
I did find a bug report.

[https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/59788](https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/59788)

---

### Post by hansdown on 2009-01-01
There is one fix.

[ATTACH]98356[/ATTACH]

---

### Post by pumo on 2009-01-11
I have same proble with ixus 950is.
I found when umount camera drive from desktop it works with digikam.
but I would like to get it work straight from connecting...
that bug 64146 post didn't work with me, yes I changed vendor and product number to match with my camera...

any ideas ?

---

### Post by bvanaerde on 2009-02-25
I've got the same problem with my Ixus 800IS on Ubuntu 8.10 64bit

---

### Post by rfurman24 on 2009-04-29
Check this out.

[http://ubuntuforums.org/showthread.php?t=967104&highlight=camera+auto+mount](http://ubuntuforums.org/showthread.php?t=967104&highlight=camera+auto+mount)

---

