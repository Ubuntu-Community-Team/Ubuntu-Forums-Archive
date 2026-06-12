---
title: "Confused about autoexpire vs deletion"
date: 2010-05-22
forum: Mythbuntu
---

### Post by NautiusMaximus on 2010-05-22
I am aware that when I delete a recording, it isn't really deleted. It is merely marked as deleted, and can easily be undeleted if desired. I'm very happy with that, as it protects me from deleting something I didn't want to delete.

However, I do want things I delete to be really deleted eventually. My hard drive is filling up worryingly quickly. I had thought I'd set my system to really delete things 7 days after I told it to delete, but I see I still have some recordings hanging around that I deleted considerably more than 7 days ago.

Perhaps I've misunderstood how some of the settings work? From MythTV frontend, I choose Setup / TV Settings /General and then go to the page labelled General (AutoExpire). I have set "Deleted Max Age" as 7, which I thought would mean that recordings marked as deleted would really be deleted after 7 days, but clearly it doesn't.

Also on that page, I have ticked "AutoExpire Instead of Delete Recording". My understanding is that if I don't tick that, then if I delete a recording it would be genuinely deleted straight away. Is that correct?

Is it possible to achieve what I want to do (ie deleted recordings to disappear forever after 7 days)? If so, what do I need to do?

Mythbuntu 9.10.

Thanks
NM

---

### Post by tgm4883 on 2010-05-22
> **NautiusMaximus said:**
> I am aware that when I delete a recording, it isn't really deleted. It is merely marked as deleted, and can easily be undeleted if desired. I'm very happy with that, as it protects me from deleting something I didn't want to delete.

However, I do want things I delete to be really deleted eventually. My hard drive is filling up worryingly quickly. I had thought I'd set my system to really delete things 7 days after I told it to delete, but I see I still have some recordings hanging around that I deleted considerably more than 7 days ago.

Perhaps I've misunderstood how some of the settings work? From MythTV frontend, I choose Setup / TV Settings /General and then go to the page labelled General (AutoExpire). I have set "Deleted Max Age" as 7, which I thought would mean that recordings marked as deleted would really be deleted after 7 days, but clearly it doesn't.

Also on that page, I have ticked "AutoExpire Instead of Delete Recording". My understanding is that if I don't tick that, then if I delete a recording it would be genuinely deleted straight away. Is that correct?

Is it possible to achieve what I want to do (ie deleted recordings to disappear forever after 7 days)? If so, what do I need to do?

Mythbuntu 9.10.

Thanks
NM

Odd that it isn't deleting the 'deleted' recordings after 7 days, as that is what that setting means. Check the backend logs and see if there are any errors.

You mention that "My hard drive is filling up worryingly quickly." Is there a reason you want a bunch of unused space on your disk? Depending on what you are trying to achieve, there is also a setting that will have MythTV always keep a certain amount of free space.

---

### Post by NautiusMaximus on 2010-05-22
> **tgm4883 said:**
> Odd that it isn't deleting the 'deleted' recordings after 7 days, as that is what that setting means. Check the backend logs and see if there are any errors.

You mention that "My hard drive is filling up worryingly quickly." Is there a reason you want a bunch of unused space on your disk? Depending on what you are trying to achieve, there is also a setting that will have MythTV always keep a certain amount of free space.

There are 3 reasons why I want the deleted recordings gone. First, if my disk fills up, problems will no doubt ensue. Yes, I know it's supposed to delete recordings once disk space runs low, but apparently it's also supposed to delete recordings after 7 days. I'd feel more comfortable if things were being deleted when they should be.

Second, I have more limited space for backups (on an external hard drive) than on my hard disk. Backing up all my recordings, including the deleted ones, is taking up more space than necessary.

Third, I often watch recordings in another room via a Zyxel media streamer, which makes use of the UPnP server feature of my MythTV box. It doesn't seem to be smart enough to tell the difference between normal recordings and deleted ones, and it can be a struggle trying to find the right episode to watch when all the deleted ones are showing up as well.

