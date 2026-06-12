---
title: "BluRay og DVD which software?"
date: 2009-10-10
forum: Multimedia Software
---

### Post by KOROR on 2009-10-10
Hey Folks

I've bought a  Asrock Ion 330 BD [http://www.asrock.com/nettop/overview.asp?Model=ION%20330-BD](http://www.asrock.com/nettop/overview.asp?Model=ION%20330-BD) and installet Ubuntu (Desktop) 9.04, now my question is, which software can you guys recommend for playing BluRay and DVD discs?

---

### Post by ricardisimo on 2009-11-18
I'm curious (and cautiously pessimistic) about this as well. I'm also confused about the output in lshw about my removable disc drives:
```
           *-cdrom:0
                description: DVD reader
                product: BD  O  DH4O3S
                vendor: ATAPI
                physical id: 1
                bus info: scsi@2:0.0.0
                logical name: /dev/cdrom1
                logical name: /dev/dvd1
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: WH1A
                capabilities: removable audio dvd
                configuration: ansiversion=5 status=open
           *-cdrom:1
                description: DVD-RAM writer
                product: CDDVDW TS-H653R
                vendor: TSSTcorp
                physical id: 0.0.0
                bus info: scsi@3:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: 0301
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
```
Why does cdrom:0 (my bluray disk player) have the logical name of "cdrom1", while cdrom:1 has the logical name of "cdrom"? Seems like a needless bit of convolution.

When I put a Bluray disc into the machine, I get a popup from the system, asking me what app to use with this media, but also informing me that I have no app to use with this media (see attachment). What is to be done here? Thanks for any help.

---

### Post by xzero1 on 2009-11-18
Its a matter of copy protection. A player cannot play drm protected material without the key. Guess who *doesn't* want you to have that key.:p

---

### Post by mc4man on 2009-11-18
> output in lshw about my removable disc drives:....

That happens occasionally based on the placement of your drives. Typically /dev/sr0 (scd0) is given to the cd/dvd drive set in bios to boot from, depending on your setup the other drive can get the /dev/cdrom, /dev/dvd links.

Can be adjusted if desired in /etc/udev/rules.d/70-persistent-cd.rules

---

### Post by ilil on 2009-11-19
For Bluray you can try this [http://forum.doom9.org/showthread.php?t=149392](http://forum.doom9.org/showthread.php?t=149392)
or seek solution in Ubuntu wiki somewhere

---

