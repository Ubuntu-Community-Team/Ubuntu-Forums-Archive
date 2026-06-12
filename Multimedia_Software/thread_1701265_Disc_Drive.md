---
title: "Disc Drive"
date: 2011-03-06
forum: Multimedia Software
---

### Post by yeahme22000 on 2011-03-06
My disc drive is not showing up at all in my computer. Ubuntu 10.10 64 bit. When I first installed Ubuntu, the disc drive worked fine. Now, I can put in a disc and the drive will read it, but I can't find it anywhere on the computer. Almost as if the disc drive is not there. Any ideas?

---

### Post by howefield on 2011-03-06
Are you talking about an optical drive here ?

It doesn't show in the Places menu ?

Try looking in /media for it.

---

### Post by yeahme22000 on 2011-03-09
It's the drive that came with the computer. It worked fine when I first installed Ubuntu. I know this because I was able to play a cd. Now when I put a disc in, the drive reads the disc but as far as the computer goes, it's as if the drive doesn't exist.

---

### Post by Grenage on 2011-03-09
See if you can boot from the drive.  If you can, we can investigate; if you can't, the drive is likely defective.

Checking cables can't hurt.

---

### Post by yeahme22000 on 2011-03-09
I can't find any procedures to mount a pre-installed dvd writer. I shouldn't have to given the fact that the drive was recognized after I installed Ubuntu. I've done the following and not sure what it means:

  	 	 	 	p { margin-bottom: 0.08in; }  ls -l /dev | grep cdrom


To which I received:


   	 	 	 	p { margin-bottom: 0.08in; }  lrwxrwxrwx  1 root root           3 2011-03-09 07:44 cdrom -> sr0  
 crw-rw----  1 root cdrom    21,   1 2011-03-09 07:44 sg1  
 brw-rw----+ 1 root cdrom    11,   0 2011-03-09 07:44 sr0 



Any help would be hot.

---

### Post by yeahme22000 on 2011-03-09
I can boot from the drive. I reinstalled Ubuntu via live disc to see if it would help. Booted from cd just fine, but once again I can put it any cd or dvd and it's almost as if the drive doesn't exist

---

### Post by yeahme22000 on 2011-03-09
Howefield, I looked in /media. No drives. The only thing that showed was sonata volume which I'm not allowed to access

---

### Post by Grenage on 2011-03-09
Ok! I'll bungle along here, in the hopes we get lucky. ;)

First, lets see if the drive is actively detected:

```
sudo lshw -C disk
```

What does that give you?

Could you also post your /etc/fstab contents?

---

### Post by yeahme22000 on 2011-03-09
By the time of that post I had it fixed. Simple command and I felt a little stupid afterwards.

  	 	 	 	p { margin-bottom: 0.08in; }  sudo mv /dev/sg0 /dev/sg1

---

### Post by Grenage on 2011-03-10
Oh, how strange; I though that the sg* points were for generic SCSI devices, such as tape drives.

---