Thanks for the tip about the backend logs. I shall check and come back with what I find.

---

### Post by NautiusMaximus on 2010-05-22
OK, it was clearly a good plan to check the backend log. There is a very obvious error in there, which I am fairly sure is the cause of old recordings not being deleted.

This is what I found in the log:

```
2010-04-01 07:11:04.301 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-04-01 07:11:04.362 Expiring 2402 MBytes for 1002 @ Fri Jan 29 21:00:00 2010 => Empire of the Seas "How the Navy Forged the Modern World. High Tide"
2010-04-01 07:11:04.420 ProgramInfo, Error: GetPlaybackURL: '1002_20100129210000.mpg' should be local, but it can not be found.
2010-04-01 07:11:04.492 ERROR when trying to delete file: /GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/htpc/1002_20100129210000.mpg. File doesn't exist.  Database metadata will not be removed.
2010-04-01 07:13:53.027 Reschedule requested for id -1.
2010-04-01 07:13:53.726 Scheduled 29 items in 0.7 = 0.53 match + 0.17 place

```

The same messages recur every 15 minutes, identical apart from the timestamp, and have been doing so for weeks.

I've checked, and the file that it says doesn't exist really doesn't exist. So presumably it tries to delete it, finds that it can't, and throws a hissy fit and gives up on deleting files altogether, right?

Any idea what I could do to fix it?

---

### Post by ian dobson on 2010-05-22
Hi,

Just delete the recording from your frontend. Also having only 1Gb as reserve isn't much. Maybe set it to a larger value (maybe the average size of several recordings)

Regards
Ian Dobson

---

### Post by tgm4883 on 2010-05-22
Maybe create the file so the backend can delete it?

---

### Post by NautiusMaximus on 2010-05-23
OK, we're making progress, although I don't think it's solved yet. 

I created a file with the filename that MythTV was expecting. This didn't seem to delete itself, but it did disappear when I deleted it from MythTV frontend.

So the recurrent error message I had before has now stopped.

However, there are still deleted recordings hanging around that are considerably more than 7 days old. I assume that, since the original error message was recurring every 15 minutes, MythTV is trying to delete old recordings every 15 minutes, correct?

I now have new error messages in my backend log. They look like this:

