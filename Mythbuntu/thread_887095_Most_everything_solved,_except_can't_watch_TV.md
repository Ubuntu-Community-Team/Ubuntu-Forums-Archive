---
title: "Most everything solved, except can't watch TV"
date: 2008-08-11
forum: Mythbuntu
---

### Post by bt224 on 2008-08-11
Ok, thanks to all that have helped thus far. I can see the backend from another computer, see my guide, rip unprotected DVD's and watch them. But I can't watch TV. I can set to record, and the title will be in my recordings, however no video. I have read more than a few posts about "select watch TV screen goes black then back to the menu" but I never see any resolution. Anyone have any ideas?

AMD 64 3500, PVR-150 if that helps.

Thanks!

---

### Post by bt224 on 2008-08-11
Forgot to mention, running DirecTV

---

### Post by nickrout on 2008-08-11
what does your front end log say?

can you play the file using other software like mplayer or xine?

---

### Post by bt224 on 2008-08-11
No, it never really records anything. It shows taking up zero space. I'm thinking something along the lines of where/how I saved it or permissions.

---

### Post by tgm4883 on 2008-08-11
Post your /var/log/mythtv/backend.log file from your backend

---

### Post by nickrout on 2008-08-11
> **bt224 said:**
> No, it never really records anything. It shows taking up zero space. I'm thinking something along the lines of where/how I saved it or permissions.

so are there files in /var/lib/mythtv/recordings ?

---

### Post by nigel502 on 2008-08-12
What do you have your tuner setup as in your mythbackend-setup? I had the same problem with running it as a VLC (I think thats the acrynom - video for linux) driver, which the 150's are automatically setup as. 

If you enter mythbackend-setup and setup your tuner as a mpeg2 capture device you should be aok.

However if you've already done all of this and you are still getting nothing then I would suggest that the issue is on the DirectTV side of things. What region are you in? NTSC? Do you change channels through DirectTV's box or on your television set? If it's on the box side of things then you might need to figure out additional software/hardware solution to changing the box's channel through an IR Emitter.

---

### Post by bt224 on 2008-08-12
Thanks, I'll get on this tonight and post.

---

### Post by nickrout on 2008-08-12
> **nigel502 said:**
> What do you have your tuner setup as in your mythbackend-setup? I had the same problem with running it as a VLC (I think thats the acrynom - video for linux) driver, which the 150's are automatically setup as. 

If you enter mythbackend-setup and setup your tuner as a mpeg2 capture device you should be aok.



Its not automatically set up as anything. You have to choose from the list. V4L just happens to be the first in the list.

---

### Post by bt224 on 2008-08-14
I changed the card to an MPEG2.The only difference is that the screen is black a shorter time. I also have it set as -cable.

---

### Post by bt224 on 2008-08-14
Here's the main log:

