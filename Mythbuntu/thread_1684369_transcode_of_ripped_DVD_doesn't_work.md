---
title: "transcode of ripped DVD doesn't work"
date: 2011-02-09
forum: Mythbuntu
---

### Post by jakev383 on 2011-02-09
So I import a DVD and select "excellent" quality so that it will transcode the movie down to something smaller. It rips the DVD fine, but fails on the transcode portion. And why does it use -o /dev/null?
Here's what the log shows:

```

01:53:59: launching job: job dvd 4 1 2 0 -1 /media/videos/Dive
01:53:59: transcode command will be: 'transcode -i /var/lib/mythdvd/temp/Dive/vob/ -g 720x480 -M 2 -y xvid,null -o /dev/null --progress_rate 20 --log_no_color -R 1,twopass.log'
01:53:59: job thread beginning to rip dvd title

01:57:31: job thread finished ripping dvd title
01:57:33: Error: Exiting runTranscode(1) transcode exit code: 1

01:57:34: job failed: job dvd 4 1 2 0 -1 /media/videos/Dive
01:58:39: a client socket has been closed

```

/media/videos is a NFS mount to my backend storage.
I google'd around some, but am not coming up with any real relevant results. Anyone have any tips/links/pointers?
Thanks!

---

### Post by nickrout on 2011-02-09
it uses -o /dev/null because it is the first pass of a 2 pass encode. The first pass is essentially to suss out the video and present info to the second pass so it can do a better job. 

The rest I can't help with sorry.

---

### Post by klc5555 on 2011-02-09
> **jakev383 said:**
> So I import a DVD and select "excellent" quality so that it will transcode the movie down to something smaller. It rips the DVD fine, but fails on the transcode portion. And why does it use -o /dev/null?
Here's what the log shows:

```

01:53:59: launching job: job dvd 4 1 2 0 -1 /media/videos/Dive
01:53:59: transcode command will be: 'transcode -i /var/lib/mythdvd/temp/Dive/vob/ -g 720x480 -M 2 -y xvid,null -o /dev/null --progress_rate 20 --log_no_color -R 1,twopass.log'
01:53:59: job thread beginning to rip dvd title

01:57:31: job thread finished ripping dvd title
01:57:33: Error: Exiting runTranscode(1) transcode exit code: 1

01:57:34: job failed: job dvd 4 1 2 0 -1 /media/videos/Dive
01:58:39: a client socket has been closed

```

/media/videos is a NFS mount to my backend storage.
I google'd around some, but am not coming up with any real relevant results. Anyone have any tips/links/pointers?
Thanks!

There were points in the development of mtd and transcode, before they were removed from mythtv, where mtd would pass params to transcode that were OK with an earlier version of transcode, but that a more current version of transcode no longer used.

To find out what transcode is objecting to, you can run the the command listed in the mtd log yourself from the command line: 

transcode -i /var/lib/mythdvd/temp/Dive/vob/ -g 720x480 -M 2 -y xvid,null -o /dev/null --progress_rate 20 --log_no_color -R 1,twopass.log

When the command bombs it likely will give you a more useful error message about what param went wrong in the terminal than you got from the mtd log.

---

### Post by nickrout on 2011-02-09
As this ability has been removed from mythtv as from 0.24, you are probably better to use one of the other solutions that are floating about. Read the archives here and on the users mailing list for ideas.

---

### Post by jakev383 on 2011-02-12
Thanks for the suggestions everyone. This was a fresh install as of a couple weeks ago, but did not realize that 10.04 was using myth 0.23.1. I'll look into updating, or just transcode on the backend machine manually.
Thanks.

---

