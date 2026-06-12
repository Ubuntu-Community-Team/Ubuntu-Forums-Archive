---
title: "How do I pause the fast terminal screen?"
date: 2009-10-07
forum: Mythbuntu
---

### Post by cat2005 on 2009-10-07
I entered my sudo password to run "mythfilldatabase" or whatever it was called.  A terminal appeared with verbose details, but it closed too quickly for me to even read the summary.

How do I pause the fast terminal screen, or find its log?

Its information could prove helpful; I think my backend is farked.

Thanks!

---

### Post by Lepy on 2009-10-07
Try entering mythfilldatabase into a terminal you open from your windows manager. 

Once mythfilldatabase has run its course, the terminal will stay open allowing you to analyse the output.

---

### Post by ian dobson on 2009-10-07
Hi,

You could use a pipe to pass the screen information from one program to the next. And use "more" to pause the output per screen full.

mythfilldatabase | more

the | is the pipe.


Or if your quick enough you can use control S/control Q to pause output.

Regards
Ian Dobson

---

### Post by cat2005 on 2009-10-08
Lepy,
 
a) How would I do so?  Would I enter terminal type:  run mythfilldatabase
b) Must I sudo?
 
 
ian dobson,
 
a) How would I do so?  Would I enter terminal and type:  mythfilldatabase | more
b) Must I sudo?
c) As an alternative, if I understand correctly, I could use ctrl + S (or ctrl + Q) to pause it immediately after if finishes - and that should give me the time I need
 
 
Thank you both!
[]("http://ubuntuforums.org/member.php?u=303716")

---

### Post by ian dobson on 2009-10-08
Hi,

for mythfilldatabase you don't need to use sudo as you what mythfilldatabase to run as a normal user.

When the text is scrolling just press control S and it will stop scrolling until you press control Q.

Regards
Ian Dobson

---

### Post by Lepy on 2009-10-08
> **cat2005 said:**
> Lepy,
 
a) How would I do so?  Would I enter terminal type:  run mythfilldatabase
b) Must I sudo?
[]("http://ubuntuforums.org/member.php?u=303716")

Just open a terminal how you normally would (through the applications menu or a keyboard short cut you may have set yourself) and type "mythfilldatabase" to get generic output. 
If you want more specialized output, type "mythfilldatabase -v help" and custom tailor to what output you may need eg. "mythfilldatabase -v extra".

---

### Post by cat2005 on 2009-10-08
Thank you both!

---

### Post by cat2005 on 2009-10-08
**I ran it in regular terminal.  Everytime I got this: ** 

mythregular@mythcpu:~$ mythfilldatabase
2009-10-08 18:14:10.324 Using runtime prefix = /usr
2009-10-08 18:14:10.325 Empty LocalHostName.
2009-10-08 18:14:10.325 Using localhost value of mythcpu
2009-10-08 18:14:10.337 New DB connection, total: 1
2009-10-08 18:14:10.342 Connected to database 'mythconverg' at host: localhost
2009-10-08 18:14:10.343 Closing DB connection named 'DBManager0'
2009-10-08 18:14:10.344 Connected to database 'mythconverg' at host: localhost
2009-10-08 18:14:10.348 New DB connection, total: 2
2009-10-08 18:14:10.358 Connected to database 'mythconverg' at host: localhost
2009-10-08 18:14:10.359 Updating source #1 (PVR-150) with grabber schedulesdirect1
2009-10-08 18:14:10.359 No channels are configured to use grabber.
2009-10-08 18:14:10.359 
2009-10-08 18:14:10.360 Checking day @ offset 0, date: Thu Oct 8 2009
2009-10-08 18:14:10.361 Data refresh needed because no data exists for day @ offset 0 from 8PM - midnight.
2009-10-08 18:14:10.362 Refreshing data for Thu Oct 8 2009
2009-10-08 18:14:10.362 New DB DataDirect connection
2009-10-08 18:14:10.363 Connected to database 'mythconverg' at host: localhost
2009-10-08 18:14:10.364 Retrieving datadirect data.
2009-10-08 18:14:10.364 Grabbing data for Thu Oct 8 2009 offset 0
2009-10-08 18:14:10.365 From Thu Oct 8 05:00:00 2009 to Fri Oct 9 05:00:00 2009 (UTC)
2009-10-08 18:14:10.365 Grabbing listing data
--2009-10-08 18:14:10--  [http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService](http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService)
Resolving webservices.schedulesdirect.tmsdatadirect.com... 144.142.232.53
Connecting to webservices.schedulesdirect.tmsdatadirect.com|144.142.232.53|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 500 Internal Server Error
2009-10-08 18:14:10 ERROR 500: Internal Server Error.