2008-08-14 06:57:49.276 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-14 06:58:11.454 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-08-14 06:58:11.463 UPnpMedia: BuildMediaMap Done. Found 2 objects
2008-08-14 07:12:49.310 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-14 07:27:49.347 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-14 07:28:12.466 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-08-14 07:28:12.475 UPnpMedia: BuildMediaMap Done. Found 2 objects
2008-08-14 07:42:49.382 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-14 07:57:49.420 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-14 07:58:16.479 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-08-14 07:58:16.485 UPnpMedia: BuildMediaMap Done. Found 2 objects
2008-08-14 08:12:49.460 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-14 08:27:49.499 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-14 08:28:17.489 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-08-14 08:28:17.495 UPnpMedia: BuildMediaMap Done. Found 2 objects
2008-08-14 08:42:49.532 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-14 08:57:49.567 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-14 08:58:21.499 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-08-14 08:58:21.506 UPnpMedia: BuildMediaMap Done. Found 2 objects
2008-08-14 09:12:49.604 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-14 09:27:49.640 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-14 09:28:21.510 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-08-14 09:28:21.515 UPnpMedia: BuildMediaMap Done. Found 2 objects
2008-08-14 09:42:49.678 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-14 09:57:49.716 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-14 09:58:28.519 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-08-14 09:58:28.526 UPnpMedia: BuildMediaMap Done. Found 2 objects
2008-08-14 10:12:49.753 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-14 10:27:49.790 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-14 10:28:31.530 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-08-14 10:28:31.535 UPnpMedia: BuildMediaMap Done. Found 2 objects
2008-08-14 10:42:49.827 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-14 10:57:49.864 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-14 10:58:32.539 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-08-14 10:58:32.546 UPnpMedia: BuildMediaMap Done. Found 2 objects
2008-08-14 11:12:49.905 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-14 11:27:49.944 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-14 11:28:39.549 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-08-14 11:28:39.556 UPnpMedia: BuildMediaMap Done. Found 2 objects
2008-08-14 11:42:49.979 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-14 11:57:50.017 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-14 11:58:42.560 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-08-14 11:58:42.567 UPnpMedia: BuildMediaMap Done. Found 2 objects
2008-08-14 12:12:50.054 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-14 12:27:50.091 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-14 12:28:42.570 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-08-14 12:28:42.579 UPnpMedia: BuildMediaMap Done. Found 2 objects
2008-08-14 12:42:50.128 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-14 12:57:50.164 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-14 12:58:43.583 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-08-14 12:58:43.591 UPnpMedia: BuildMediaMap Done. Found 2 objects
2008-08-14 13:12:50.200 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-14 13:27:50.240 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-14 13:28:44.594 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-08-14 13:28:44.603 UPnpMedia: BuildMediaMap Done. Found 2 objects
2008-08-14 13:42:50.279 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-14 13:57:50.316 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-14 13:58:44.607 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-08-14 13:58:44.611 UPnpMedia: BuildMediaMap Done. Found 2 objects
2008-08-14 14:12:50.351 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-14 14:27:50.387 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-14 14:28:46.615 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-08-14 14:28:46.622 UPnpMedia: BuildMediaMap Done. Found 2 objects
2008-08-14 14:42:50.422 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-14 14:57:50.460 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-14 14:58:52.625 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-08-14 14:58:52.632 UPnpMedia: BuildMediaMap Done. Found 2 objects
2008-08-14 15:12:50.496 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-14 15:27:50.537 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-14 15:28:56.635 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-08-14 15:28:56.642 UPnpMedia: BuildMediaMap Done. Found 2 objects
2008-08-14 15:42:50.575 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-14 15:50:38.295 Running mythfilldatabase
2008-08-14 15:50:38.684 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-14 15:50:38.691 Empty LocalHostName.
2008-08-14 15:50:38.692 Using localhost value of bt224-desktop
2008-08-14 15:50:38.707 New DB connection, total: 1
2008-08-14 15:50:38.714 Connected to database 'mythconverg' at host: localhost
2008-08-14 15:50:38.716 Closing DB connection named 'DBManager0'
2008-08-14 15:50:38.718 Connected to database 'mythconverg' at host: localhost
2008-08-14 15:50:38.723 New DB connection, total: 2
2008-08-14 15:50:38.725 Connected to database 'mythconverg' at host: localhost
2008-08-14 15:50:38.729 Updating source #1 () with grabber schedulesdirect1
2008-08-14 15:50:38.732 No channels are configured to use grabber.
2008-08-14 15:50:38.733 
2008-08-14 15:50:38.734 Checking day @ offset 0, date: Thu Aug 14 2008
2008-08-14 15:50:38.737 Data refresh needed because no data exists for day @ offset 0 from 8PM - midnight.
2008-08-14 15:50:38.738 Refreshing data for Thu Aug 14 2008
2008-08-14 15:50:38.740 New DB DataDirect connection
2008-08-14 15:50:38.742 Connected to database 'mythconverg' at host: localhost
2008-08-14 15:50:38.745 Retrieving datadirect data.
2008-08-14 15:50:38.747 Grabbing data for Thu Aug 14 2008 offset 0
2008-08-14 15:50:38.748 From Thu Aug 14 05:00:00 2008 to Fri Aug 15 05:00:00 2008 (UTC)
2008-08-14 15:50:38.749 Grabbing listing data
--15:50:38--  [http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService](http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService)
           => `-'
Resolving webservices.schedulesdirect.tmsdatadirect.com... 206.18.98.175
Connecting to webservices.schedulesdirect.tmsdatadirect.com|206.18.98.175|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 401 Unauthorized
Authorization failed.
2008-08-14 15:50:39.199 Grab complete.  Actual data from  to  (UTC)
2008-08-14 15:50:39.205 Main temp tables populated.
2008-08-14 15:50:39.206 Updating myth channels.
2008-08-14 15:50:39.210 New DB connection, total: 3
2008-08-14 15:50:39.215 Connected to database 'mythconverg' at host: localhost
2008-08-14 15:50:39.220 DataDirect: Not inserting channels into disconnected source 1.
2008-08-14 15:50:39.221 Updating icons for sourceid: 1
2008-08-14 15:50:39.223 Channels updated.
2008-08-14 15:50:39.226 Did not find any new program data.
2008-08-14 15:50:39.236 
2008-08-14 15:50:39.237 Checking day @ offset 1, date: Fri Aug 15 2008
2008-08-14 15:50:39.237 Data Refresh always needed for tomorrow
2008-08-14 15:50:39.238 Refreshing data for Fri Aug 15 2008
2008-08-14 15:50:39.240 Retrieving datadirect data.
2008-08-14 15:50:39.241 Grabbing data for Thu Aug 14 2008 offset 1
2008-08-14 15:50:39.241 From Fri Aug 15 05:00:00 2008 to Sat Aug 16 05:00:00 2008 (UTC)
2008-08-14 15:50:39.246 Grabbing listing data
--15:50:39--  [http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService](http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService)
           => `-'
