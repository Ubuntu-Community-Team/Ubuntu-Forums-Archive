---
title: "Netatalk + AFP Problems"
date: 2010-12-16
forum: Networking &amp; Wireless
---

### Post by thomashw on 2010-12-16
My goal was to be able to have Time Machine backup over my network to a computer running Ubuntu.

I setup Netatalk and Avahi in order to do so.

I have four drives being shared (AFP) which my OS X computer can see and connect to.

The problem is, the fourth drive, which I want to use for the Time Machine backup, I can't create any files/folders via AFP. I **can** if I enable samba sharing. The other 3 drives I have no problem creating/deleting folders and files.

Three of the drives are mounted on startup using fstab and they all have the same entries:

```

/dev/sdb1	/media/sdb1		ext4	defaults	0	0
/dev/sdc1	/media/TimeMachine	ext4	defaults	0	0
/dev/sde1	/media/sde1		ext4	defaults	0	0
```

All three have the same entries in the AppleVolumes.default for netatalk as well.

I've tried chmod'ing and chown'ing and it hasn't helped.

Help would be much appreciated!

---

### Post by thomashw on 2010-12-16
Got it working.

I removed the entry from fstab, formatted the drive using a different label, and then did the following steps and it now works.

Not sure what went wrong before!

```

sudo mkdir /media/timemach
sudo nano /etc/fstab
 /media/timemach TimeMachine ext4 defaults 0 0
sudo mount -a
sudo chown -R thomas:thomas /media/timemach
sudo chmod -R 755 /media/timemach

```

---

