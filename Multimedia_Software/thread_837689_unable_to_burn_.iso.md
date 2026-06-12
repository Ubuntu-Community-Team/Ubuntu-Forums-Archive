---
title: "unable to burn .iso"
date: 2008-06-22
forum: Multimedia Software
---

### Post by fiskking on 2008-06-22
I was successful in making an .iso file using DeVeDe.  Upon trying to burn .iso file to Dvd using GnomeBaker I received the following error upon completion:

```
Executing 'builtin_dd if=/home/fisk/death_proof.iso of=/dev/sr1 obs=32k seek=0'
/dev/sr1: "Current Write Speed" is 2.5x1352KBps.
/dev/sr1: flushing cache
:-[ SYNCHRONOUS FLUSH CACHE failed with SK=3h/ASC=A0h/ACQ=80h]: Input/output error

```

can anyone help?

---

### Post by ahbart on 2008-06-23
Have you tried another application? I personally love k3b, but Brasero seems to be the standard burn application in Gnome-Ubuntu. 
I'm no an expert, but you could try to lower the burn speed.

---

### Post by forger on 2008-06-23
> **fiskking said:**
> GnomeBaker

Try with brasero, search for it through applications > add/remove..

---

### Post by fiskking on 2008-06-23
thanks guys for the help...downloading Brasero to give it a shot.  in gnomebaker I was burning at a speed of 2x.

---

### Post by fiskking on 2008-06-23
I was successful in burning a dvd using Brasero but upon checking the disk integrity, it gave an error message that it could not mount the drive.  I tried playing the dvd w/o any success (read: no disc)

---

### Post by Nikitas350 on 2008-06-23
The problem is when you write .iso or when you write dvds? Maybe your dvd writer has a problem...

---

### Post by fiskking on 2008-06-23
when I write the dvd. when using DeVeDe I use the NTsc format (N.american)

---

### Post by cariboo on 2008-06-23
Just to check, can you mount your iso manually. To do this in a terminal type the following:

```
sudo mount -o loop some.iso /mnt
```

replace some.iso with the name of your iso.

Jim

---

### Post by chiisu on 2008-07-14
I have recently had problems burning iso's in both Ubuntu 8.04 and Fedora 9.  Both have had recent kernel updates that I believe is related to this problem.  Both Brasero and K3B refuse to even begin, while GnomeBaker will burn the iso but then can't mount or boot the cd.  I have used the burner (ASUS DRW-2014L1T) recently in Linux and Windows just fine, so I know it's not a burner or media problem.

---

### Post by fiskking on 2008-09-19
> **cariboo907 said:**
> Just to check, can you mount your iso manually. To do this in a terminal type the following:

```
sudo mount -o loop some.iso /mnt
```

replace some.iso with the name of your iso.

Jim

no, I was unsuccessful.  For some reason, after I make the .iso and use either Brasero/Gnomebaker I receive a message stating input/output error.  I am able to burn cds and not Dvds.

running:
Gutsy
gnome 2.20.1
memory 1 gig
pentium 4
hard drive disk space: 6.4 gig
LG GSA-E40L Super Write dvd +r burner

Phillips DVD+R

---