Resolving webservices.schedulesdirect.tmsdatadirect.com... 206.18.98.175
Connecting to webservices.schedulesdirect.tmsdatadirect.com|206.18.98.175|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 401 Unauthorized
Authorization failed.
2008-08-14 15:50:39.696 Grab complete.  Actual data from  to  (UTC)
2008-08-14 15:50:39.703 Main temp tables populated.
2008-08-14 15:50:39.707 Did not find any new program data.
2008-08-14 15:50:39.709 
2008-08-14 15:50:39.710 Checking day @ offset 2, date: Sat Aug 16 2008
2008-08-14 15:50:39.712 Data refresh needed because no data exists for day @ offset 2 from 8PM - midnight.
2008-08-14 15:50:39.714 Refreshing data for Sat Aug 16 2008
2008-08-14 15:50:39.715 Retrieving datadirect data.
2008-08-14 15:50:39.716 Grabbing data for Thu Aug 14 2008 offset 2
2008-08-14 15:50:39.717 From Sat Aug 16 05:00:00 2008 to Sun Aug 17 05:00:00 2008 (UTC)
2008-08-14 15:50:39.718 Grabbing listing data
--15:50:39--  [http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService](http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService)
           => `-'
Resolving webservices.schedulesdirect.tmsdatadirect.com... 206.18.98.175
Connecting to webservices.schedulesdirect.tmsdatadirect.com|206.18.98.175|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 401 Unauthorized
Authorization failed.
2008-08-14 15:50:40.035 Grab complete.  Actual data from  to  (UTC)
2008-08-14 15:50:40.039 Main temp tables populated.
2008-08-14 15:50:40.043 Did not find any new program data.
2008-08-14 15:50:40.044 
2008-08-14 15:50:40.045 Checking day @ offset 3, date: Sun Aug 17 2008
2008-08-14 15:50:40.047 Data refresh needed because no data exists for day @ offset 3 from 8PM - midnight.
2008-08-14 15:50:40.048 Refreshing data for Sun Aug 17 2008
2008-08-14 15:50:40.050 Retrieving datadirect data.
2008-08-14 15:50:40.051 Grabbing data for Thu Aug 14 2008 offset 3
2008-08-14 15:50:40.051 From Sun Aug 17 05:00:00 2008 to Mon Aug 18 05:00:00 2008 (UTC)
2008-08-14 15:50:40.052 Grabbing listing data
--15:50:40--  [http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService](http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService)
           => `-'
Resolving webservices.schedulesdirect.tmsdatadirect.com... 206.18.98.175
Connecting to webservices.schedulesdirect.tmsdatadirect.com|206.18.98.175|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 401 Unauthorized
Authorization failed.
2008-08-14 15:50:40.466 Grab complete.  Actual data from  to  (UTC)
2008-08-14 15:50:40.471 Main temp tables populated.
2008-08-14 15:50:40.475 Did not find any new program data.
2008-08-14 15:50:40.476 
2008-08-14 15:50:40.477 Checking day @ offset 4, date: Mon Aug 18 2008
2008-08-14 15:50:40.479 Data refresh needed because no data exists for day @ offset 4 from 8PM - midnight.
2008-08-14 15:50:40.481 Refreshing data for Mon Aug 18 2008
2008-08-14 15:50:40.482 Retrieving datadirect data.
2008-08-14 15:50:40.483 Grabbing data for Thu Aug 14 2008 offset 4
2008-08-14 15:50:40.484 From Mon Aug 18 05:00:00 2008 to Tue Aug 19 05:00:00 2008 (UTC)
2008-08-14 15:50:40.485 Grabbing listing data
--15:50:40--  [http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService](http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService)
           => `-'
Resolving webservices.schedulesdirect.tmsdatadirect.com... 206.18.98.175
Connecting to webservices.schedulesdirect.tmsdatadirect.com|206.18.98.175|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 401 Unauthorized
Authorization failed.
2008-08-14 15:50:41.008 Grab complete.  Actual data from  to  (UTC)
2008-08-14 15:50:41.015 Main temp tables populated.
2008-08-14 15:50:41.019 Did not find any new program data.
2008-08-14 15:50:41.020 
2008-08-14 15:50:41.021 Checking day @ offset 5, date: Tue Aug 19 2008
2008-08-14 15:50:41.025 Data refresh needed because no data exists for day @ offset 5 from 8PM - midnight.
2008-08-14 15:50:41.026 Refreshing data for Tue Aug 19 2008
2008-08-14 15:50:41.028 Retrieving datadirect data.
2008-08-14 15:50:41.029 Grabbing data for Thu Aug 14 2008 offset 5
2008-08-14 15:50:41.030 From Tue Aug 19 05:00:00 2008 to Wed Aug 20 05:00:00 2008 (UTC)
2008-08-14 15:50:41.031 Grabbing listing data
--15:50:41--  [http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService](http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService)
           => `-'
