---
title: "Joining two recordings?"
date: 2008-01-23
forum: Mythbuntu
---

### Post by browndog289 on 2008-01-23
Hello

My mythTV system has recorded two episodes of a programme which were shown back to back. Unfortunately it stopped recording the first episode before it finished and started on the second.

Is there any way I can cut the end of the first episode from the second recording and paste it on to the end of the first recording within MythTV?

Thanks

browndog

---

### Post by novellahub on 2008-01-23
```

cat file1.mpg file2.mpg > file1and2.mpg

```

After combining them, I would transcode the combined file cut out any unwanted sections.

---

### Post by browndog289 on 2008-01-24
Would that not damage the MPEG file as the headers would be wrong?

Also I really need to do it through MythTV and not the command line.

---

### Post by novellahub on 2008-01-25
> **browndog289 said:**
> Would that not damage the MPEG file as the headers would be wrong?

Also I really need to do it through MythTV and not the command line.


See here:

[http://ubuntuforums.org/showthread.php?t=85718](http://ubuntuforums.org/showthread.php?t=85718)

[http://www.knoppmythwiki.org/index.php?page=LinuxTips](http://www.knoppmythwiki.org/index.php?page=LinuxTips)

[http://www.knoppmyth.net/phpBB2/viewtopic.php?t=12348](http://www.knoppmyth.net/phpBB2/viewtopic.php?t=12348)

---

