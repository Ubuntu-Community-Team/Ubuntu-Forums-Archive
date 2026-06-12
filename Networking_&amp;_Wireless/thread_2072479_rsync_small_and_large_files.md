---
title: "rsync small and large files"
date: 2012-10-17
forum: Networking &amp; Wireless
---

### Post by Mr.Dee on 2012-10-17
So I have 140gigs worth of family photos and videos.  I have unlimited storage with a domain.  So I would like to use that storage to back up these files.  I already have a local backup so now I would like a backup in the cloud.  I have read on rsync and that seems the way I would like to go.

I will probably do something like
```
 rsync -e 'ssh -p 1234' -azv /directory/blahblah  blah@blah.com:/directory/blahblah 
```

I'll probably need to run this for a while or stop it and continue.  My concern is how rsync handles large files... if I stop the backup in the middle of a large file will I be able to just continue where it left off or will it restart?  I'm hoping I don't have to be baby sit too much.  Should I always run rsync with --partial?

Advice?  Thanks in advance.

---

### Post by papibe on 2012-10-18
Hi Mr.Dee.

> **Mr.Dee said:**
> I have read on rsync and that seems the way I would like to go.
I like rsync a lot, and I use it extensively. However, let me point out some cons, just so you have a more complete picture:
[LIST]
[*]Although it can be used as a backup tool, its main purpose is mirroring, so for actual backup tool it would need more scripting (full backup, incremental, differential, etc).
[*]rsync works almost flawlessly on a LAN, but the game changes for a large transfer over the Internet (see link below).
[*]Most cloud services don't allow rsync to them. You can rsync to your cloud local drive, like UbuntuOne or Dropbox, but in general you can't rsync directly. AFAIK, only paid services allow it, like Amazon S3 for example.
[/LIST]
> **Mr.Dee said:**
> if I stop the backup in the middle of a large file will I be able to just continue where it left off or will it restart
Yes, but not by itself, you would need to script it (see link example below).
> **Mr.Dee said:**
> Should I always run rsync with --partial?
I would recommend it, yes.

Take a look at this [thread]("http://ubuntuforums.org/showthread.php?t=1861143&highlight=rsync+partial+lan+internet"). There are both rsync options and scripting to take care of these concerns.

I hope that helps. Let us know how it goes.
Regards.

---

### Post by Mr.Dee on 2012-10-19
thanks for your reply papibe, and for the link to that thread. So far rsync has been working ok. I have debian server I am uploading to. I'll start adding --partial and consider keepalive. So far everything has been stable. I've run rsync for up to 8 hours without trouble.

---