2009-10-08 18:14:10.898 Grab complete.  Actual data from  to  (UTC)
2009-10-08 18:14:10.898 Main temp tables populated.
2009-10-08 18:14:10.898 Updating myth channels.
2009-10-08 18:14:10.900 New DB connection, total: 3
2009-10-08 18:14:10.901 Connected to database 'mythconverg' at host: localhost
2009-10-08 18:14:10.905 Updating icons for sourceid: 1
2009-10-08 18:14:10.906 Channels updated.
2009-10-08 18:14:10.908 Did not find any new program data.
2009-10-08 18:14:10.908 
2009-10-08 18:14:10.908 Checking day @ offset 1, date: Fri Oct 9 2009
2009-10-08 18:14:10.908 Data Refresh always needed for tomorrow
2009-10-08 18:14:10.908 Refreshing data for Fri Oct 9 2009
2009-10-08 18:14:10.909 Retrieving datadirect data.
2009-10-08 18:14:10.909 Grabbing data for Thu Oct 8 2009 offset 1
2009-10-08 18:14:10.909 From Fri Oct 9 05:00:00 2009 to Sat Oct 10 05:00:00 2009 (UTC)
2009-10-08 18:14:10.909 Grabbing listing data
--2009-10-08 18:14:10--  [http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService](http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService)
Resolving webservices.schedulesdirect.tmsdatadirect.com... 144.142.232.53
Connecting to webservices.schedulesdirect.tmsdatadirect.com|144.142.232.53|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 500 Internal Server Error
2009-10-08 18:14:11 ERROR 500: Internal Server Error.

2009-10-08 18:14:11.367 Grab complete.  Actual data from  to  (UTC)
2009-10-08 18:14:11.368 Main temp tables populated.
2009-10-08 18:14:11.370 Did not find any new program data.
2009-10-08 18:14:11.370 
2009-10-08 18:14:11.370 Checking day @ offset 2, date: Sat Oct 10 2009
2009-10-08 18:14:11.372 Data refresh needed because no data exists for day @ offset 2 from 8PM - midnight.
2009-10-08 18:14:11.372 Refreshing data for Sat Oct 10 2009
2009-10-08 18:14:11.373 Retrieving datadirect data.
2009-10-08 18:14:11.373 Grabbing data for Thu Oct 8 2009 offset 2
2009-10-08 18:14:11.373 From Sat Oct 10 05:00:00 2009 to Sun Oct 11 05:00:00 2009 (UTC)
2009-10-08 18:14:11.373 Grabbing listing data
--2009-10-08 18:14:11--  [http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService](http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService)
Resolving webservices.schedulesdirect.tmsdatadirect.com... 144.142.232.53
Connecting to webservices.schedulesdirect.tmsdatadirect.com|144.142.232.53|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 500 Internal Server Error
2009-10-08 18:14:11 ERROR 500: Internal Server Error.

2009-10-08 18:14:11.864 Grab complete.  Actual data from  to  (UTC)
2009-10-08 18:14:11.865 Main temp tables populated.
2009-10-08 18:14:11.869 Did not find any new program data.
2009-10-08 18:14:11.869 
2009-10-08 18:14:11.869 Checking day @ offset 3, date: Sun Oct 11 2009
2009-10-08 18:14:11.871 Data refresh needed because no data exists for day @ offset 3 from 8PM - midnight.
2009-10-08 18:14:11.871 Refreshing data for Sun Oct 11 2009
2009-10-08 18:14:11.872 Retrieving datadirect data.
2009-10-08 18:14:11.872 Grabbing data for Thu Oct 8 2009 offset 3
2009-10-08 18:14:11.872 From Sun Oct 11 05:00:00 2009 to Mon Oct 12 05:00:00 2009 (UTC)
2009-10-08 18:14:11.872 Grabbing listing data
--2009-10-08 18:14:11--  [http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService](http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService)
Resolving webservices.schedulesdirect.tmsdatadirect.com... 144.142.232.53
Connecting to webservices.schedulesdirect.tmsdatadirect.com|144.142.232.53|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 500 Internal Server Error
2009-10-08 18:14:12 ERROR 500: Internal Server Error.

