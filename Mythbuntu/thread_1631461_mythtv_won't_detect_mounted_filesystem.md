---
title: "mythtv won't detect mounted filesystem"
date: 2010-11-26
forum: Mythbuntu
---

### Post by Sharft 6 on 2010-11-26
this is in my fstab
```

UUID=264191d0-6419-4819-a9fa-c5bbd2ab49b2	/media/750GB/	ext4	defaults	0	0

```

this is on the mounted fs
```

ls -l /media/750GB/
total 52
drwsrwsrwx 2 mythtv mythtv  4096 2010-11-27 09:35 banners
drwsrwsrwx 2 mythtv mythtv  4096 2010-11-27 09:35 coverart
drwsrwsrwx 2 mythtv mythtv  4096 2010-11-27 09:35 db_backups
drwsrwsrwx 2 mythtv mythtv  4096 2010-11-27 09:35 fanart
drwsrwsrwx 2 mythtv mythtv  4096 2010-11-27 09:35 livetv
drwx------ 2 root   root   16384 2010-10-13 22:51 lost+found
drwsrwsrwx 2 mythtv mythtv  4096 2010-11-27 09:35 recordings
drwsrwsrwx 2 mythtv mythtv  4096 2010-11-27 09:35 screenshots
drwsrwsrwx 2 mythtv mythtv  4096 2010-11-27 09:35 trailers
drwsrwsrwt 6 mythtv mythtv  4096 2010-11-27 09:35 videos

```

and you'll just have to take my word that I have added all of those as storage directories in mythtv backend.

I have tried adding Vidoes in my home folder which works perfectly find. Just can't get anything from the mounted drive to show up in mythtv.

---

### Post by nickrout on 2010-11-26
in mythvideo hit m for menu and then scan

---

### Post by Sharft 6 on 2010-11-26
yeah thats what i've been doing

it also will not record to livetv or recordings on 750GB. I would think it would record something by now as i don't have much space left on the 1.5TB system drive.

---

### Post by nickrout on 2010-11-26
> **Sharft 6 said:**
> yeah thats what i've been doing

it also will not record to livetv or recordings on 750GB. I would think it would record something by now as i don't have much space left on the 1.5TB system drive.

permissions?

---

### Post by Sharft 6 on 2010-11-27
yeah thats what I thought but the above permissions are right aren't they?

---

### Post by nickrout on 2010-11-27
> **Sharft 6 said:**
> yeah thats what I thought but the above permissions are right aren't they?

what about the ownership and permissions of the files themselves?

---

### Post by Sharft 6 on 2010-11-27
I set them recursively so all sub files have the same permissions

```

  ls -l /media/750GB/videos/tv\ series/Air_Crash_Investigation/
total 8977940
-rwxrwxrwt 1 mythtv mythtv 365877248 2006-07-26 14:18 ACI_S01E01_Unlocking_Disaster.avi
-rwxrwxrwt 1 mythtv mythtv 365969408 2006-07-26 14:20 ACI_S01E06 Flying_On_Empty.avi
-rwxrwxrwt 1 mythtv mythtv 366198784 2006-07-22 16:39 ACI_S02E01_Blow_Out.avi
-rwxrwxrwt 1 mythtv mythtv 366479360 2006-07-25 20:16 ACI_S02E02_A_Wounded_Bird.avi
-rwxrwxrwt 1 mythtv mythtv 366366720 2006-07-25 19:34 ACI_S02E03_Hijacked.avi
-rwxrwxrwt 1 mythtv mythtv 366569472 2006-07-25 20:15 ACI_S02E04_Mid-Air_Collision.avi
-rwxrwxrwt 1 mythtv mythtv 366155776 2006-07-26 07:13 ACI_S02E05 Crash_On_The_Mountain.avi
-rwxrwxrwt 1 mythtv mythtv 366073856 2006-07-25 09:10 ACI_S02E06_Deadly_Delay.avi
-rwxrwxrwt 1 mythtv mythtv 366968832 2008-03-04 14:19 Air Crash Investigation 0501 - Dead Weight.avi
-rwxrwxrwt 1 mythtv mythtv 419399680 2008-04-02 12:36 Air Crash Investigation 0503 - Deadly Glide.avi
-rwxrwxrwt 1 mythtv mythtv 419446784 2008-04-03 01:25 Air Crash Investigation 0505 - Southern Storm.avi
-rwxrwxrwt 1 mythtv mythtv 419446784 2008-04-09 09:33 Air Crash Investigation 0506 - Cargo Conspiracy.avi
-rwxrwxrwt 1 mythtv mythtv 419422208 2008-06-25 03:55 Air Crash Investigation 0510 - Radio Silence.avi
-rwxrwxrwt 1 mythtv mythtv 399277738 2006-08-07 05:19 Air Crash Investigations - 3x01 - Hanging by a Thread_(ci).avi
-rwxrwxrwt 1 mythtv mythtv 367580296 2007-07-29 18:25 Air Crash Investigations - 3x02 - Attack Over Baghdad-shiloh.avi
-rwxrwxrwt 1 mythtv mythtv 367445920 2007-07-28 14:56 Air Crash Investigations - 3x03 - Out Of Control-shiloh.avi
-rwxrwxrwt 1 mythtv mythtv 399556224 2006-08-05 13:43 Air Crash Investigations - 3x04 - Suicide Attack_(ci).avi
-rwxrwxrwt 1 mythtv mythtv 396369346 2006-08-08 05:51 Air Crash Investigations - 3x05 - Mistaken Identity_(ci).avi
-rwxrwxrwt 1 mythtv mythtv 396256534 2006-08-05 22:32 Air Crash Investigations - 3x06 - Bomb On Board_(ci).avi
-rwxrwxrwt 1 mythtv mythtv 367580838 2007-07-29 19:27 Air Crash Investigations - 3x07 -Helicopter Down-shiloh.avi
-rwxrwxrwt 1 mythtv mythtv 367534244 2007-07-29 17:31 Air Crash Investigations - 3x08 - Death And Denial-shiloh.avi
-rwxrwxrwt 1 mythtv mythtv 367245578 2007-07-29 17:54 Air Crash Investigations - 3x09 - Kid In The Cockpit-shiloh.avi
-rwxrwxrwt 1 mythtv mythtv 370718334 2007-07-29 18:11 Air Crash Investigations - 3x10 - Ocean Landing-shiloh.avi
-rwxrwxrwt 1 mythtv mythtv 419375104 2008-05-29 09:12 Air Crash Investigation V - 09 - Whos at the Controls.avi

```

