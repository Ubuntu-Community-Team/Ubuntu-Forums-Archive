---
title: "K3b Won't Burn Ripped Songs to CD"
date: 2010-06-02
forum: Multimedia Software
---

### Post by HDTimeshifter on 2010-06-02
I ripped 2 music CDs for a total of 78 minutes, but K3b won't burn them to a blank CD-R.  It says the free space in temporary folder is 615.5 MB, but the size of project is 691.5 MB.  I don't know why the tmp directory is that small when I have 615 GB free on my filesystem.  When I start the burn, it simply says copying, but nothing shows up in the progress bars.  I am able to burn direct copies of CDs, however.  After a couple of tries and a couple of successful burns of entire CDs, I tried again, and it crashed.

---

### Post by thebigob on 2010-06-02
can you please post the result of running the command

```

df -h

```

---

### Post by HDTimeshifter on 2010-06-02
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             691G   41G  616G   7% /
none                  2.0G  288K  2.0G   1% /dev
none                  2.0G  664K  2.0G   1% /dev/shm
none                  2.0G  300K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
none                  2.0G     0  2.0G   0% /lib/init/rw
none                  691G   41G  616G   7% /var/lib/ureadahead/debugfs

---

### Post by HDTimeshifter on 2010-06-02
Seems like K3b is only good for duplicating discs.  I've often had problems when trying to create my own play list compilations by ripping selecting songs and combining to burn a custom disc.  Extremely frustrating!

---

### Post by HDTimeshifter on 2010-06-02
Got it to work.  For whatever reason, when I drag and drop songs from a CD to my custom project, then rip, it lists them as "CD Track".  Instead, I rip each source CD first, and the songs show up as .ORB type. Then I drag the songs to my custom project, and finally burn the CD.  I don't know why .ORB works, but not CD Track type.

---