```
2010-05-23 12:33:34.586 MainServer::ANN Monitor
2010-05-23 12:33:34.704 adding: htpc as a client (events: 0)
2010-05-23 12:33:34.761 MainServer::ANN Monitor
2010-05-23 12:33:34.827 adding: htpc as a client (events: 1)
2010-05-23 12:33:39.333 ProgramInfo, Error: GetPlaybackURL: '1309_20100522040000.mpg' should be local, but it can not be found.
2010-05-23 12:33:39.397 ProgramInfo, Error: GetPlaybackURL: '1307_20100517060000.mpg' should be local, but it can not be found.
2010-05-23 12:33:39.453 ProgramInfo, Error: GetPlaybackURL: '1309_20100515090000.mpg' should be local, but it can not be found.
2010-05-23 12:33:39.509 ProgramInfo, Error: GetPlaybackURL: '1307_20100510060000.mpg' should be local, but it can not be found.
2010-05-23 12:33:39.565 ProgramInfo, Error: GetPlaybackURL: '1309_20100508040000.mpg' should be local, but it can not be found.
2010-05-23 12:33:39.620 ProgramInfo, Error: GetPlaybackURL: '1309_20100506090000.mpg' should be local, but it can not be found.
2010-05-23 12:33:39.676 ProgramInfo, Error: GetPlaybackURL: '1307_20100503060000.mpg' should be local, but it can not be found.
2010-05-23 12:33:39.734 ProgramInfo, Error: GetPlaybackURL: '1307_20100426060000.mpg' should be local, but it can not be found.
2010-05-23 12:33:39.789 ProgramInfo, Error: GetPlaybackURL: '1307_20100419060000.mpg' should be local, but it can not be found.
2010-05-23 12:33:39.845 ProgramInfo, Error: GetPlaybackURL: '1307_20100412060000.mpg' should be local, but it can not be found.
2010-05-23 12:33:39.889 ProgramInfo, Error: GetPlaybackURL: '1307_20100405060000.mpg' should be local, but it can not be found.
2010-05-23 12:33:39.949 ProgramInfo, Error: GetPlaybackURL: '1308_20100217030000.mpg' should be local, but it can not be found.
2010-05-23 12:33:39.987 ProgramInfo, Error: GetPlaybackURL: '1308_20100217020000.mpg' should be local, but it can not be found.
2010-05-23 12:33:40.033 ProgramInfo, Error: GetPlaybackURL: '1308_20100211020000.mpg' should be local, but it can not be found.
2010-05-23 12:33:40.076 ProgramInfo, Error: GetPlaybackURL: '1308_20100210030000.mpg' should be local, but it can not be found.
2010-05-23 12:33:40.121 ProgramInfo, Error: GetPlaybackURL: '1308_20100210020000.mpg' should be local, but it can not be found.
2010-05-23 12:33:40.168 ProgramInfo, Error: GetPlaybackURL: '1308_20100203030000.mpg' should be local, but it can not be found.
2010-05-23 12:33:40.210 ProgramInfo, Error: GetPlaybackURL: '1308_20100203020000.mpg' should be local, but it can not be found.
2010-05-23 12:33:40.257 ProgramInfo, Error: GetPlaybackURL: '1308_20100128040000.mpg' should be local, but it can not be found.
2010-05-23 12:33:40.299 ProgramInfo, Error: GetPlaybackURL: '1309_20100127233000.mpg' should be local, but it can not be found.
2010-05-23 12:33:40.346 ProgramInfo, Error: GetPlaybackURL: '1309_20100120233000.mpg' should be local, but it can not be found.
2010-05-23 12:33:40.388 ProgramInfo, Error: GetPlaybackURL: '1308_20100120040000.mpg' should be local, but it can not be found.
2010-05-23 12:33:40.433 ProgramInfo, Error: GetPlaybackURL: '1309_20100119233000.mpg' should be local, but it can not be found.
2010-05-23 12:33:40.480 ProgramInfo, Error: GetPlaybackURL: '1308_20100113041000.mpg' should be local, but it can not be found.
2010-05-23 12:33:40.522 ProgramInfo, Error: GetPlaybackURL: '1309_20100112233000.mpg' should be local, but it can not be found.
2010-05-23 12:33:40.609 ProgramInfo, Error: GetPlaybackURL: '13866_20090521220000.mpg' should be local, but it can not be found.
2010-05-23 12:33:40.662 ProgramInfo, Error: GetPlaybackURL: '5228_20090402073445.mpg' should be local, but it can not be found.
2010-05-23 12:33:40.701 ProgramInfo, Error: GetPlaybackURL: '5164_20090402073414.mpg' should be local, but it can not be found.
2010-05-23 12:33:40.751 ProgramInfo, Error: GetPlaybackURL: '5164_20090222210000.mpg' should be local, but it can not be found.
2010-05-23 12:33:45.519 Reschedule requested for id -1.
2010-05-23 12:33:45.740 Scheduled 19 items in 0.2 = 0.07 match + 0.15 place
2010-05-23 12:34:11.169 ProgramInfo, Error: GetPlaybackURL: '1309_20100522040000.mpg' should be local, but it can not be found.
2010-05-23 12:34:11.252 ProgramInfo, Error: GetPlaybackURL: '1307_20100517060000.mpg' should be local, but it can not be found.
2010-05-23 12:34:11.307 ProgramInfo, Error: GetPlaybackURL: '1309_20100515090000.mpg' should be local, but it can not be found.
2010-05-23 12:34:11.363 ProgramInfo, Error: GetPlaybackURL: '1307_20100510060000.mpg' should be local, but it can not be found.
2010-05-23 12:34:11.419 ProgramInfo, Error: GetPlaybackURL: '1309_20100508040000.mpg' should be local, but it can not be found.
2010-05-23 12:34:11.474 ProgramInfo, Error: GetPlaybackURL: '1309_20100506090000.mpg' should be local, but it can not be found.
2010-05-23 12:34:11.530 ProgramInfo, Error: GetPlaybackURL: '1307_20100503060000.mpg' should be local, but it can not be found.
2010-05-23 12:34:11.588 ProgramInfo, Error: GetPlaybackURL: '1307_20100426060000.mpg' should be local, but it can not be found.
2010-05-23 12:34:11.643 ProgramInfo, Error: GetPlaybackURL: '1307_20100419060000.mpg' should be local, but it can not be found.
2010-05-23 12:34:11.699 ProgramInfo, Error: GetPlaybackURL: '1307_20100412060000.mpg' should be local, but it can not be found.
2010-05-23 12:34:11.754 ProgramInfo, Error: GetPlaybackURL: '1307_20100405060000.mpg' should be local, but it can not be found.
2010-05-23 12:34:11.826 ProgramInfo, Error: GetPlaybackURL: '1308_20100217030000.mpg' should be local, but it can not be found.
2010-05-23 12:34:11.886 ProgramInfo, Error: GetPlaybackURL: '1308_20100217020000.mpg' should be local, but it can not be found.
2010-05-23 12:34:11.943 ProgramInfo, Error: GetPlaybackURL: '1308_20100211020000.mpg' should be local, but it can not be found.
2010-05-23 12:34:11.997 ProgramInfo, Error: GetPlaybackURL: '1308_20100210030000.mpg' should be local, but it can not be found.
2010-05-23 12:34:12.042 ProgramInfo, Error: GetPlaybackURL: '1308_20100210020000.mpg' should be local, but it can not be found.
2010-05-23 12:34:12.090 ProgramInfo, Error: GetPlaybackURL: '1308_20100203030000.mpg' should be local, but it can not be found.
2010-05-23 12:34:12.131 ProgramInfo, Error: GetPlaybackURL: '1308_20100203020000.mpg' should be local, but it can not be found.
2010-05-23 12:34:12.178 ProgramInfo, Error: GetPlaybackURL: '1308_20100128040000.mpg' should be local, but it can not be found.
2010-05-23 12:34:12.220 ProgramInfo, Error: GetPlaybackURL: '1309_20100127233000.mpg' should be local, but it can not be found.
2010-05-23 12:34:12.267 ProgramInfo, Error: GetPlaybackURL: '1309_20100120233000.mpg' should be local, but it can not be found.
2010-05-23 12:34:12.309 ProgramInfo, Error: GetPlaybackURL: '1308_20100120040000.mpg' should be local, but it can not be found.
2010-05-23 12:34:12.354 ProgramInfo, Error: GetPlaybackURL: '1309_20100119233000.mpg' should be local, but it can not be found.
2010-05-23 12:34:12.401 ProgramInfo, Error: GetPlaybackURL: '1308_20100113041000.mpg' should be local, but it can not be found.
2010-05-23 12:34:12.443 ProgramInfo, Error: GetPlaybackURL: '1309_20100112233000.mpg' should be local, but it can not be found.
2010-05-23 12:34:12.544 ProgramInfo, Error: GetPlaybackURL: '13866_20090521220000.mpg' should be local, but it can not be found.
2010-05-23 12:34:12.594 ProgramInfo, Error: GetPlaybackURL: '5228_20090402073445.mpg' should be local, but it can not be found.
2010-05-23 12:34:12.633 ProgramInfo, Error: GetPlaybackURL: '5164_20090402073414.mpg' should be local, but it can not be found.
2010-05-23 12:34:12.683 ProgramInfo, Error: GetPlaybackURL: '5164_20090222210000.mpg' should be local, but it can not be found.
2010-05-23 12:34:21.474 MainServer::ANN Monitor
2010-05-23 12:34:21.542 adding: htpc as a client (events: 0)
2010-05-23 12:34:21.589 ProgramInfo, Error: GetPlaybackURL: '5164_20090222210000.mpg' should be local, but it can not be found.
2010-05-23 12:34:21.644 ProgramInfo, Error: GetPlaybackURL: '5164_20090222210000.mpg' should be local, but it can not be found.
2010-05-23 12:34:21.687 Preview Error: Run() file not local: '/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/htpc/5164_20090222210000.mpg'
2010-05-23 12:34:21.732 MainServer: Failed to make preview image.
2010-05-23 12:38:28.559 AutoExpire: CalcParams(): Max required Free Space: 100.0 GB w/freq: 15 min
2010-05-23 12:39:39.925 Reschedule requested for id -1.
2010-05-23 12:39:40.164 Scheduled 19 items in 0.2 = 0.06 match + 0.17 place
2010-05-23 12:45:03.229 Reschedule requested for id -1.
2010-05-23 12:45:03.445 Scheduled 19 items in 0.2 = 0.06 match + 0.16 place
2010-05-23 12:51:32.095 Reschedule requested for id -1.
2010-05-23 12:51:32.396 Scheduled 19 items in 0.3 = 0.07 match + 0.22 place
2010-05-23 12:53:28.704 AutoExpire: CalcParams(): Max required Free Space: 100.0 GB w/freq: 15 min
2010-05-23 12:55:49.912 Reschedule requested for id -1.
2010-05-23 12:55:50.195 Scheduled 19 items in 0.3 = 0.08 match + 0.19 place
2010-05-23 13:01:13.119 Reschedule requested for id -1.
2010-05-23 13:01:13.433 Scheduled 19 items in 0.3 = 0.15 match + 0.15 place
2010-05-23 13:06:06.568 Reschedule requested for id -1.
2010-05-23 13:06:07.227 Scheduled 19 items in 0.7 = 0.50 match + 0.15 place
```

