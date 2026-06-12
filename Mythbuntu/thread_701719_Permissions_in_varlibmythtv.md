---
title: "Permissions in /var/lib/mythtv"
date: 2008-02-19
forum: Mythbuntu
---

### Post by Levander on 2008-02-19
Can someone replay and post the output of these two commands?

```

ls -ld /var/lib/mythtv
ls -ld /var/lib/mythtv/*

```

I just mounted another disk to store all my recordings on.  And, I think I screwed up the permissions in those directory.

---

### Post by Nikas on 2008-02-19
> **Levander said:**
> Can someone replay and post the output of these two commands?

```

ls -ld /var/lib/mythtv
ls -ld /var/lib/mythtv/*

```

I just mounted another disk to store all my recordings on.  And, I think I screwed up the permissions in those directory.

Hello.

I gave you the output on IRC but i think you missed it. :)

```

ls -ld /var/lib/mythtv/*
drwxrwsr-x 5 mythtv mythtv  4096 2008-02-19 14:14 /var/lib/mythtv/music
drwxrwxr-x 8 mythtv mythtv  4096 2008-02-19 15:07 /var/lib/mythtv/pictures
drwxrwsr-x 4 mythtv mythtv 32768 2008-02-19 20:30 /var/lib/mythtv/recordings
drwxrwxr-x 2 mythtv mythtv  4096 2008-02-18 16:36 /var/lib/mythtv/videos

ls -ld /var/lib/mythtv
drwxr-xr-x 6 root root 4096 2008-02-18 00:22 /var/lib/mythtv
```

---

### Post by Levander on 2008-02-21
Great, thanks.  That did it.  Apparently when you rip a DVD and have the permissions wrong for the videos directory, you have to sit there and wait the entire time for the rip to complete, but then the process dies without an error message message.  And, it deletes the rip out of the temp directory, so you're left with nothing.  You have to figure out on your own what went wrong and start the process from scratch.

---