---

### Post by nickrout on 2010-11-27
> **Sharft 6 said:**
> I set them recursively so all sub files have the same permissions

```

  ls -l /media/750GB/videos/tv\ series/Air_Crash_Investigation/
total 8977940
-rwxrwxrwt 1 mythtv mythtv 365877248 2006-07-26 14:18 ACI_S01E01_Unlocking_Disaster.avi
-rwxrwxrwt 1 mythtv mythtv 365969408 2006-07-26 14:20 ACI_S01E06 Flying_On_Empty.avi
-rwxrwxrwt 1 mythtv mythtv 366198784 2006-07-22 16:39 ACI_S02E01_Blow_Out.avi
-rwxrwxrwt 1 mythtv mythtv 366479360 2006-07-25 20:16 ACI_S02E02_A_Wounded_Bird.avi
-rwxrwxrwt 1 mythtv mythtv 366366720 2006-07-25 19:34 ACI_S02E03_Hijacked.avi
-rwxrwxrwt 1 mythtv mythtv 366569472 2006-07-25 20:15 ACI_S02E04_Mid-Air_Collision.avi
-rwxrwxrwt 1 mythtv mythtv 366155776 2006-07-26 07:13 ACI_S02E05 Crash_On_The_Mountain.avi
-rwxrwxrwt 1 mythtv mythtv 366073856 2006-07-25 09:10 ACI_S02E06_Deadly_Delay.avi
-rwxrwxrwt 1 mythtv mythtv 366968832 2008-03-04 14:19 Air Crash Investigation 0501 - Dead Weight.avi
-rwxrwxrwt 1 mythtv mythtv 419399680 2008-04-02 12:36 Air Crash Investigation 0503 - Deadly Glide.avi
-rwxrwxrwt 1 mythtv mythtv 419446784 2008-04-03 01:25 Air Crash Investigation 0505 - Southern Storm.avi
-rwxrwxrwt 1 mythtv mythtv 419446784 2008-04-09 09:33 Air Crash Investigation 0506 - Cargo Conspiracy.avi
-rwxrwxrwt 1 mythtv mythtv 419422208 2008-06-25 03:55 Air Crash Investigation 0510 - Radio Silence.avi
-rwxrwxrwt 1 mythtv mythtv 399277738 2006-08-07 05:19 Air Crash Investigations - 3x01 - Hanging by a Thread_(ci).avi
-rwxrwxrwt 1 mythtv mythtv 367580296 2007-07-29 18:25 Air Crash Investigations - 3x02 - Attack Over Baghdad-shiloh.avi
-rwxrwxrwt 1 mythtv mythtv 367445920 2007-07-28 14:56 Air Crash Investigations - 3x03 - Out Of Control-shiloh.avi
-rwxrwxrwt 1 mythtv mythtv 399556224 2006-08-05 13:43 Air Crash Investigations - 3x04 - Suicide Attack_(ci).avi
-rwxrwxrwt 1 mythtv mythtv 396369346 2006-08-08 05:51 Air Crash Investigations - 3x05 - Mistaken Identity_(ci).avi
-rwxrwxrwt 1 mythtv mythtv 396256534 2006-08-05 22:32 Air Crash Investigations - 3x06 - Bomb On Board_(ci).avi
-rwxrwxrwt 1 mythtv mythtv 367580838 2007-07-29 19:27 Air Crash Investigations - 3x07 -Helicopter Down-shiloh.avi
-rwxrwxrwt 1 mythtv mythtv 367534244 2007-07-29 17:31 Air Crash Investigations - 3x08 - Death And Denial-shiloh.avi
-rwxrwxrwt 1 mythtv mythtv 367245578 2007-07-29 17:54 Air Crash Investigations - 3x09 - Kid In The Cockpit-shiloh.avi
-rwxrwxrwt 1 mythtv mythtv 370718334 2007-07-29 18:11 Air Crash Investigations - 3x10 - Ocean Landing-shiloh.avi
-rwxrwxrwt 1 mythtv mythtv 419375104 2008-05-29 09:12 Air Crash Investigation V - 09 - Whos at the Controls.avi

```

i THINK you need to check permissions all the way down the chain. I suspect that maybe /media/750G might have the wrong permissions?

ls -ld /media/750G

---

### Post by Sharft 6 on 2010-11-27
oh thanks its working now.

didn't know I needed to set the permissions all the way up the chain.

---