Any idea what's going on here?

BTW, thanks for the suggestion about the 1 GB free space, Ian. I've now changed it to make sure there is 100 GB of free space. That may be over the top, but I can always reduce it in due course once I've got this deletion business solved.

---

### Post by NautiusMaximus on 2010-05-29
OK, I think I'm making progress. Turns out that the files it couldn't find were never recorded in the first place, mostly (but not entirely) because they were recorded from encrypted channels (I've posted another thread about that, and think I've solved it).

Another problem was that MythTV didn't have permission to delete some of the files. I suspect this was as a result of my last upgrade, when I did a clean install and restored all my media files manually. They ended up owned by the root user, and simply changing the owner to mythtv made the permission denied errors go away.

Since figuring all this out, I haven't had any more error messages, and some old files have been deleted. There are plenty more files that should have been deleted and haven't. I'm not sure yet whether that's because it's just taking its time to delete all the old files or whether there is another problem.

I shall post back in a day or two when that is clearer.

---

### Post by NautiusMaximus on 2010-05-30
Well, I'm starting to have my doubts about whether this is really fixed. There are no more error messages in the log, but there are plenty of old files that should be deleted and which haven't been. As far as I can tell from the log, it looks like it is thinking about deleting them and then rescheduling to another time, and then just keeps putting it off (a bit like some of the things on my own to-do list!)