2009-10-08 18:14:12.363 Grab complete.  Actual data from  to  (UTC)
2009-10-08 18:14:12.364 Main temp tables populated.
2009-10-08 18:14:12.368 Did not find any new program data.
2009-10-08 18:14:12.368 
2009-10-08 18:14:12.368 Checking day @ offset 4, date: Mon Oct 12 2009
2009-10-08 18:14:12.370 Data refresh needed because no data exists for day @ offset 4 from 8PM - midnight.
2009-10-08 18:14:12.370 Refreshing data for Mon Oct 12 2009
2009-10-08 18:14:12.370 Retrieving datadirect data.
2009-10-08 18:14:12.370 Grabbing data for Thu Oct 8 2009 offset 4
2009-10-08 18:14:12.371 From Mon Oct 12 05:00:00 2009 to Tue Oct 13 05:00:00 2009 (UTC)
2009-10-08 18:14:12.371 Grabbing listing data
--2009-10-08 18:14:12--  [http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService](http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService)
Resolving webservices.schedulesdirect.tmsdatadirect.com... 144.142.232.53
Connecting to webservices.schedulesdirect.tmsdatadirect.com|144.142.232.53|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 500 Internal Server Error
2009-10-08 18:14:12 ERROR 500: Internal Server Error.

2009-10-08 18:14:12.840 Grab complete.  Actual data from  to  (UTC)
2009-10-08 18:14:12.841 Main temp tables populated.
2009-10-08 18:14:12.845 Did not find any new program data.
2009-10-08 18:14:12.845 
2009-10-08 18:14:12.845 Checking day @ offset 5, date: Tue Oct 13 2009
2009-10-08 18:14:12.847 Data refresh needed because no data exists for day @ offset 5 from 8PM - midnight.
2009-10-08 18:14:12.847 Refreshing data for Tue Oct 13 2009
2009-10-08 18:14:12.848 Retrieving datadirect data.
2009-10-08 18:14:12.848 Grabbing data for Thu Oct 8 2009 offset 5
2009-10-08 18:14:12.848 From Tue Oct 13 05:00:00 2009 to Wed Oct 14 05:00:00 2009 (UTC)
2009-10-08 18:14:12.848 Grabbing listing data
--2009-10-08 18:14:12--  [http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService](http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService)
Resolving webservices.schedulesdirect.tmsdatadirect.com... 144.142.232.53
Connecting to webservices.schedulesdirect.tmsdatadirect.com|144.142.232.53|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 500 Internal Server Error
2009-10-08 18:14:13 ERROR 500: Internal Server Error.

2009-10-08 18:14:13.322 Grab complete.  Actual data from  to  (UTC)
2009-10-08 18:14:13.322 Main temp tables populated.
2009-10-08 18:14:13.326 Did not find any new program data.
2009-10-08 18:14:13.326 
2009-10-08 18:14:13.326 Checking day @ offset 6, date: Wed Oct 14 2009
2009-10-08 18:14:13.328 Data refresh needed because no data exists for day @ offset 6 from 8PM - midnight.
2009-10-08 18:14:13.328 Refreshing data for Wed Oct 14 2009
2009-10-08 18:14:13.329 Retrieving datadirect data.
2009-10-08 18:14:13.329 Grabbing data for Thu Oct 8 2009 offset 6
2009-10-08 18:14:13.329 From Wed Oct 14 05:00:00 2009 to Thu Oct 15 05:00:00 2009 (UTC)
2009-10-08 18:14:13.329 Grabbing listing data
--2009-10-08 18:14:13--  [http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService](http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService)
Resolving webservices.schedulesdirect.tmsdatadirect.com... 144.142.232.53
Connecting to webservices.schedulesdirect.tmsdatadirect.com|144.142.232.53|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 500 Internal Server Error
2009-10-08 18:14:13 ERROR 500: Internal Server Error.

