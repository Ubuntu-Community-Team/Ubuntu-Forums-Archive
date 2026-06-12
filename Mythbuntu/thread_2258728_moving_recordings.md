---
title: "moving recordings"
date: 2014-12-30
forum: Mythbuntu
---

### Post by deanie44 on 2014-12-30
Hi everyone.  I just moved 2 recordings from Mythtv recordings via nautilus(called Castle) into the "castle" folder on my usb harddrive.  I started Mythtv frontend and they are not in the castle recording group. What did I do wrong?  Any assistance will be appreciated.  deanie44

---

### Post by khPWXxF on 2014-12-30
Can you see the recordings via a terminal session?
If you cd to the folder on your usb drive, what does 'ls -l' tell you about the permissions and ownership of the recordings?  
They need to be owned by, readable and writable by user mythtv.

Phil
ps if you post a follow up I may be off air for a few days - IPS switchover imminent.

---

### Post by deanie44 on 2014-12-30
[**[COLOR=#000000]khPWXxF[/COLOR]**]("http://ubuntuforums.org/member.php?u=1844453"). thank you for answering my post.  Here is the outcome from the terminal:

deanie56@deanie56-Inspiron-560:~$ cd /media/myth/castle
deanie56@deanie56-Inspiron-560:/media/myth/castle$ ls -l
total 25341512
-rw-r--r-- 1 mythtv mythtv 6543246940 Nov 17 23:01 4008_20141118030100.mpg
-rw-rw-rw- 1 mythtv mythtv      64258 Nov 28 09:29 4008_20141118030100.mpg.png
-rw-r--r-- 1 mythtv mythtv 6323325856 Nov 23 01:03 4008_20141123050500.mpg
-rw-rw-rw- 1 mythtv mythtv      38036 Nov 27 22:05 4008_20141123050500.mpg.png
-rw-r--r-- 1 mythtv mythtv 6540526768 Nov 24 23:01 4008_20141125030100.mpg
-rw-rw-rw- 1 mythtv mythtv      87091 Nov 30 17:25 4008_20141125030100.mpg.png
-rw-rw-r-- 1 mythtv mythtv 6542239072 Dec  1 23:01 4008_20141202030100.mpg
-rw-rw-rw- 1 mythtv mythtv      76273 Dec 30 08:25 4008_20141202030100.mpg.png
-rw-rw-rw- 1 mythtv mythtv      68794 Dec 30 05:39 4008_20141209030100.mpg.png
deanie56@deanie56-Inspiron-560:/media/myth/castle$ 

Thank you. deanie44

---

### Post by khPWXxF on 2014-12-30
They look ok - they are the same as my recordings.

What about permissions for mythtv on the directory itself?
How do they compare with the original directory?
```
ls -ld /media/myth/castle
ls -ld /var/lib/mythtv/recordings
```

What does find_orphans.py report?

Phil

---

### Post by deanie44 on 2014-12-30
here is the output:

deanie56@deanie56-Inspiron-560:~$ ls -ld /media/myth/castle
drwxrwxr-x 2 deanie56 mythtv 4096 Dec 30 11:00 /media/myth/castle
deanie56@deanie56-Inspiron-560:~$ ls -ld /var/lib/mythtv/recordings
drwxrwsr-x 3 mythtv mythtv 4096 Dec 30 13:01 /var/lib/mythtv/recordings
deanie56@deanie56-Inspiron-560:~$ 
 
Thanks again.  deanie44

---

### Post by Lester_Burnham on 2014-12-30
Hi,

Is /media/myth/ setup as a storage group in mythbackend? If not, you've moved them away from where mythtv can find them.
I don't use recording groups, but I that's how they work.

If you're going to me adding and removing this storage group. I don't know if mythtv will like that. You might be better off exporting the recording to that location as a user job in mythtv.

[https://www.mythtv.org/wiki/Storage_Groups](https://www.mythtv.org/wiki/Storage_Groups)

Lester

---

### Post by khPWXxF on 2014-12-31
Might this fix it?
sudo chown mythtv:mythtv /media/myth/castle/
Phil

---

### Post by tgm4883 on 2014-12-31
You changed the storage group that it was in, which is not connected in any way to the recording group (storage group is the location it's stored in. Recording group is other settings specific to types of recordings). Recording group info for a specific recording is kept in the database, I'm not sure of any way for a user to change that.

---

### Post by deanie44 on 2014-12-31
Hi Lester_Burham.  /media/myth/ is a partition on a external harddrive where i store all the storage groups for mythtv. Is that the wrong way to have it configured?  It has been working for me.  I have it mounted in media and I edited fstab so it could mount on startup.  When I look in the folder castle on the /media/myth partition I  count four recordings and there are five recordings in the frontend.  I forgot to mention that a restored a pervious database.   I do not know where the five recording is coming from.  It is a "castle' recording, but I can"t find it in the system.  It plays good.  Is there a reason why I cannot find the recording?  deanie44

---

### Post by Lester_Burnham on 2015-01-01
.

---

### Post by Lester_Burnham on 2015-01-01
Hi,
If it's permanent it should be fine. Do you still have a recording group /var/lib/mythtv/recordings? It may be there still. 
If you hit the 'm' or menu key on your remote with the recording selected, you may be able to move it to the correct storage group.
I haven't used storage groups for sorting, so either reading up on how to use them or experiment until someone that uses them comes along.
I think you can manually move files around in the defined storage groups and mythtv will find them, but I bet there's an automated way of doing it with the recording rule.

---