Here is a representative extract from the backend log. Does anyone have any idea what's going on?

```
2010-05-30 15:20:46.207 AutoExpire: CalcParams(): Max required Free Space: 100.0 GB w/freq: 15 min
2010-05-30 15:25:31.721 Reschedule requested for id -1.
2010-05-30 15:25:32.418 Scheduled 23 items in 0.7 = 0.52 match + 0.18 place
2010-05-30 15:31:21.246 Reschedule requested for id -1.
2010-05-30 15:31:21.493 Scheduled 23 items in 0.2 = 0.08 match + 0.16 place
2010-05-30 15:35:42.111 Reschedule requested for id -1.
2010-05-30 15:35:42.796 Scheduled 23 items in 0.7 = 0.50 match + 0.18 place
2010-05-30 15:35:46.767 AutoExpire: CalcParams(): Max required Free Space: 100.0 GB w/freq: 15 min
2010-05-30 15:36:27.276 UPnpMedia: BuildMediaMap VIDEO scan starting in :/media/disk2/mythtv/videos:
2010-05-30 15:36:27.372 UPnpMedia: BuildMediaMap Done. Found 28 objects
2010-05-30 15:39:00.566 Reschedule requested for id -1.
2010-05-30 15:39:01.245 Scheduled 23 items in 0.7 = 0.53 match + 0.15 place
2010-05-30 15:46:36.785 Reschedule requested for id -1.
2010-05-30 15:46:37.449 Scheduled 23 items in 0.7 = 0.50 match + 0.16 place
2010-05-30 15:50:46.886 AutoExpire: CalcParams(): Max required Free Space: 100.0 GB w/freq: 15 min
2010-05-30 15:50:58.857 Reschedule requested for id -1.
2010-05-30 15:50:59.531 Scheduled 23 items in 0.7 = 0.51 match + 0.16 place
2010-05-30 15:53:58.977 Reschedule requested for id -1.
2010-05-30 15:53:59.238 Scheduled 23 items in 0.3 = 0.08 match + 0.18 place
2010-05-30 16:01:08.386 Reschedule requested for id -1.
2010-05-30 16:01:09.063 Scheduled 23 items in 0.7 = 0.51 match + 0.16 place
2010-05-30 16:03:44.773 Reschedule requested for id -1.
2010-05-30 16:03:45.438 Scheduled 23 items in 0.7 = 0.50 match + 0.16 place
2010-05-30 16:05:47.452 AutoExpire: CalcParams(): Max required Free Space: 100.0 GB w/freq: 15 min
2010-05-30 16:06:33.430 UPnpMedia: BuildMediaMap VIDEO scan starting in :/media/disk2/mythtv/videos:
2010-05-30 16:06:33.502 UPnpMedia: BuildMediaMap Done. Found 28 objects
2010-05-30 16:09:03.197 Reschedule requested for id -1.
2010-05-30 16:09:03.957 Scheduled 23 items in 0.8 = 0.58 match + 0.18 place
2010-05-30 16:13:51.902 Reschedule requested for id -1.
2010-05-30 16:13:52.582 Scheduled 23 items in 0.7 = 0.51 match + 0.16 place
2010-05-30 16:17:02.258 MainServer::ANN Monitor
2010-05-30 16:17:02.340 adding: htpc as a client (events: 0)
2010-05-30 16:18:15.157 Reschedule requested for id -1.
2010-05-30 16:18:15.831 Scheduled 23 items in 0.7 = 0.51 match + 0.16 place
2010-05-30 16:20:48.013 AutoExpire: CalcParams(): Max required Free Space: 100.0 GB w/freq: 15 min
2010-05-30 16:23:42.860 Reschedule requested for id -1.
2010-05-30 16:23:43.546 Scheduled 23 items in 0.7 = 0.51 match + 0.17 place
2010-05-30 16:31:15.968 Reschedule requested for id -1.
2010-05-30 16:31:16.372 Scheduled 23 items in 0.4 = 0.23 match + 0.17 place
2
```

Thanks
NM

---

### Post by NautiusMaximus on 2010-06-08
OK, it seems to be fixed now. All a bit strange really. For several days, it ignored a whole load of recordings that were deleted well over a week previously, and then for no apparent reading it just started working. Didn't delete everything all at once, but over a period of about 3 days, everything got deleted. 

Now it seems to be working as it should, with the only deleted recordings that are still there those that have been deleted in the last 7 days.

Very strange, considering it wasn't working when I posted my last update and I didn't do anything to it in between. That's computers for you.

---

