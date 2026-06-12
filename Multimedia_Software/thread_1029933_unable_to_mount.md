---
title: "unable to mount"
date: 2009-01-03
forum: Multimedia Software
---

### Post by smurfgod on 2009-01-03
ok..i got a dvd that i am unable to mount.its a dvd-r and has 5 .avi files on it.i had this problem a couple of days ago and then...it worked.know its not.has anyone had this happen to them??

smurf   :D

---

### Post by cariboo on 2009-01-03
Have you tried mounting manually? In a Applications-->Accessories-->Terminal  type:

```
sudo mount /dev/scd0 /media/cdrom
```

Also check the output of dmesg after inserting the dvd. In a terminal type:

```
desg | tail -f
```

Jim

---

### Post by smurfgod on 2009-01-04
ok...i tried both the codes and they didnt work.when i tried to manuall t mount it said there was no media.When i went to the second code i couldnt get anything to come up.is the (-f) supposed to be there???


smurf   :confused:

---

