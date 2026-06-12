---
title: "mjpg_streamer"
date: 2010-09-03
forum: Multimedia Software
---

### Post by Plasma_NZ on 2010-09-03
ok, have mjpg-streamer running on a 32bit 9.10 box - used a .deb 9386 install.. worked fine..

have another box which is running 10.04 64bit - tried a force-install of the deb but when trying to launch it i get the following error..


```

MJPG Streamer Version.: 2.0
ERROR: could not find input plugin
       Perhaps you want to adjust the search path with:
       # export LD_LIBRARY_PATH=/path/to/plugin/folder
       dlopen: input_uvc.so: cannot open shared object file: No such file or directory

```


any idea how to solve the problem..?

---

### Post by Plasma_NZ on 2010-09-04
no suggestions.?

---

### Post by Plasma_NZ on 2010-09-13
bump

---

### Post by Plasma_NZ on 2010-10-31
bump

---

### Post by Plasma_NZ on 2010-11-07
again, bump

---

### Post by Silvernail on 2010-12-05
Start with:
```
locate "input_uvc.so"
```
and see if it comes up where your error message said it should be.

If you don't own it, get it.
```
sudo apt-get install input_uvc.so
```

Test your system and report back.

---

### Post by Plasma_NZ on 2010-12-12
I know where the file is....

so i do the 


```
export LD_LIBRARY_PATH=/usr/lib
```

Then try to run the program again and it pukes the same error


```
ERROR: could not find input plugin
       Perhaps you want to adjust the search path with:
       # export LD_LIBRARY_PATH=/path/to/plugin/folder
       dlopen: input_uvc.so: cannot open shared object file: No such file or directory
```

---

### Post by Plasma_NZ on 2010-12-13
Solved my problem...


When issuing the command i wanted to use when it required the mentioned files... i just used the full-path e.g.

```

mjpg_streamer mjpg_streamer -i "/usr/lib/input_uvc.so -d /dev/video0 -f 60 -r 960x720" -o "output_http.so -p 58180 -n"

```

---

