---
title: "Slowing down my cdrom while ripping"
date: 2007-02-10
forum: Multimedia &amp; Video
---

### Post by kevinlyfellow on 2007-02-10
I just bought a cd that just does not rip properly.  It plays just fine on rhythmbox and xine, but when juicing it, it skips like mad.  The tracks that are having problems are the ones at the end.  So I was hoping for a way to slow down the read speed on my cdrom to reduce the amount of error.

---

### Post by kevinlyfellow on 2007-02-10
I found [http://hektor.umcs.lublin.pl/~mikosmul/computing/tips/cd-rom-speed.html](http://hektor.umcs.lublin.pl/~mikosmul/computing/tips/cd-rom-speed.html) which uses the eject command to slow down the cdrom drive, so I'm giving that a go

---

### Post by kevinlyfellow on 2007-02-10
Ok, when I use the eject command I get this

```

kevinly@ubuntu:~$ eject -v -x 4 /dev/cdrom
eject: device name is `/dev/cdrom'
eject: expanded name is `/dev/cdrom'
eject: `/dev/cdrom' is a link to `/dev/hdb'
eject: `/dev/hdb' is not mounted
eject: `/dev/hdb' is not a mount point
eject: setting CD-ROM speed to 4X

```

I also tried hdparm -E 4 /dev/hdb this does slow it down, but only for a few moments (I have no clue why).  I'm going to insert this into my hdparm.conf and see what happens

---

### Post by kevinlyfellow on 2007-02-10
Ok, well I added the following line to /etc/hdparm.conf
```

/dev/hdb {
        cd_speed = 4
}

```

But it did not seem to do anything!  I nursed it with the command line changes where it would ramp up to max speed at every new track.  Any suggestions on how I can more permanently change the cd speed?

---

