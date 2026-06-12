---
title: "Ipod won't mount in 11.04"
date: 2011-05-04
forum: Multimedia Software
---

### Post by greenjumper on 2011-05-04
I can't get my ipod to mount in natty. It is a second generation classic with 32 GB. All that happens when I plug it in is that the ipod shows the "do not disconnect" screen. It doesn't mount and isn't recognized by Ubuntu.

Any ideas?

---

### Post by steveredshaw on 2011-05-05
same with me,  just upgraded to 11.04, ipod used to be recognised under ubuntu 10, no problem, but now does not show up anywhere!!

---

### Post by suquamish on 2011-05-05
well, just to throw my hat in.

Fresh install of 11.04 on a new computer, neither my ipod touch nor my ipod classic will mount.  

"Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdc3..."

Both devices work fine on my Macs, and I know the classic works on my 10.10 box.


I suspect it's [this bug]("https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/734883").

---

### Post by greenjumper on 2011-05-06
I've managed to fix my problem like this:

Connect unrecognized ipod

sudo mkdir /media/ipod

ls /dev/disk/by-uuid -alh - to find the uuid of the ipod

then I put this line in my fstab file:

UUID=D704-9A50 /media/ipod auto rw,user,noauto 0 0

Seems to mount now with no problems.

I must say that on top of this I have given up on Banshee. It crashed every time I tried to do something with one of my ipods. Have gone back to good, old, reliable Rhythmbox and now I'm happy!

---

### Post by steveredshaw on 2011-05-06
:P

I was going to try this, connected my ipod and it was recognised, just as it was before I upgraded

the only thing I have changed is that I chose Ubuntu Classic desktop rather than Unity (which I don't much like I have to say)

could running Unity be causing this problem?

---

### Post by merrymairi on 2011-11-29
> **greenjumper said:**
> I've managed to fix my problem like this:

Connect unrecognized ipod

sudo mkdir /media/ipod

ls /dev/disk/by-uuid -alh - to find the uuid of the ipod

then I put this line in my fstab file:

UUID=D704-9A50 /media/ipod auto rw,user,noauto 0 0

Seems to mount now with no problems.


This fix is not working for me. I don't know if it's my UUID or the way I edited fstab, but I still get the same message as before when I try to mount: 
Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdb2, missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
Any ideas as to what could be wrong?

---

