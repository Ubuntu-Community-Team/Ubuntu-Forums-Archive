---
title: "can't play read-only-files"
date: 2013-01-06
forum: Mythbuntu
---

### Post by whocares02 on 2013-01-06
Mythbuntu's internal player doesn't play files (avi, mpg, ...) from DVD. As soon as I copy them to a local folder, playing is no problem anymore. I think it's because of the file-permissions, though I'm not quiet sure. I set umask to 002 in /etc/profile but of course this alone won't help. What can I do to make mythbuntu play files from read-only-media?

---

### Post by thaibuntu on 2013-02-05
Assuming that your DVD ROM Drive mounts to somewhere in /media, try changing the settings on /media to give the mythtv group access to the directory. You may have the access that mythtv doesn't have.

Something like:
```
sudo chgrp -R mythtv /media
```
and
```
chmod g+r -R /media
```

---

### Post by topcat5 on 2013-02-06
I'd recommend just making mythtv the owner of the files.  You should not need to change the permissions.  

```

chown -R mythtv.mythtv *filename*

```

"-R" makes it recursive so take care where you issue it. :)

If you do this, and mythtv is the ID running the BE, then you can manipulate and delete the file from the myth menus after tha.

---

### Post by furything on 2013-02-06
This is interesting as I have only played dvds or files from my video library.
I am guessing this is with all formats so mkv mp4 mpg etc.

May try this out this evening to see what happens.

For optical disc playback there are a number of params.

Have you tried googling to see what they are and if you need to specify some other param for read only?

---