Resolving webservices.schedulesdirect.tmsdatadirect.com... 206.18.98.175
Connecting to webservices.schedulesdirect.tmsdatadirect.com|206.18.98.175|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 401 Unauthorized
Authorization failed.
2008-08-14 15:50:41.341 Grab complete.  Actual data from  to  (UTC)
2008-08-14 15:50:41.347 Main temp tables populated.
2008-08-14 15:50:41.351 Did not find any new program data.
2008-08-14 15:50:41.352 
2008-08-14 15:50:41.353 Checking day @ offset 6, date: Wed Aug 20 2008
2008-08-14 15:50:41.356 Data refresh needed because no data exists for day @ offset 6 from 8PM - midnight.
2008-08-14 15:50:41.357 Refreshing data for Wed Aug 20 2008
2008-08-14 15:50:41.358 Retrieving datadirect data.
2008-08-14 15:50:41.359 Grabbing data for Thu Aug 14 2008 offset 6
2008-08-14 15:50:41.360 From Wed Aug 20 05:00:00 2008 to Thu Aug 21 05:00:00 2008 (UTC)
2008-08-14 15:50:41.361 Grabbing listing data
--15:50:41--  [http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService](http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService)
           => `-'
Resolving webservices.schedulesdirect.tmsdatadirect.com... 206.18.98.175
Connecting to webservices.schedulesdirect.tmsdatadirect.com|206.18.98.175|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 401 Unauthorized
Authorization failed.
2008-08-14 15:50:41.900 Grab complete.  Actual data from  to  (UTC)
2008-08-14 15:50:41.903 Main temp tables populated.
2008-08-14 15:50:41.906 Did not find any new program data.
2008-08-14 15:50:41.908 
2008-08-14 15:50:41.910 Checking day @ offset 7, date: Thu Aug 21 2008
2008-08-14 15:50:41.913 Data refresh needed because no data exists for day @ offset 7 from 8PM - midnight.
2008-08-14 15:50:41.914 Refreshing data for Thu Aug 21 2008
2008-08-14 15:50:41.916 Retrieving datadirect data.
2008-08-14 15:50:41.917 Grabbing data for Thu Aug 14 2008 offset 7
2008-08-14 15:50:41.918 From Thu Aug 21 05:00:00 2008 to Fri Aug 22 05:00:00 2008 (UTC)
2008-08-14 15:50:41.919 Grabbing listing data
--15:50:41--  [http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService](http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService)
           => `-'
Resolving webservices.schedulesdirect.tmsdatadirect.com... 206.18.98.175
Connecting to webservices.schedulesdirect.tmsdatadirect.com|206.18.98.175|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 401 Unauthorized
Authorization failed.
2008-08-14 15:50:42.437 Grab complete.  Actual data from  to  (UTC)
2008-08-14 15:50:42.443 Main temp tables populated.
2008-08-14 15:50:42.447 Did not find any new program data.
2008-08-14 15:50:42.448 
2008-08-14 15:50:42.450 Checking day @ offset 8, date: Fri Aug 22 2008
2008-08-14 15:50:42.453 Data refresh needed because no data exists for day @ offset 8 from 8PM - midnight.
2008-08-14 15:50:42.454 Refreshing data for Fri Aug 22 2008
2008-08-14 15:50:42.456 Retrieving datadirect data.
2008-08-14 15:50:42.457 Grabbing data for Thu Aug 14 2008 offset 8
2008-08-14 15:50:42.458 From Fri Aug 22 05:00:00 2008 to Sat Aug 23 05:00:00 2008 (UTC)
2008-08-14 15:50:42.459 Grabbing listing data
--15:50:42--  [http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService](http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService)
           => `-'
Resolving webservices.schedulesdirect.tmsdatadirect.com... 206.18.98.175
Connecting to webservices.schedulesdirect.tmsdatadirect.com|206.18.98.175|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 401 Unauthorized
Authorization failed.
2008-08-14 15:50:42.786 Grab complete.  Actual data from  to  (UTC)
2008-08-14 15:50:42.791 Main temp tables populated.
2008-08-14 15:50:42.796 Did not find any new program data.
2008-08-14 15:50:42.798 
2008-08-14 15:50:42.799 Checking day @ offset 9, date: Sat Aug 23 2008
2008-08-14 15:50:42.801 Data refresh needed because no data exists for day @ offset 9 from 8PM - midnight.
2008-08-14 15:50:42.803 Refreshing data for Sat Aug 23 2008
2008-08-14 15:50:42.805 Retrieving datadirect data.
2008-08-14 15:50:42.806 Grabbing data for Thu Aug 14 2008 offset 9
2008-08-14 15:50:42.807 From Sat Aug 23 05:00:00 2008 to Sun Aug 24 05:00:00 2008 (UTC)
2008-08-14 15:50:42.808 Grabbing listing data
--15:50:42--  [http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService](http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService)
           => `-'
