---
title: "importing DVD's in Myth 8.04"
date: 2008-07-22
forum: Mythbuntu
---

### Post by Chizzah on 2008-07-22
I am attempting to import my dvd's into mythbuntu but have been unsuccessful.  Selecting import DVD under the optical disk menu, then setting up a job it does nothing.  It doesn't import anything any ideas?

---

### Post by jlagrone on 2008-07-22
Make sure you have the appropriate video folder and temp folder.  You'll need to use whatever you have them as in the settings.  I believe by default they are /var/lib/mythtv/video and /var/lib/mythtv/video/temp

---

### Post by nickrout on 2008-07-22
What do the logs say? we are not clairvoyant, and we do not have access to your machine.

---

### Post by Trollslayer on 2008-07-23
Can you play DVDs?

---

### Post by itsdaveperdue on 2008-07-25
I'm having a very similar issue (I think...don't know much about the original issue).

My logs show the following:

*When ripping to ISO*
```

09:00:58: a client socket has been opened
09:01:13: launching job: job dvd 2 1 -1 0 -1 /recordings_usb/media/video/DVD_TITLE
09:01:13: Using DVD source: /dev/dvd
09:01:18: ISO DVD image copy to: /recordings_usb/media/video/DVD_TITLE_001of
09:02:03: Error: DVDISOCopyThread dvd device read error
09:02:03: job failed: job dvd 2 1 -1 0 -1 /recordings_usb/media/video/DVD_TITLE

```

*When ripping to Good or Perfect or anything like that*
```

08:18:31: a client socket has been opened
08:19:17: launching job: job dvd 2 1 6 0 -1 /var/lib/mythtv/videos/DVD_TITLE
08:19:18: transcode command will be: transcode -i /var/lib/mythdvd/temp/DVD_TITLE/vob/ -g 720x480 -M 2 -V -X 2,0 -y xvid,null -o /dev/null --print_status 20 --color 0 -R 1,twopass.log
08:19:18: job thread beginning to rip dvd title
08:19:56: Error: DVDPerfectThread read failed for 92 blocks at 8172
08:19:57: job failed: job dvd 2 1 6 0 -1 /var/lib/mythtv/videos/DVD_TITLE
08:44:42: a client socket has been closed

```

I can play the DVD's just fine.  Any ideas?

---

