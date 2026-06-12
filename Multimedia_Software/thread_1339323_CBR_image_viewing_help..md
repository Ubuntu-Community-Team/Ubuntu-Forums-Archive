---
title: "CBR image viewing help."
date: 2009-11-27
forum: Multimedia Software
---

### Post by Perdin on 2009-11-27
Hey, I'm a new user to Ubuntu just switched over from XP to Ubuntu 9.10 and I'm getting the hang of it but there is one weird thing that I'm having problems with and that is .CBR/.CBZ files. Of course I searched and downloaded Comix and other CBR loaders but they won't display the images. I don't get an error message, instead the program opens up normally but there are no pictures inside.

I can tell the program knows there are pictures or files in there because it's getting the right number, but ofr some reason the pictures won't show.

---

### Post by prshah on 2009-11-27
> **Perdin said:**
> downloaded Comix and other CBR loaders 

I use Comix myself without any trouble. Can you try it from a terminal? Click Applications-Accessories-Terminal, then give the command```
comix
```

Now try opening a comic; please post back any messages that appear, for a clue to the problem.

---

### Post by slumbergod on 2009-11-27
I tried all of the popular comic book readers and in the end I decided I liked plain old Evince the best. Why? Because it let me view pages continuously...so I could just keep scrolling down with my mouse wheel page after page without having to keep clicking for the next or previous page.

---

### Post by Perdin on 2009-11-27
So I opened comix from terminal and this is what I got:

** (comix:2847): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (comix:2847): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

Still won't open CBRs.

---

### Post by Kingstrum on 2009-12-06
I just updated to Karmic with a fresh install and got the same error at startup. However, I believe the interesting part is the message

> unrar: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
 

showing up when you open a .CBR file (yes, .CBZs are fine).

Anyone else notice issues with unrar or libstdc++.so?
   Kingstrum

---

### Post by Kingstrum on 2009-12-16
Problem solved!

I went back and forth a couple times, but it turns out for some unknown reason the various unrar packages are hard-coded to libstdc++5, instead of 6, which is what Karmic ships. So since the two versions can (so far on my box, at least) live harmoniously, the simplest fix is go to:

```
http://packages.ubuntu.com/intrepid/libstdc++5
```

download the i386/ia64 package (depending on your architecture), and enjoy the .cbr files.

I'm going to check and see if anyone has submitted a bug report for this.

-Kingstrum

---