Resolving webservices.schedulesdirect.tmsdatadirect.com... 206.18.98.175
Connecting to webservices.schedulesdirect.tmsdatadirect.com|206.18.98.175|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 401 Unauthorized
Authorization failed.
2008-08-14 15:50:43.126 Grab complete.  Actual data from  to  (UTC)
2008-08-14 15:50:43.131 Main temp tables populated.
2008-08-14 15:50:43.135 Did not find any new program data.
2008-08-14 15:50:43.136 
2008-08-14 15:50:43.137 Checking day @ offset 10, date: Sun Aug 24 2008
2008-08-14 15:50:43.140 Data refresh needed because no data exists for day @ offset 10 from 8PM - midnight.
2008-08-14 15:50:43.141 Refreshing data for Sun Aug 24 2008
2008-08-14 15:50:43.142 Retrieving datadirect data.
2008-08-14 15:50:43.143 Grabbing data for Thu Aug 14 2008 offset 10
2008-08-14 15:50:43.144 From Sun Aug 24 05:00:00 2008 to Mon Aug 25 05:00:00 2008 (UTC)
2008-08-14 15:50:43.145 Grabbing listing data
--15:50:43--  [http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService](http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService)
           => `-'
Resolving webservices.schedulesdirect.tmsdatadirect.com... 206.18.98.175
Connecting to webservices.schedulesdirect.tmsdatadirect.com|206.18.98.175|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 401 Unauthorized
Authorization failed.
2008-08-14 15:50:44.072 Grab complete.  Actual data from  to  (UTC)
2008-08-14 15:50:44.079 Main temp tables populated.
2008-08-14 15:50:44.083 Did not find any new program data.
2008-08-14 15:50:44.084 
2008-08-14 15:50:44.085 Checking day @ offset 11, date: Mon Aug 25 2008
2008-08-14 15:50:44.088 Data refresh needed because no data exists for day @ offset 11 from 8PM - midnight.
2008-08-14 15:50:44.089 Refreshing data for Mon Aug 25 2008
2008-08-14 15:50:44.090 Retrieving datadirect data.
2008-08-14 15:50:44.091 Grabbing data for Thu Aug 14 2008 offset 11
2008-08-14 15:50:44.092 From Mon Aug 25 05:00:00 2008 to Tue Aug 26 05:00:00 2008 (UTC)
2008-08-14 15:50:44.094 Grabbing listing data
--15:50:44--  [http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService](http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService)
           => `-'
Resolving webservices.schedulesdirect.tmsdatadirect.com... 206.18.98.175
Connecting to webservices.schedulesdirect.tmsdatadirect.com|206.18.98.175|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 401 Unauthorized
Authorization failed.
2008-08-14 15:50:44.402 Grab complete.  Actual data from  to  (UTC)
2008-08-14 15:50:44.407 Main temp tables populated.
2008-08-14 15:50:44.411 Did not find any new program data.
2008-08-14 15:50:44.413 
2008-08-14 15:50:44.414 Checking day @ offset 12, date: Tue Aug 26 2008
2008-08-14 15:50:44.417 Data refresh needed because no data exists for day @ offset 12 from 8PM - midnight.
2008-08-14 15:50:44.418 Refreshing data for Tue Aug 26 2008
2008-08-14 15:50:44.419 Retrieving datadirect data.
2008-08-14 15:50:44.420 Grabbing data for Thu Aug 14 2008 offset 12
2008-08-14 15:50:44.421 From Tue Aug 26 05:00:00 2008 to Wed Aug 27 05:00:00 2008 (UTC)
2008-08-14 15:50:44.422 Grabbing listing data
--15:50:44--  [http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService](http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService)
           => `-'
Resolving webservices.schedulesdirect.tmsdatadirect.com... 206.18.98.175
Connecting to webservices.schedulesdirect.tmsdatadirect.com|206.18.98.175|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 401 Unauthorized
Authorization failed.
2008-08-14 15:50:44.825 Grab complete.  Actual data from  to  (UTC)
2008-08-14 15:50:44.831 Main temp tables populated.
2008-08-14 15:50:44.835 Did not find any new program data.
2008-08-14 15:50:44.836 
2008-08-14 15:50:44.837 Checking day @ offset 13, date: Wed Aug 27 2008
2008-08-14 15:50:44.839 Data refresh needed because no data exists for day @ offset 13 from 8PM - midnight.
2008-08-14 15:50:44.841 Refreshing data for Wed Aug 27 2008
2008-08-14 15:50:44.842 Retrieving datadirect data.
2008-08-14 15:50:44.843 Grabbing data for Thu Aug 14 2008 offset 13
2008-08-14 15:50:44.844 From Wed Aug 27 05:00:00 2008 to Thu Aug 28 05:00:00 2008 (UTC)
2008-08-14 15:50:44.845 Grabbing listing data
--15:50:44--  [http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService](http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService)
           => `-'
