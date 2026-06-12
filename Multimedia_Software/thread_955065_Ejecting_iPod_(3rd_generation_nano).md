---
title: "Ejecting iPod (3rd generation nano)"
date: 2008-10-21
forum: Multimedia Software
---

### Post by MrSparkles on 2008-10-21
I feel like I am close.  Very close.  I must come up with a method to allow my stepson (NOT an admin account) to properly eject his new iPod without orphaning songs.

He can mount it (/dev/sdd1 as /media/ipod) and transfer songs to it using Amarok.  But a proper ejection is the issue.

eject /media/ipod

results in:

```
eject: unable to open `/dev/sdd1'
```

eject -v /media/ipod

gets us:

```
eject: device name is `/media/ipod'
eject: expanded name is `/media/ipod'
eject: `/media/ipod' is not mounted
eject: `/dev/sdd1' can be mounted at `/media/ipod'
eject: `/dev/sdd1' is a multipartition device
eject: unable to open `/dev/sdd1'
```

Using my (admin) account

sudo eject -v /media/ipod

outputs:

```
eject: device name is `/media/ipod'
eject: expanded name is `/media/ipod'
eject: `/media/ipod' is not mounted
eject: `/dev/sdd1' can be mounted at `/media/ipod'
eject: `/dev/sdd1' is a multipartition device
eject: trying to eject `/dev/sdd1' using CD-ROM eject command
eject: CD-ROM eject command succeeded
```

If eject is ejecting the iPod as a CD-ROM device, then

eject -vr /media/ipod

would be the next command to try.  However, it spits out this:

```
eject: device name is `/media/ipod'
eject: expanded name is `/media/ipod'
eject: `/dev/sdd1' is mounted at `/media/ipod'
eject: unmounting device `/dev/sdd1' from `/media/ipod'
eject: `/dev/sdd1' is a multipartition device
eject: unable to open `/dev/sdd1'
```

A regular user can mount the device.  After using the 'eject' command, the device is unmounted by not completely 'ejected'.  This seems to be necessary as to properly sync the iPod/Amarok/iPod database.

Any suggestions?  I'd really like to have a nice, clean command for Amarok to eject the iPod.

Thank you for your help!

Sparkles

---

### Post by mc4man on 2008-10-21
Assuming your using 8.04
Use 
```
sudo eject /dev/[COLOR="Red"]sdd1[/COLOR]
```  
(adjust red to what is shown in mouseover of ipod if different, must be disconnected from amarok first.

This should eject and return ipod to main menu window (vs  'Do not disconnect' circle

---

### Post by MrSparkles on 2008-10-21
eject /dev/sdd1

spits out

```
eject: unable to open `/dev/sdd1'
```

I am not going to allow the kid an admin account for his safety and my sanity.  As such, anything involving 'sudo' is out of the question.

Thank you, anyways.

Sparkles

---

### Post by mc4man on 2008-10-21
> As such, anything involving 'sudo' is out of the question.

Then your hope would be either find an amarok post disconnect command that works to eject or that kubuntu adjusts the way it treats devices like ipod's.
The right click 'safely remove' only unmounts.
For comparison in ubuntu there is a r. click 'eject' that works fine on ipod's

---

### Post by mc4man on 2008-10-21
This will work as a post-disconnect command in kubuntu to disconnect and eject.

The only downside is you need to enter your password in the command, if your grandson doesn't know about the 'configure media device' setting then it would be ok.  (it's not totally obvious to find) 
In any event 

```
echo <password> | sudo eject %d
```

---

### Post by alison.santiago on 2008-11-09
Umm, the problem does seem to be permissions.  I fixed it by adding myself to the disk group and it ejected with no problems.  Please try it out and let me know if it does work for you.:KS

:lolflag:

---

### Post by mc4man on 2008-11-09
> adding myself to the disk group 
good job, works here with a post disconnect of eject %d

---

