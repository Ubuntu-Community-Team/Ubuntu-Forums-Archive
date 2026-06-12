---
title: "How to set up two partition Mythbuntu"
date: 2013-04-07
forum: Mythbuntu
---

### Post by SteveH0 on 2013-04-07
[TABLE="class: msg-table"]
[TR="class: msg"]
[TD="class: msg-user"][/TD]
[TD="class: msg-data"]I  had a hard drive crash and started again with a clean install of 12.04 mythbuntu. 

 On  a previous release, there was a single partition, and so I figured that I would  have a better chance of saving my data if I kept programs and data  on separate partitions.  Now I can set schedules, but nothing records.   Before I repartition and reinstall, does anyone have troubleshooting  steps that I could use to see why the programs aren't being recorded?

I particularly would like to verify that my permissions are set properly.
[/TD]
[/TR]
[TR="class: msg"]
[TD="class: msg-timestamp"][/TD]
[TD="class: msg-user"]SteveH0[/TD]
[/TR]
[TR="class: msg"]
[TD="class: msg-timestamp"][/TD]
[TD="class: msg-data"][/TD]
[/TR]
[/TABLE]

---

### Post by PhilWig on 2013-04-07
Presumably you mean two partitions plus swap.  What is on each of the two?  Root on one, what on the other?  Use df to check.

Recordings are normally held in /var/lib/mythtv/recordings.  I've seen references to problems if this is the top level directory of the partition, but /var/lib/mythtv is okay.

Do you see anything in the backend log?  Check particularly at the times you expected the recording to start and end.
Do:   less /var/log/mythtv/mythbackend.log

Phil

---

### Post by steeldriver on 2013-04-07
yes definitely check the permissions (and ownership) 

```
$ tree -pugd /var/lib/mythtv
/var/lib/mythtv
&#9500;&#9472;&#9472; [drwxrwsr-x mythtv   mythtv  ]  banners
&#9500;&#9472;&#9472; [drwxrwsr-x mythtv   mythtv  ]  bare-client
&#9500;&#9472;&#9472; [drwxrwsr-x mythtv   mythtv  ]  coverart
&#9500;&#9472;&#9472; [drwxrwsr-x mythtv   mythtv  ]  db_backups
&#9500;&#9472;&#9472; [drwxrwsr-x mythtv   mythtv  ]  fanart
&#9500;&#9472;&#9472; [drwxrwsr-x mythtv   mythtv  ]  livetv
&#9500;&#9472;&#9472; [drwxrwsr-x mythtv   mythtv  ]  music
&#9500;&#9472;&#9472; [drwxrwxr-x mythtv   mythtv  ]  pictures
&#9500;&#9472;&#9472; [drwxrwsr-x mythtv   mythtv  ]  recordings
&#9500;&#9472;&#9472; [drwxrwsr-x mythtv   mythtv  ]  screenshots
&#9500;&#9472;&#9472; [drwxrwsr-x mythtv   mythtv  ]  streaming
&#9500;&#9472;&#9472; [drwxrwsr-x mythtv   mythtv  ]  trailers
&#9492;&#9472;&#9472; [drwxrwsr-x mythtv   mythtv  ]  videos
```

(drwxrwsr-x is octal mode 2775 if you need to chmod them)

```
$ stat -c '%a' /var/lib/mythtv/recordings
2775
```

I seem to remember having a similar issue when I first moved my mythtv dirs off the root filesystem

---

### Post by SteveH0 on 2013-04-07
Yes, you are correct, Phil.  I meant two partitions plus swap.  I set up a smaller partition for root, and I set the other one up for /home.  It has been a couple of months, but I either hard linked /var/lib/mythtv to a sub-directory under /home, or I configured the repository for the videos by name on a /home subdirectory.

I'll fire up the beastie and check the log, which, honestly, I forgot about. {Duh!}

Thanks for the response,
   Steve

---

### Post by SteveH0 on 2013-04-07
And thank you for the perms, which will also come in handy.  I wonder, if I did do the hard-link, does the link need the permissions, or does it just pick them up from the destination?

---