Resolving webservices.schedulesdirect.tmsdatadirect.com... 206.18.98.175
Connecting to webservices.schedulesdirect.tmsdatadirect.com|206.18.98.175|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 401 Unauthorized
Authorization failed.
2008-08-14 15:50:50.261 Grab complete.  Actual data from  to  (UTC)
2008-08-14 15:50:50.267 Main temp tables populated.
2008-08-14 15:50:50.270 Did not find any new program data.
2008-08-14 15:50:52.248 Updating source #2 (ScheduleDirect) with grabber schedulesdirect1
2008-08-14 15:50:52.253 Found 788 channels for source 2 which use grabber
2008-08-14 15:50:52.254 
2008-08-14 15:50:52.254 Checking day @ offset 0, date: Thu Aug 14 2008
2008-08-14 15:50:52.796 Data is already present for Thu Aug 14 2008, skipping
2008-08-14 15:50:52.801 
2008-08-14 15:50:52.801 Checking day @ offset 1, date: Fri Aug 15 2008
2008-08-14 15:50:52.802 Data Refresh always needed for tomorrow
2008-08-14 15:50:52.803 Refreshing data for Fri Aug 15 2008
2008-08-14 15:50:52.804 Retrieving datadirect data.
2008-08-14 15:50:52.805 Grabbing data for Thu Aug 14 2008 offset 1
2008-08-14 15:50:52.805 From Fri Aug 15 05:00:00 2008 to Sat Aug 16 05:00:00 2008 (UTC)
2008-08-14 15:50:52.806 Grabbing listing data
--15:50:52--  [http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService](http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService)
           => `-'
Resolving webservices.schedulesdirect.tmsdatadirect.com... 206.18.98.175
Connecting to webservices.schedulesdirect.tmsdatadirect.com|206.18.98.175|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]

    0K .......... .......... .......... .......... ..........   20.64 KB/s
   50K .......... .......... .......... .......... ..........   13.81 KB/s
  100K .......... .......... .......... .......... ..........   20.61 KB/s
  150K .......... .......... .......... .......... ..........  405.08 KB/s
  200K .......... .......... .......... .......... ..........  398.58 KB/s
  250K .......... .......... .......... .......... ..........  377.72 KB/s
  300K .......... .......... .......... .......... ..........  536.42 KB/s
  350K .......... .......... .......... .......... ..........  273.01 KB/s
  400K .......... .......... .......... .......... ..........  257.12 KB/s
  450K .......... .......... .......... .......... ..........  102.37 KB/s
  500K .......... .......... .......... .......... ..........   67.36 KB/s
  550K .......... .......... .......... .......... ..........   38.41 KB/s
  600K .......... .......... .......... .......... ..........  410.25 KB/s
  650K ..                                                      739.76 KB/s

15:51:05 (54.49 KB/s) - `-' saved [668247]

2008-08-14 15:51:06.043 DataDirect: Your subscription expires on 07/18/2009 06:43:46 PM
2008-08-14 15:51:07.075 sourceid 2 has lineup type: Satellite
2008-08-14 15:51:35.240 Grab complete.  Actual data from Fri Aug 15 05:00:00 2008 to Sat Aug 16 05:00:00 2008 (UTC)
2008-08-14 15:51:35.257 Main temp tables populated.
2008-08-14 15:51:35.258 Updating myth channels.
2008-08-14 15:51:35.564 DataDirect: Adding channel 668 'Fox Sports HD North - Minnesota' (FOXHDNO).
2008-08-14 15:51:35.574 DataDirect: Adding channel 683 'Fox Sports Rocky Mountain HD' (FOXHDRM).
2008-08-14 15:51:35.580 DataDirect: Adding channel 649 'Fox Sports South/SportSouth HD Channel' (FOXHDSS).
2008-08-14 15:51:35.586 DataDirect: Adding channel 311 'ABC Family Channel HD' (FAMHD).
2008-08-14 15:51:35.591 DataDirect: Adding channel 687 'Fox Sports Northwest HD (Alt.) - FSN4HD' (FSN4HD).
2008-08-14 15:51:35.596 DataDirect: Adding channel 286 'Planet Green HD' (GRNHD).
2008-08-14 15:51:35.602 DataDirect: Adding channel 542 'Showtime Extreme HD' (SHOWXHD).
2008-08-14 15:51:35.607 DataDirect: Adding channel 539 'Showtime Showcase HD' (SHOCSHD).
2008-08-14 15:51:35.610 Updating icons for sourceid: 2
2008-08-14 15:51:35.626 Channels updated.
2008-08-14 15:51:36.250 Clearing data for source.
2008-08-14 15:51:36.274 Clearing from Fri Aug 15 00:00:00 2008 to Sat Aug 16 00:00:00 2008 (localtime)
2008-08-14 15:51:36.277 New DB connection, total: 4
2008-08-14 15:51:36.278 Connected to database 'mythconverg' at host: localhost
2008-08-14 15:52:27.686 Data for source cleared.
2008-08-14 15:52:35.998 Updating programs.
2008-08-14 15:52:48.880 Program table update complete.
2008-08-14 15:52:48.903 
2008-08-14 15:52:49.155 Checking day @ offset 2, date: Sat Aug 16 2008
2008-08-14 15:52:49.687 Data is already present for Sat Aug 16 2008, skipping
2008-08-14 15:52:49.690 
2008-08-14 15:52:49.690 Checking day @ offset 3, date: Sun Aug 17 2008
2008-08-14 15:52:50.215 Data is already present for Sun Aug 17 2008, skipping
2008-08-14 15:52:50.217 
2008-08-14 15:52:50.218 Checking day @ offset 4, date: Mon Aug 18 2008
2008-08-14 15:52:50.734 Data is already present for Mon Aug 18 2008, skipping
2008-08-14 15:52:50.737 
2008-08-14 15:52:50.737 Checking day @ offset 5, date: Tue Aug 19 2008
2008-08-14 15:52:51.239 Data is already present for Tue Aug 19 2008, skipping
2008-08-14 15:52:51.239 
2008-08-14 15:52:51.240 Checking day @ offset 6, date: Wed Aug 20 2008
2008-08-14 15:52:51.750 Data is already present for Wed Aug 20 2008, skipping
2008-08-14 15:52:51.751 
2008-08-14 15:52:51.752 Checking day @ offset 7, date: Thu Aug 21 2008
2008-08-14 15:52:52.245 Data is already present for Thu Aug 21 2008, skipping
2008-08-14 15:52:52.246 
2008-08-14 15:52:52.247 Checking day @ offset 8, date: Fri Aug 22 2008
2008-08-14 15:52:52.741 Data is already present for Fri Aug 22 2008, skipping
2008-08-14 15:52:52.743 
2008-08-14 15:52:52.743 Checking day @ offset 9, date: Sat Aug 23 2008
2008-08-14 15:52:53.235 Data Refresh needed because offset day 9 has less than 3 programs per channel for the 8PM - midnight time window for channels that normally have data. We want at least 2352 programs, but only found 2350
2008-08-14 15:52:53.238 Refreshing data for Sat Aug 23 2008
2008-08-14 15:52:53.239 Retrieving datadirect data.
2008-08-14 15:52:53.240 Grabbing data for Thu Aug 14 2008 offset 9
2008-08-14 15:52:53.241 From Sat Aug 23 05:00:00 2008 to Sun Aug 24 05:00:00 2008 (UTC)
2008-08-14 15:52:53.242 Grabbing listing data
--15:52:53--  [http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService](http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService)
           => `-'
Resolving webservices.schedulesdirect.tmsdatadirect.com... 206.18.98.175
Connecting to webservices.schedulesdirect.tmsdatadirect.com|206.18.98.175|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]

    0K .......... .......... .......... .......... ..........   21.25 KB/s
   50K .......... .......... .......... .......... ..........   14.62 KB/s
  100K .......... .......... .......... .......... ..........   31.20 KB/s
  150K .......... .......... .......... .......... ..........  473.30 KB/s
  200K .......... .......... .......... .......... ..........   65.12 KB/s
  250K .......... .......... .......... .......... ..........  469.15 KB/s
  300K .......... .......... .......... .......... ..........  263.00 KB/s
  350K .......... .......... .......... .......... ..........  150.64 KB/s
  400K .......... .......... .......... .......... ..........  257.97 KB/s
  450K .......... .......... .......... .......... ..........   58.13 KB/s
  500K .......... .......... .......... .......... ..........  209.06 KB/s
  550K .......... .......... .......... .......... ..........   53.86 KB/s
  600K .......... .......... ....                              518.33 KB/s

15:53:04 (56.04 KB/s) - `-' saved [639683]

