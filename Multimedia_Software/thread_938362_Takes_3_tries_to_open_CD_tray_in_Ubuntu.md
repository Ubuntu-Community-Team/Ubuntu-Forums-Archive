---
title: "Takes 3 tries to open CD tray in Ubuntu"
date: 2008-10-04
forum: Multimedia Software
---

### Post by timzak on 2008-10-04
Whenever I want to burn a CD, I hit the eject button on the drive, but when I'm in Ubuntu, it takes 3 tries before it finally ejects.  When I'm not in Ubuntu the tray ejects on the first try.  Any idea why this happens and how I can get it to open on the first try while in Ubuntu?

I'm using 8.04 with all the latest updates.

---

### Post by timzak on 2008-10-06
*bump*--no one else needs multiple pushes on the eject button to open their CD drive?  It seems to me to be an issue with Ubuntu since the drive opens on the first try in DOS or while in the system BIOS.  

Thanks.

---

### Post by xeth_delta on 2008-10-06
> **timzak said:**
> *bump*--no one else needs multiple pushes on the eject button to open their CD drive?  It seems to me to be an issue with Ubuntu since the drive opens on the first try in DOS or while in the system BIOS.  

Thanks.

Is there any output when releasing the CD from a terminal with the command
```
eject
```
or
```
sudo eject
```

---

### Post by timzak on 2008-10-06
No, no output.  I tried multiple times and the first time, I saw the drive light turn on and heard a sound as if it was attempting to eject, but each time I tried afterward the drive light didn't even turn on.  No output whatsoever from the terminal either.  It still required a few physical presses of the eject button on the drive to get it to open.

Any ideas??

---

### Post by timzak on 2008-10-07
One more *bump*...I can't be the only one who's experienced this problem?  Is it a mounting issue?

Thanks.

---

### Post by davidryder on 2008-10-07
Try

```
eject -n
```

eject: device is 'dev/scd1'

Then try 

```
sudo umount -f /dev/scd1
or
sudo umount -f /dev/scd0

```

Changing the device to whatever eject -n outputs.

---

### Post by timzak on 2008-10-07
Thanks for the reply.  Here are the results:

```
tim@tim-desktop:~$ eject -n
eject: device is `/dev/scd0'
tim@tim-desktop:~$ sudo umount -f /dev/scd0
[sudo] password for tim: 
umount2: Invalid argument
umount: /dev/scd0: not mounted
tim@tim-desktop:~$ 

```

what does this mean?

---

### Post by snowpine on 2008-10-07
> **timzak said:**
> Thanks for the reply.  Here are the results:

```
tim@tim-desktop:~$ eject -n
eject: device is `/dev/scd0'
tim@tim-desktop:~$ sudo umount -f /dev/scd0
[sudo] password for tim: 
umount2: Invalid argument
umount: /dev/scd0: not mounted
tim@tim-desktop:~$ 

```

what does this mean?

Timzak, you are not alone... I have the exact same problem and error message on my Gateway computer. I have 2 CD/DVD drives; what about you?

---

### Post by timzak on 2008-10-07
Hi snowpine:

> **snowpine said:**
> Timzak, you are not alone... I have the exact same problem and error message on my Gateway computer. I have 2 CD/DVD drives; what about you?

Just one DVD/CD drive.  I don't understand what the output means.  Invalid argument, not mounted, what does it mean?

---

### Post by mc4man on 2008-10-07
```
what does it mean? 
``` It means there is no mounted media (file system ) in the drive. The possibilities are - the drive is empty, there is blank media  or an audio cd in the drive.
umount doesn't mean eject anyway

---

### Post by davidryder on 2008-10-07
Have you tried

```
sudo eject
```

?

If that doesn't work, look in your /etc/fstab file for an entry like:

```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

Post the entry here. Your drive may not be mounting correctly.

---

### Post by timzak on 2008-10-07
Here's mine:

```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

Just to reiterate:  when my drive is empty, and I want to open it to place a blank CD in to burn to, I hit the eject button on the drive.  The drive light comes on, the drive sounds like it is trying to open, but it stays closed.  I have to repeat this a few times (3-4?) before the drive finally opens.  Once I place the CD in the drive and close it, it operates normally.  My CD burns are always normal and at full speed.

If I boot into a DOS disk or enter the system BIOS, the drive always opens immediately on the first try.

---

### Post by snowpine on 2008-10-07
'sudo eject' opens drive #1.
When I press the button on drive #2, it makes noise and the light blinks, but it doesn't open. I have to press the eject button 3 or 4 times before drive #2 opens.

---

### Post by mc4man on 2008-10-07
@ timzak
just for curiosity what does either just plain eject or eject -s do?

---

### Post by timzak on 2008-10-07
> **mc4man said:**
> @ timzak
just for curiosity what does either just plain eject or eject -s do?

Neither eject nor eject -s open the drive.  Eject will cause the drive light to go on and sounds come from the drive as if it is trying to open, but it stays closed.  After the 1st eject command, subsequent eject commands don't even cause the drive light to go on.  To get the drive to open, I must manually press the eject button multiple times.

Thanks, I hope we can eventually get this sorted out.

Edit:  by the way, sudo eject behaves just like eject and eject -s

---

