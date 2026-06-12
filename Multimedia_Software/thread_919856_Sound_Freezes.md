---
title: "Sound Freezes"
date: 2008-09-14
forum: Multimedia Software
---

### Post by Hawk__0 on 2008-09-14
Right now I'm on my girlfriends laptop and its having random issues with sound so I basically took it for the day to check things out.  So I'm listening to music in amarok and randomly it just freezes.  So naturally, I kill all the processes and start it back up.  Now this is where the fun begins.  All media players will attempt to play a file then freeze.

Funny thing is, youtube videos in firefox still have sound that plays fine.  The easy way to fix this is to restart the computer, which is just unacceptable.  Anyone else out there have this problem?00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)


EDIT: Logging out then in seems to work as well, so obviously this process that is causing this problem is being terminated and restarted upon logon. What process could this be?

lspic:

> 00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)


Specs:
HP Pavilion dv6000
Ubuntu 8.04

Thanks in advance!

---

### Post by knattlhuber on 2008-09-14
Next time it crashes, please log out and post the output of

```
cat /var/log/syslog
dmesg

```

---

### Post by Hawk__0 on 2008-09-14
log out, then log in and paste the output of those commands? or log out and switch to a different tty and post the output?

---

### Post by Yellow Pasque on 2008-09-14
Try upgrading your ALSA: [http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959) 
..or get rid of ALSA and try OSS4: [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

---

### Post by Hawk__0 on 2008-09-14
temujin thanks so much its working great so far!! Hopefully I have no issues!

one question though, how can I make it so my volume buttons on my laptop control the volume control again? Currently it shows the volume is at 0% and doesn't move an inch when I try to change it.  But I do have the regular volume adjuster on the panel working fine.

Edit: Nevermind!! A system reboot fixed it. Thanks again, all is well!

---

