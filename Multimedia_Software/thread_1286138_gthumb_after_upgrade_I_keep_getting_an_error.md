---
title: "gthumb: after upgrade I keep getting an error"
date: 2009-10-08
forum: Multimedia Software
---

### Post by sdide on 2009-10-08
Hey, I upgraded to Karmic Koala. After that gthumb hangs.

It opens fine but then nothing happens. If I start it from a terminal it gives the following.

```

$ gthumb .

** (gthumb:5563): WARNING **: directory creation failed: /home.

** (gthumb:5563): WARNING **: directory creation failed: /home.

** (gthumb:5563): WARNING **: directory creation failed: /home.

** (gthumb:5563): WARNING **: directory creation failed: /home.

** (gthumb:5563): CRITICAL **: new_uri_from_path: assertion `uri != NULL' failed

** (gthumb:5563): CRITICAL **: gth_dir_list_change_to__step2: assertion `pld != NULL' failed
$


```

Anyone know what files gthumb need to work properly? 
I've tried to do a  reinstall..
```

$ apt-get purge gthumb gthumb-data
$ apt-get install gthumb gthumb-data

```
to no avail.. 
anyone got any ideas?

/Søren

---

### Post by tropdoug on 2010-03-19
I have this problem too, and it's driving me nuts. I am going to BUMP this thread to see if we can get an answer

BUMP

---

### Post by mastapat11 on 2011-03-19
> **tropdoug said:**
> I have this problem too, and it's driving me nuts. I am going to BUMP this thread to see if we can get an answer

BUMP

Not to beat a dead horse, but i'm having this problem now and it just started today after working just fine a couple days ago and i'd appreciate some help too.

BUMP!

---

