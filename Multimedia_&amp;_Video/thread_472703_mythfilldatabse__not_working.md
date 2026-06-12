---
title: "mythfilldatabse  not working"
date: 2007-06-13
forum: Multimedia &amp; Video
---

### Post by klandwehr on 2007-06-13
I have just installed Mythtv on Ubuntu 7.04, and the TV portion  is working fine.  However I can't get a program guide.  I signed up for Zap2it,  I had it Mythtv set to auto download the data base, that didn't work. Then I tried to do it manually also without success.  When I go to setup  in mythtv frontend  I keep getting the message no program guide, did you run mythfilldatabase..  This is what I get back   
10:51:36 (48.35 KB/s) - `-' saved [178261]

2007-06-13 10:51:37.025 DataDirect: Your subscription expires on 09/10/2007 09:28:28 PM
2007-06-13 10:52:31.011 Grab complete.  Actual data from Mon Jun 25 04:00:00 2007 to Tue Jun 26 04:00:00 2007 (UTC)
2007-06-13 10:52:31.014 Main temp tables populated.
2007-06-13 10:52:31.377 Did not find any new program data.
2007-06-13 10:52:31.377 
2007-06-13 10:52:31.378 Checking day @ offset 13, date: Tue Jun 26 2007
2007-06-13 10:52:31.390 Data refresh needed because no data exists for day @ offset 13 from 6PM - midnight.
2007-06-13 10:52:31.390 Refreshing data for Tue Jun 26 2007
2007-06-13 10:52:31.500 Retrieving datadirect data.
2007-06-13 10:52:31.500 Grabbing data for Wed Jun 13 2007 offset 13
2007-06-13 10:52:31.501 From Tue Jun 26 04:00:00 2007 to Wed Jun 27 04:00:00 2007 (UTC)
2007-06-13 10:52:31.502 Grabbing listing data
--10:52:31--  [http://datadirect.webservices.zap2it.com/tvlistings/xtvdService](http://datadirect.webservices.zap2it.com/tvlistings/xtvdService)
           => `-'
Resolving datadirect.webservices.zap2it.com... 206.18.98.160
Connecting to datadirect.webservices.zap2it.com|206.18.98.160|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to datadirect.webservices.zap2it.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]

    [               <=>                                                                ] 283,487       54.43K/s

---

### Post by newlinux on 2007-06-13
looks like it already thinks you have the most up to date info (which it says there is no new data to grab and it is looking for data after june 26th...). Do you have the proper channels setup in your zap2it account?  Are you running this on your master backend?

Maybe you should try refreshing all of your listings...

```

mythfilldatabase --refresh-all

```

---