2008-08-14 15:53:05.244 DataDirect: Your subscription expires on 07/18/2009 06:43:46 PM
2008-08-14 15:53:32.725 Grab complete.  Actual data from Sat Aug 23 05:00:00 2008 to Sun Aug 24 05:00:00 2008 (UTC)
2008-08-14 15:53:32.732 Main temp tables populated.
2008-08-14 15:53:33.319 Clearing data for source.
2008-08-14 15:53:33.342 Clearing from Sat Aug 23 00:00:00 2008 to Sun Aug 24 00:00:00 2008 (localtime)
2008-08-14 15:54:12.395 Data for source cleared.
2008-08-14 15:54:17.687 Updating programs.
2008-08-14 15:54:26.707 Program table update complete.
2008-08-14 15:54:26.720 
2008-08-14 15:54:26.999 Checking day @ offset 10, date: Sun Aug 24 2008
2008-08-14 15:54:27.500 Data is already present for Sun Aug 24 2008, skipping
2008-08-14 15:54:27.502 
2008-08-14 15:54:27.503 Checking day @ offset 11, date: Mon Aug 25 2008
2008-08-14 15:54:27.967 Data is already present for Mon Aug 25 2008, skipping
2008-08-14 15:54:27.969 
2008-08-14 15:54:27.970 Checking day @ offset 12, date: Tue Aug 26 2008
2008-08-14 15:54:28.445 Data is already present for Tue Aug 26 2008, skipping
2008-08-14 15:54:28.448 
2008-08-14 15:54:28.448 Checking day @ offset 13, date: Wed Aug 27 2008
2008-08-14 15:54:28.691 Data refresh needed because only 0 out of 788 channels have at least one program listed for day @ offset 13 from 8PM - midnight.  Previous day had 784 channels with data in that time period.
2008-08-14 15:54:28.694 Refreshing data for Wed Aug 27 2008
2008-08-14 15:54:28.695 Retrieving datadirect data.
2008-08-14 15:54:28.696 Grabbing data for Thu Aug 14 2008 offset 13
2008-08-14 15:54:28.697 From Wed Aug 27 05:00:00 2008 to Thu Aug 28 05:00:00 2008 (UTC)
2008-08-14 15:54:28.697 Grabbing listing data
--15:54:28--  [http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService](http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService)
           => `-'
Resolving webservices.schedulesdirect.tmsdatadirect.com... 206.18.98.175
Connecting to webservices.schedulesdirect.tmsdatadirect.com|206.18.98.175|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]

    0K .......... .......... .......... .......... ..........   22.71 KB/s
   50K .......... .......... .......... .......... ..........   15.01 KB/s
  100K .......... .......... .......... .......... ..........   31.02 KB/s
  150K .......... .......... .......... .......... ..........  292.95 KB/s
  200K .......... .......... .......... .......... ..........  429.31 KB/s
  250K .......... .......... .......... .......... ..........  456.65 KB/s
  300K .......... .......... .......... .......... ..........  340.59 KB/s
  350K .......... .......... .......... .......... ..........  230.69 KB/s
  400K .......... .......... .......... .......... ..........  197.91 KB/s
  450K .......... .......... .......... .......... ..........   59.16 KB/s
  500K .......... .......... .......... .......... ..........  192.22 KB/s
  550K .......... .......... .......... .......... ..........   68.67 KB/s
  600K .......... ......                                       525.01 KB/s

15:54:39 (61.52 KB/s) - `-' saved [631453]

