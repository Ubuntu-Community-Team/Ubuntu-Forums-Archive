---
title: "Gnomad2 not installed correctly?"
date: 2007-02-06
forum: Multimedia &amp; Video
---

### Post by nickoli_02 on 2007-02-06
I followed method 1 of this guide:

[http://ubuntuforums.org/showthread.php?t=199250&highlight=CREATIVE+ZEN+vision+m+gnomad]("http://ubuntuforums.org/showthread.php?t=199250&highlight=CREATIVE+ZEN+vision+m+gnomad")

to install Gnomad2 to work with my creative zen vision: m. Everything went smoothly, but when I checked the applications menu for the gnomad2 launcher it wasn't there. OK, I thought, so I went to the terminal and tried launching it and this is what I get:

```
$ gnomad2
bash: gnomad2: command not found

```

So, my question is... how do I check to ensure gnomad2 installed correctly, how do I launch gnomad2, and how do I create a launcher for it? :)

---

### Post by nickoli_02 on 2007-02-06
hate to do this, but...

bump

---

### Post by gb5757870 on 2007-02-12
Hey, I was scratching my head trying to get Gnomad installed with that same guide but in the end just installed Gnomad through the Synaptic Package Manager and worked first time. Give it a go.

---

### Post by nickoli_02 on 2007-02-12
Yea, I tried that too. I got Gnomad2 installed but now the problem is it won't recognize my Creative Zen Vision: M

---

### Post by Kougaiji on 2007-02-21
I got the same problem, anyone please have a solution?

---

### Post by nickoli_02 on 2007-02-22
I got it working :) I kind of left this issue for awhile and after downgrading to Dapper decided to give it another shot. So, following the guide for Dapper and building everything from source everything worked great :D

One thing, when going through checkinstall it's a good idea to change the name of the library or package or whatever so that synaptics doesn't try and tell you it has an update for it (you don't want the update). Simply prefixing it with something like "-built" works.

---

### Post by still.thought on 2007-03-09
I tried compiling in edgy with the instructions for dapper (not sure if that's a good idea.)
and got this error:

```
jukebox.c:130: error: ‘LIBMTP_FILETYPE_AAC’ undeclared here (not in a function)
jukebox.c:131: error: ‘LIBMTP_FILETYPE_FLAC’ undeclared here (not in a function)
jukebox.c:132: error: ‘LIBMTP_FILETYPE_MP2’ undeclared here (not in a function)
jukebox.c:133: error: ‘LIBMTP_FILETYPE_M4A’ undeclared here (not in a function)
jukebox.c:134: error: ‘LIBMTP_FILETYPE_DOC’ undeclared here (not in a function)
jukebox.c:135: error: ‘LIBMTP_FILETYPE_XML’ undeclared here (not in a function)
jukebox.c:136: error: ‘LIBMTP_FILETYPE_XLS’ undeclared here (not in a function)
jukebox.c:137: error: ‘LIBMTP_FILETYPE_PPT’ undeclared here (not in a function)
jukebox.c:138: error: ‘LIBMTP_FILETYPE_MHT’ undeclared here (not in a function)
jukebox.c:139: error: ‘LIBMTP_FILETYPE_JP2’ undeclared here (not in a function)
jukebox.c:140: error: ‘LIBMTP_FILETYPE_JPX’ undeclared here (not in a function)
jukebox.c: In function ‘flush_usage’:
jukebox.c:1150: error: ‘LIBMTP_mtpdevice_t’ has no member named ‘storage’
jukebox.c:1151: error: ‘LIBMTP_mtpdevice_t’ has no member named ‘storage’
jukebox.c:1151: error: ‘mtp_filetype_description_t’ has no member named ‘MaxCapacity’
jukebox.c:1151: warning: assignment makes integer from pointer without a cast
jukebox.c:1152: error: ‘LIBMTP_mtpdevice_t’ has no member named ‘storage’
jukebox.c:1152: error: ‘mtp_filetype_description_t’ has no member named ‘FreeSpaceInBytes’
jukebox.c:1152: warning: assignment makes integer from pointer without a cast
jukebox.c: In function ‘scan_thread’:
jukebox.c:1425: warning: assignment makes pointer from integer without a cast
jukebox.c:1585: warning: assignment makes pointer from integer without a cast
make[1]: *** [jukebox.o] Error 1
make[1]: Leaving directory `/home/jeff/gnomad_install/gnomad2-2.8.11/src'
```

Then, after it shows up correctly under applications, it won't recognize my ZVM...
Anyone have a fix?

---

