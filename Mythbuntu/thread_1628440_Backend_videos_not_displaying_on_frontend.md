---
title: "Backend videos not displaying on frontend"
date: 2010-11-22
forum: Mythbuntu
---

### Post by cander611 on 2010-11-22
I have a frontend/backend combo machine that works perfectly.  I just loaded a frontend only machine for another room.  I can watch live tv and see all the recorded shows using the frontend, but I cannot see any videos (which are iso files).  I'm not using storage groups.  I have a path defined under the Media settings on my backend.  On the frontend machine the videos path was blank.  Can anyone tell me what I'm missing to access the videos stored on my backend machine from my frontend machine?

The videos can be accessed from the frontend that's on the same box as the backend.  It's just the remote frontend that doesn't see them.

---

### Post by nickrout on 2010-11-22
you need to mount the directory that has the videos on the backend in exactly the same place on the frontend.

ie if the videos are in the default position on the backend (/var/lib/mythtv/videos) and you have samba sharing enabled then:

```
mount -t cifs //backend/videos /var/lib/mythtv/videos -o username=xxx,password=yyy
```

username is the user running the frontend on the combined box, password is that user's password.

---

### Post by cander611 on 2010-11-27
I tried mounting it and it didn't work.  I changed over to using Storage Groups and I can see videos.  I can't play ISO's but I understand that's not support with Storage Groups.  I can pay avi files.  One thing that's strange is each time I open the Videos window on the remote frontend it loses all information about each movie.  Cover, synopsis, etc...  Any idea why that is?

---

### Post by thatguruguy on 2010-11-27
Which version of mythtv are you running?  It was my understanding (although I haven't tried it) that .iso files are supported under mythtv .24.

---

### Post by nickrout on 2010-11-27
> **thatguruguy said:**
> Which version of mythtv are you running?  It was my understanding (although I haven't tried it) that .iso files are supported under mythtv .24.

unencrypted isos only - read the release notes!!

---

### Post by cander611 on 2010-11-27
I'm using .24.  I don't know if the iso's are encrypted or not.  I don't mind using an alternate format.  I just don't want to lose my covers, ratings, synopsis, etc for each one every time I exit the Video menu.  What would cause that data to be dropped every time I navigate away and back to the video folder?

---