2009-10-08 18:14:13.801 Grab complete.  Actual data from  to  (UTC)
2009-10-08 18:14:13.801 Main temp tables populated.
2009-10-08 18:14:13.806 Did not find any new program data.
2009-10-08 18:14:13.806 
2009-10-08 18:14:13.806 Checking day @ offset 7, date: Thu Oct 15 2009
2009-10-08 18:14:13.808 Data refresh needed because no data exists for day @ offset 7 from 8PM - midnight.
2009-10-08 18:14:13.808 Refreshing data for Thu Oct 15 2009
2009-10-08 18:14:13.809 Retrieving datadirect data.
2009-10-08 18:14:13.809 Grabbing data for Thu Oct 8 2009 offset 7
2009-10-08 18:14:13.809 From Thu Oct 15 05:00:00 2009 to Fri Oct 16 05:00:00 2009 (UTC)
2009-10-08 18:14:13.809 Grabbing listing data
--2009-10-08 18:14:13--  [http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService](http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService)
Resolving webservices.schedulesdirect.tmsdatadirect.com... 144.142.232.53
Connecting to webservices.schedulesdirect.tmsdatadirect.com|144.142.232.53|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 500 Internal Server Error
2009-10-08 18:14:14 ERROR 500: Internal Server Error.

2009-10-08 18:14:14.294 Grab complete.  Actual data from  to  (UTC)
2009-10-08 18:14:14.295 Main temp tables populated.
2009-10-08 18:14:14.300 Did not find any new program data.
2009-10-08 18:14:14.301 
2009-10-08 18:14:14.301 Checking day @ offset 8, date: Fri Oct 16 2009
2009-10-08 18:14:14.302 Data refresh needed because no data exists for day @ offset 8 from 8PM - midnight.
2009-10-08 18:14:14.303 Refreshing data for Fri Oct 16 2009
2009-10-08 18:14:14.303 Retrieving datadirect data.
2009-10-08 18:14:14.303 Grabbing data for Thu Oct 8 2009 offset 8
2009-10-08 18:14:14.303 From Fri Oct 16 05:00:00 2009 to Sat Oct 17 05:00:00 2009 (UTC)
2009-10-08 18:14:14.303 Grabbing listing data
--2009-10-08 18:14:14--  [http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService](http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService)
Resolving webservices.schedulesdirect.tmsdatadirect.com... 144.142.232.53
Connecting to webservices.schedulesdirect.tmsdatadirect.com|144.142.232.53|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 500 Internal Server Error
2009-10-08 18:14:14 ERROR 500: Internal Server Error.

2009-10-08 18:14:14.798 Grab complete.  Actual data from  to  (UTC)
2009-10-08 18:14:14.798 Main temp tables populated.
2009-10-08 18:14:14.803 Did not find any new program data.
2009-10-08 18:14:14.804 
2009-10-08 18:14:14.804 Checking day @ offset 9, date: Sat Oct 17 2009
2009-10-08 18:14:14.805 Data refresh needed because no data exists for day @ offset 9 from 8PM - midnight.
2009-10-08 18:14:14.805 Refreshing data for Sat Oct 17 2009
2009-10-08 18:14:14.806 Retrieving datadirect data.
2009-10-08 18:14:14.806 Grabbing data for Thu Oct 8 2009 offset 9
2009-10-08 18:14:14.806 From Sat Oct 17 05:00:00 2009 to Sun Oct 18 05:00:00 2009 (UTC)
2009-10-08 18:14:14.806 Grabbing listing data
--2009-10-08 18:14:14--  [http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService](http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService)
Resolving webservices.schedulesdirect.tmsdatadirect.com... 144.142.232.53
Connecting to webservices.schedulesdirect.tmsdatadirect.com|144.142.232.53|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 500 Internal Server Error
2009-10-08 18:14:15 ERROR 500: Internal Server Error.

2009-10-08 18:14:15.275 Grab complete.  Actual data from  to  (UTC)
2009-10-08 18:14:15.275 Main temp tables populated.
2009-10-08 18:14:15.279 Did not find any new program data.
2009-10-08 18:14:15.279 
2009-10-08 18:14:15.279 Checking day @ offset 10, date: Sun Oct 18 2009
2009-10-08 18:14:15.281 Data refresh needed because no data exists for day @ offset 10 from 8PM - midnight.
2009-10-08 18:14:15.281 Refreshing data for Sun Oct 18 2009
2009-10-08 18:14:15.282 Retrieving datadirect data.
2009-10-08 18:14:15.282 Grabbing data for Thu Oct 8 2009 offset 10
2009-10-08 18:14:15.282 From Sun Oct 18 05:00:00 2009 to Mon Oct 19 05:00:00 2009 (UTC)
2009-10-08 18:14:15.282 Grabbing listing data
--2009-10-08 18:14:15--  [http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService](http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService)
Resolving webservices.schedulesdirect.tmsdatadirect.com... 144.142.232.53
Connecting to webservices.schedulesdirect.tmsdatadirect.com|144.142.232.53|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 500 Internal Server Error
2009-10-08 18:14:15 ERROR 500: Internal Server Error.

