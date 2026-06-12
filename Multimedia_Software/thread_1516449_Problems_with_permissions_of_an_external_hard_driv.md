---
title: "Problems with permissions of an external hard drive."
date: 2010-06-23
forum: Multimedia Software
---

### Post by wwe9112 on 2010-06-23
OK, so I am trying to set up a media server from my ubuntu to my ps3 so I can listen to music and watch movies that I have stored on an external hard drive on my pc. I managed to get media tomb configured and such but when I go to click on the hard drive to set it to share it says permission denied how do I go about havin git say that i can use the hard drive. I went and looked at the permissions of my external hard drive and it said they couldn't be determined.  


I hope I posted this in the right spot.  Thanks for all your help.

---

### Post by garvinrick4 on 2010-06-23
[B]A post that I have found in previous forum thread.
[/B]


**Re: External drive will not give permission to write or read**  
       You just need to change the mount point for that drive from root to your login name. _Assuming_ it is mounted to /media/storage and your login name is **wdriver**, open a terminal and run
          Code:
    

 sudo chown -R **wdriver**:**wdriver** /media/storage
ls -la /media

---

### Post by wwe9112 on 2010-06-23
I dont get what your telling me sorry.

---

### Post by garvinrick4 on 2010-06-23
The line of code after being put in a Terminal will give you permissions on that drive.
You have to give your external drive a label. This one is storage and use your own login name.
 To give your drive a label leave it unmounted go into disk utility or gparted and give it a label. Lets say you call it data and your login name is rick.
```

sudo chown -R rick:rick /media/data
``````
ls -la /media
```:  ls -la /media (asking what your permissions are for your media)

should start with drwxr-xr-x for the media (what ever you labeled you external drive).
It is easier if you label your partitions that way they are all /media/(whatever your label)

---

