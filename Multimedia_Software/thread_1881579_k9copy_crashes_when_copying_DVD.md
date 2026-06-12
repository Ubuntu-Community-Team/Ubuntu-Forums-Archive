---
title: "k9copy crashes when copying DVD"
date: 2011-11-15
forum: Multimedia Software
---

### Post by Ruben Remus on 2011-11-15
I cannot copy a DVD (Create folders or ISO image) in k9copy but I can encode an "avi" just fine.

k9copy will read the DVD but the minute it starts to copy it crashes.

```
oldpapadon@Don-Machine:~$ k9copy
ASSERT: "!isEmpty()" in file /usr/include/qt4/QtCore/qlist.h, line 269
KCrash: Application 'k9copy' crashing...
KCrash: Attempting to start /usr/lib/kde4/libexec/drkonqi from kdeinit
sock_file=/home/oldpapadon/.kde/socket-Don-Machine/kdeinit4__0
```

I am running 11.10 in 64 bit. I'm not sure what any of this means since I'm brand new to Linux.

I have already installed ubuntu-restricted-formats and livdvdcss2.

---

### Post by gordintoronto on 2011-11-15
Are you running Kubuntu? Apps beginning with "k" are usually written for Kubuntu, although many of them work just fine in Ubuntu.

Brasero is the standard disc burner app in Ubuntu, and I have used it to copy a DVD a friend created. Some people really like k3b.

---

### Post by Ruben Remus on 2011-11-16
It's Ubuntu (11.10) that I've installed k9copy on. It's actually my neighbour's computer that I installed k9copy on. I installed it from the Software Centre so I assumed it would run fine.

I did not; however, realize that applications beginning with 'k' may be intended for Kubuntu. Maybe I should just forget about k9copy. I was trying to find a DVD copier that my neighbour (who has little computer experience) would be comfortable with.

---

### Post by gordintoronto on 2011-11-16
Could you try Brasero, and let us know how it works?

---

### Post by alphacrucis2 on 2011-11-16
Deleted

---

### Post by Ruben Remus on 2011-11-17
I tried Brasero but for some reason could not load the DVD. The DVD title showed but I could not select it from the drop down menu. I think this may have been some minor glitch and I'll try Brasero again tomorrow.

I tried OGMRip and it began to copy the disc but got stuck @ 3%. I tried again with the same result. I switched to another DVD and it began copying fine. It started encoding and showed 3 hours left so I decided to leave it copying and I'll return tomorrow (it's my neighbour's computer).

The computer is a Co[SIZE=1]re i[/SIZE][SIZE=1]3  [/SIZE]with a brand new DVD drive (a cheap LG).

Tomorrow, out of curiosity, I'll try another disc with K9copy and give Brasero another shot.

---

### Post by Ruben Remus on 2011-11-17
Brasero works fine but I was hoping to find an application that would compress dual layer DVDs to fit on a 4.7GB disc.

OGMRip doesn't seem to do the trick. I set it to copy and encode for a 4.7GB DVD. It ran through the copy process quickly but I left my neighbour's place at 19:30 last night with 3 hours left in the encoding process. Today he told me he woke up @ 06:00 and OGMRip was still running. A few hours later he said it finished with a warning/error but he shut down the computer without writing down the warning/error.

I tried OGMRip again only to see the same 3 hours left in encoding. To make matters worse, there seems to be a 2.7GB folder that appears after the copy process and a 2.7GB MPEG file that appeared after the marathon overnight encoding session when OGMRip was set to create 4.7GB DVD files.

Both AcidRip and DVD::Rip are too complicated and I tried k9copy with a new disc only to have it crash again.

I'm thinking, at this point, I might be looking at non-Ubuntu solutions since he is dual-booted with Windows 7. I would prefer to keep him in Ubuntu though since he has a hard time with Windows 7.

---

### Post by MoreOrLess on 2011-11-18
FWIW, I've been using Linux in various distro forms for years, and I still have problems with just about every copying/encoding/ripping program. I'm thinking my CD burner is to blame, but other than updating its firmware (already done) and trying different SATA cables/ports, I don't know what else to try. I have to boot to that "other OS" to get these tasks done.

---

