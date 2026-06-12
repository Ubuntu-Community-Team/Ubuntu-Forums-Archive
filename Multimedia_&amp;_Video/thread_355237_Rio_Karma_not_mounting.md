---
title: "Rio Karma not mounting"
date: 2007-02-07
forum: Multimedia &amp; Video
---

### Post by jcconnor on 2007-02-07
I am trying to get my Rio Karma recognized by my Edgy system.  The RMML works fine but I'm trying to get USB support for the thing.

The command lsusb reports back this:

Bus 004 Device 018: ID 045a:5210 SONICblue, Inc. Rio Karma Music Player

so I know that it sees the device.  When I try to mount it though I get this:

~$ sudo mount -t omfs /dev/sda2 /mnt/karma
mount: mount point /mnt/karma does not exist

I get the same message whether I try sda2 sda1 and karma1 karma2 or whatever.

I'm very new at this stuff but think I have everything set up like I need.

Any help would be appreciated.

John

---

### Post by jcconnor on 2007-02-10
Never mind.  The folks that wrote the libkarma module helped me get it fixed.  Dumb new user (short between the floor and the keyboard) type of error.  Everything is working now.

John

---

### Post by socngill on 2007-05-23
I'm having the same problem.  Can you tell me what the solution was please?

---

### Post by jcconnor on 2007-05-23
I have a blog that describes what I did to get my Karma working with Ubuntu Edgy and Amarok.  You can find the info here:

[http://blog.jcconnor.com/?p=14]("http://blog.jcconnor.com/?p=14")

Sorry to make you bounce out to that site (and I promise I'm not trying to boost my page count :p) but I already wrote it up and it's all there.

Let me know if you have any problems.

John

---

