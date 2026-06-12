---
title: "Brasero"
date: 2009-03-23
forum: Multimedia Software
---

### Post by RedSingularity on 2009-03-23
I am trying to run brasero but it wont open.  I decided to run it in terminal to see any errors.  When i did i got this....


brasero: error while loading shared libraries: libbrasero-media.so.0: cannot open shared object file: No such file or directory


What does this mean?  BTW i installed it via source code.

---

### Post by damis648 on 2009-03-23
Why install from source? It's in the repos. :popcorn:
Do you have the brasero libraries installed? I would make sure you have libbrasero-media0 and libbrasero-media-dev installed (it would be best to have those from source too, the same version as that that is installed.

---

### Post by RedSingularity on 2009-03-23
Yeah that was the problem.  Got it now, thanks  :)

---

### Post by videodrome on 2009-03-23
Uh cuz the version in the repos is old. :-k

Same error for me. 2.26. Anyone?

---

### Post by RedSingularity on 2009-03-23
Are you getting the same error as i got above?

---

### Post by videodrome on 2009-03-25
Yep. Exact same error.

---

### Post by RedSingularity on 2009-03-25
GO to the software manager, search brasero, check the install option and install it.  You will find that it installs the newer version, not the old one, since you already set up the newer dependencies.

---

### Post by videodrome on 2009-03-25
Actually ya know what? I installed 2.26 from the tarball, and it would throw dependency errors just like above. Then I rebooted and now it works fine. Go figure. All it needed was a reboot.

---

