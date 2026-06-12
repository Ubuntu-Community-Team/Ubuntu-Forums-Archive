---
title: "File deleted, metadata still in database"
date: 2013-05-02
forum: Mythbuntu
---

### Post by larsolav on 2013-05-02
Good evening all.
I may have done something a little bit not too smart. It turned out that for some weird reasons the recordings from the first day my new Mythbox was set up did not list the mythtv user as the owner. So Mythtv could not delete the files. Before I figured out what the problem was, I had manually deleted one of the files from the command line. Now I keep getting the error below in my backend log. No programs show up in mythweb or on the frontend for 12/30/12 at 7:30 pm.
```
22:22:08 Backend mythlogserver: mythbackend[1786]: E CoreContext programinfo.cpp:2284 (GetPlaybackURL) ProgramInfo(3132_20121230193000.mpg): GetPlaybackURL: '3132_20121230193000.mpg' should be local, but it can not be found.
May  2 22:22:08 Backend mythlogserver: mythbackend[1786]: E CoreContext mainserver.cpp:2622 (DoHandleDeleteRecording) ERROR when trying to delete file: GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/Backend/3132_20121230193000.mpg. File doesn't exist.  Database metadata will not be removed.

```
How can I remove the database metadata? Will I have to edit mythconverg? Is there an easier way?

Cheers!

---

### Post by klc5555 on 2013-05-03
If the show doesn't appear in the frontend for you to delete its metadata in the usual way, then one standard tool that should work is find_orphans.py [http://www.mythtv.org/wiki/Find_orphans.py](http://www.mythtv.org/wiki/Find_orphans.py)

---

### Post by SlugSlug on 2013-05-03
Guess you could try cd to the directory and use touch 
```
 touch 3132_20121230193000.mpg
```

---

### Post by larsolav on 2013-05-03
Thank you both! Both look like great suggestions. I will try them out tonight. Guess I will first try creating the file using touch and see if it gets deleted with a happy backend log. Then if that does not work do the find_orphans.py script. But I am on 0.26, so don't know if the script will work.

Cheers1

---

### Post by larsolav on 2013-05-06
> **SlugSlug said:**
> Guess you could try cd to the directory and use touch 
```
 touch 3132_20121230193000.mpg
```

That did the trick!
Thanks!!!!

---

