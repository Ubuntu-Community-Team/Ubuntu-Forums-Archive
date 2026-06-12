---
title: "MythTV fixes 2:0.28.0+fixes.20160827.d9182ff"
date: 2016-08-28
forum: Mythbuntu
---

### Post by ian dobson on 2016-08-28
Hi All,

I've been running MythTV/Ubuntu for several years no without any major problems, yesterday I upgraded the backend to 2:0.28.0+fixes.20160827.d9182ff and since then I'm having problems with recording from my two DVB-C recorders.

**Software:**
Kernel : Linux alpha2 4.4.0-34-generic #53-Ubuntu SMP Wed Jul 27 16:06:39 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

**MythTV Backend Versions:**
ii  libmythtv-perl                        2:0.28.0+fixes.20160827.d9182ff-0ubuntu0mythbuntu2 all          Perl library to access some MythTV features
ii  mythtv-backend                        2:0.28.0+fixes.20160827.d9182ff-0ubuntu0mythbuntu2 amd64        Personal video recorder application (server)
ii  mythtv-common                         2:0.28.0+fixes.20160827.d9182ff-0ubuntu0mythbuntu2 amd64        Personal video recorder application (common data)
ii  mythtv-frontend                       2:0.28.0+fixes.20160827.d9182ff-0ubuntu0mythbuntu2 amd64        Personal video recorder application (client)
ii  mythtv-transcode-utils                2:0.28.0+fixes.20160827.d9182ff-0ubuntu0mythbuntu2 amd64        Utilities used for transcoding MythTV tasks
ii  php-mythtv                            2:0.28.0+fixes.20160827.d9182ff-0ubuntu0mythbuntu2 all          PHP Bindings for MythTV

**Tuner cards:**
[    7.943370] DVB: registering new adapter (KNC1 DVB-C MK3)
[    8.409608] budget_av 0000:08:00.0: DVB: registering adapter 0 frontend 0 (Philips TDA10023 DVB-C)...
[    8.409785] DVB: registering new adapter (Satelco EasyWatch DVB-C MK3)
[    8.849632] budget_av 0000:08:01.0: DVB: registering adapter 1 frontend 0 (Philips TDA10023 DVB-C)...

**Problem description:**
After booting the system or restarting Mythtv-Backend the first recording for both tuners works correctly. The second recording doesn't work, the system just creates a zero byte file. 
If I restart the mythtv-backend (systemctl stop  mythtv-backend/systemctl start  mythtv-backend) the recording works again for one recording for the tuner.
So it looks as if Mythtv can only record one program from a tuner before "blocking" (maybe it's leaving the turner open when the recording is finished, and can't open it again).
Note: I'm using over the air EIT.

Does anyone have any ideas?

Regards
Ian Dobson

---

### Post by ian dobson on 2016-08-28
Hi All,

OK, I've reduced the maximum number of recordings per tuner to 1 and it appears to be working (I've recorded 4 programs spread over both tuners and different channels without any zero byte recordings).

I'll leave this thread open "just in case" and update in a few days if everything is OK or NOT.

Regards
Ian Dobson

---

### Post by ian dobson on 2016-09-05
Hi All,

OK, recordings are working now, even with 2 recordings per tuner. Not sure what's changed but it's working again.

Regards
Ian Dobson

---