2009-10-08 18:14:15.790 Grab complete.  Actual data from  to  (UTC)
2009-10-08 18:14:15.791 Main temp tables populated.
2009-10-08 18:14:15.796 Did not find any new program data.
2009-10-08 18:14:15.796 
2009-10-08 18:14:15.796 Checking day @ offset 11, date: Mon Oct 19 2009
2009-10-08 18:14:15.798 Data refresh needed because no data exists for day @ offset 11 from 8PM - midnight.
2009-10-08 18:14:15.798 Refreshing data for Mon Oct 19 2009
2009-10-08 18:14:15.799 Retrieving datadirect data.
2009-10-08 18:14:15.799 Grabbing data for Thu Oct 8 2009 offset 11
2009-10-08 18:14:15.799 From Mon Oct 19 05:00:00 2009 to Tue Oct 20 05:00:00 2009 (UTC)
2009-10-08 18:14:15.799 Grabbing listing data
--2009-10-08 18:14:15--  [http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService](http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService)
Resolving webservices.schedulesdirect.tmsdatadirect.com... 144.142.232.53
Connecting to webservices.schedulesdirect.tmsdatadirect.com|144.142.232.53|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 500 Internal Server Error
2009-10-08 18:14:16 ERROR 500: Internal Server Error.

2009-10-08 18:14:16.271 Grab complete.  Actual data from  to  (UTC)
2009-10-08 18:14:16.272 Main temp tables populated.
2009-10-08 18:14:16.276 Did not find any new program data.
2009-10-08 18:14:16.277 
2009-10-08 18:14:16.277 Checking day @ offset 12, date: Tue Oct 20 2009
2009-10-08 18:14:16.279 Data refresh needed because no data exists for day @ offset 12 from 8PM - midnight.
2009-10-08 18:14:16.279 Refreshing data for Tue Oct 20 2009
2009-10-08 18:14:16.280 Retrieving datadirect data.
2009-10-08 18:14:16.280 Grabbing data for Thu Oct 8 2009 offset 12
2009-10-08 18:14:16.280 From Tue Oct 20 05:00:00 2009 to Wed Oct 21 05:00:00 2009 (UTC)
2009-10-08 18:14:16.280 Grabbing listing data
--2009-10-08 18:14:16--  [http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService](http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService)
Resolving webservices.schedulesdirect.tmsdatadirect.com... 144.142.232.53
Connecting to webservices.schedulesdirect.tmsdatadirect.com|144.142.232.53|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 500 Internal Server Error
2009-10-08 18:14:16 ERROR 500: Internal Server Error.

2009-10-08 18:14:16.753 Grab complete.  Actual data from  to  (UTC)
2009-10-08 18:14:16.753 Main temp tables populated.
2009-10-08 18:14:16.759 Did not find any new program data.
2009-10-08 18:14:16.759 
2009-10-08 18:14:16.759 Checking day @ offset 13, date: Wed Oct 21 2009
2009-10-08 18:14:16.761 Data refresh needed because no data exists for day @ offset 13 from 8PM - midnight.
2009-10-08 18:14:16.761 Refreshing data for Wed Oct 21 2009
2009-10-08 18:14:16.762 Retrieving datadirect data.
2009-10-08 18:14:16.762 Grabbing data for Thu Oct 8 2009 offset 13
2009-10-08 18:14:16.762 From Wed Oct 21 05:00:00 2009 to Thu Oct 22 05:00:00 2009 (UTC)
2009-10-08 18:14:16.762 Grabbing listing data
--2009-10-08 18:14:16--  [http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService](http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService)
Resolving webservices.schedulesdirect.tmsdatadirect.com... 144.142.232.53
Connecting to webservices.schedulesdirect.tmsdatadirect.com|144.142.232.53|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 500 Internal Server Error
2009-10-08 18:14:17 ERROR 500: Internal Server Error.