2008-08-14 15:54:39.574 DataDirect: Your subscription expires on 07/18/2009 06:43:46 PM
2008-08-14 15:55:07.490 Grab complete.  Actual data from Wed Aug 27 05:00:00 2008 to Thu Aug 28 05:00:00 2008 (UTC)
2008-08-14 15:55:07.507 Main temp tables populated.
2008-08-14 15:55:08.128 Clearing data for source.
2008-08-14 15:55:08.151 Clearing from Wed Aug 27 00:00:00 2008 to Thu Aug 28 00:00:00 2008 (localtime)
2008-08-14 15:55:09.578 Data for source cleared.
2008-08-14 15:55:09.581 Updating programs.
2008-08-14 15:55:16.916 Program table update complete.
2008-08-14 15:55:18.205 Failed to fetch some program info
2008-08-14 15:55:18.482 Adjusting program database end times.
2008-08-14 15:55:24.941     0 replacements made
2008-08-14 15:55:24.943 Marking generic episodes.
2008-08-14 15:55:26.407     Found 20648
2008-08-14 15:55:27.012 Marking repeats.
2008-08-14 15:55:28.954     Found 35176
2008-08-14 15:55:30.254 Unmarking new episode rebroadcast repeats.
2008-08-14 15:55:32.555     Found 0
2008-08-14 15:55:34.555 Marking episode first showings.
2008-08-14 15:55:38.318 mythfilldatabase still running, skipping checks.
2008-08-14 15:56:52.041     Found 44514
2008-08-14 15:57:00.170 Marking episode last showings.
2008-08-14 15:57:50.610 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-14 15:58:21.853     Found 44514
2008-08-14 15:58:31.546 Grabbing next suggested grabbing time
2008-08-14 15:58:32.621 DataDirect: BlockedTime is: 2008-08-14T15:58:32
2008-08-14 15:58:32.626 DataDirect: NextSuggestedTime is: 2008-08-15T17:36:41
2008-08-14 15:58:32.631 
===============================================================
| Attempting to contact the master backend for rescheduling.  |
| If the master is not running, rescheduling will happen when |
| the master backend is restarted.                            |
===============================================================
2008-08-14 15:58:32.639 Connecting to backend server: 192.168.1.107:6543 (try 1 of 5)
2008-08-14 15:58:32.641 Using protocol version 40
2008-08-14 15:58:32.643 MainServer::HandleAnnounce Monitor
2008-08-14 15:58:32.651 adding: bt224-desktop as a client (events: 0)
2008-08-14 15:58:32.653 MainServer::HandleAnnounce Monitor
2008-08-14 15:58:32.654 adding: bt224-desktop as a client (events: 1)
2008-08-14 15:58:32.658 Received a remote 'Clear Cache' request
Segmentation fault
2008-08-14 15:58:32.708 Reschedule requested for id -1.
2008-08-14 15:58:32.742 Scheduled 0 items in 0.0 = 0.01 match + 0.03 place
2008-08-14 15:58:58.647 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-08-14 15:58:58.654 UPnpMedia: BuildMediaMap Done. Found 2 objects
2008-08-14 16:12:57.744 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-14 16:27:57.797 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-14 16:28:58.657 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-08-14 16:28:58.667 UPnpMedia: BuildMediaMap Done. Found 2 objects
2008-08-14 16:42:57.835 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-14 16:57:57.872 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-14 16:59:04.670 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-08-14 16:59:04.676 UPnpMedia: BuildMediaMap Done. Found 2 objects
2008-08-14 17:12:57.911 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-14 17:27:57.948 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-14 17:29:11.680 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-08-14 17:29:11.692 UPnpMedia: BuildMediaMap Done. Found 2 objects
2008-08-14 17:42:57.986 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-14 17:57:58.033 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min

---

### Post by bt224 on 2008-08-18
It's actually recording, however playback is only the audio. Anyone have any ideas?

---

### Post by little_penguin on 2008-10-21
The black screen wall when trying to watch live tv can *sometimes* be due to the Storage Directories you set in the last page of mythtv-setup not having read and write permissions for the mythtv user. Expand the permissions accordingly and try running Watch TV again.

---