2009-10-08 18:14:17.242 Grab complete.  Actual data from  to  (UTC)
2009-10-08 18:14:17.243 Main temp tables populated.
2009-10-08 18:14:17.247 Did not find any new program data.
2009-10-08 18:14:17.247 Failed to fetch some program info
2009-10-08 18:14:17.247 Adjusting program database end times.
2009-10-08 18:14:17.248     0 replacements made
2009-10-08 18:14:17.248 Marking generic episodes.
2009-10-08 18:14:17.248     Found 0
2009-10-08 18:14:17.248 Marking repeats.
2009-10-08 18:14:17.250     Found 0
2009-10-08 18:14:17.250 Unmarking new episode rebroadcast repeats.
2009-10-08 18:14:17.250     Found 0
2009-10-08 18:14:17.251 Marking episode first showings.
2009-10-08 18:14:17.251     Found 0
2009-10-08 18:14:17.251 Marking episode last showings.
2009-10-08 18:14:17.251     Found 0
2009-10-08 18:14:17.253 Grabbing next suggested grabbing time
2009-10-08 18:14:17.723 DataDirect: BlockedTime is: 2009-10-08T18:14:16
2009-10-08 18:14:17.723 DataDirect: NextSuggestedTime is: 2009-10-09T12:41:52
2009-10-08 18:14:17.727 
===============================================================
| Attempting to contact the master backend for rescheduling.  |
| If the master is not running, rescheduling will happen when |
| the master backend is restarted.                            |
===============================================================
2009-10-08 18:14:17.733 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-10-08 18:14:17.736 Connection timed out.          
            You probably should modify the Master Server 
            settings in the setup program and set the    
            proper IP address.
2009-10-08 18:14:17.736 Error rescheduling id -1 in ScheduledRecording::signalChange
2009-10-08 18:14:17.737 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-10-08 18:14:17.737 Connection timed out.          
            You probably should modify the Master Server 
            settings in the setup program and set the    
            proper IP address.
2009-10-08 18:14:17.738 mythfilldatabase run complete.
2009-10-08 18:14:17.738 DataDirect: Deleting temporary files
mythregular@mythcpu:~$ 


**What does all that mean?**

---

### Post by Lepy on 2009-10-08
```
2009-10-08 18:14:16.762 Grabbing listing data
--2009-10-08 18:14:16-- http://webservices.schedulesdirect.t...gs/xtvdService
Resolving webservices.schedulesdirect.tmsdatadirect.com... 144.142.232.53
Connecting to webservices.schedulesdirect.tmsdatadirect.com|144. 142.232.53|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 500 Internal Server Error
2009-10-08 18:14:17 ERROR 500: Internal Server Error.
```

This part of the log repeats multiple times. It means that mythfilldatabase is trying to get the listing data from the Schedules Direct subscription service, but is getting rejected because an invalid user name and password have been provided or none at all.

Do you have an account with SD? If so, you should put your information in the backend settings. If you don't have an SD account, sign up for one or use a free listing grabber such as mc2xml.

---

### Post by cat2005 on 2009-10-09
> **Lepy said:**
> ```
2009-10-08 18:14:16.762 Grabbing listing data
--2009-10-08 18:14:16-- http://webservices.schedulesdirect.t...gs/xtvdService
Resolving webservices.schedulesdirect.tmsdatadirect.com... 144.142.232.53
Connecting to webservices.schedulesdirect.tmsdatadirect.com|144. 142.232.53|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 500 Internal Server Error
2009-10-08 18:14:17 ERROR 500: Internal Server Error.
```This part of the log repeats multiple times. It means that mythfilldatabase is trying to get the listing data from the Schedules Direct subscription service, but is getting rejected because an invalid user name and password have been provided or none at all.

Do you have an account with SD? If so, you should put your information in the backend settings. If you don't have an SD account, sign up for one or use a free listing grabber such as mc2xml.


Yes, I created an SD account the day before.  Perhaps I just mistyped my ID and Password.  I will try to re-input them and post results.

Thanks.

---

### Post by cat2005 on 2009-10-10
Lepy,

This time, I know I correctly inputed my SD ID and Password, but received the same output after running mythfilldatabase.

Any ideas?

---

### Post by alexandermdevereux on 2009-10-10
try using scroll lock

---

