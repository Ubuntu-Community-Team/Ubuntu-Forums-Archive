---
title: "Schedules Direct + MythTV (No Data)"
date: 2007-10-25
forum: Multimedia &amp; Video
---

### Post by sondo2121 on 2007-10-25
I am using 7.10 and when installing and configuring MythTV i come to a snag.  When I am configuring the schedules direct portion of the install, after pressing the retrieve lineups button, it just goews to 50% then 100% and doesn't pull up any info.  In the background terminal box it says there is an error connecting 

```

2007-10-25 22:43:07.345 Failed to run tv_find_grabbers
2007-10-25 22:43:10.807 Fetching lineups from Schedules Direct...
2007-10-25 22:43:10.823 Grabbing channel data
--22:43:10--  http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService
           => `-'
Resolving webservices.schedulesdirect.tmsdatadirect.com... 206.18.98.175
Connecting to webservices.schedulesdirect.tmsdatadirect.com|206.18.98.175|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 500 Internal Server Error
22:43:11 ERROR 500: Internal Server Error.

2007-10-25 22:43:11.427 New DB DataDirect connection
2007-10-25 22:43:11.427 Connected to database 'mythconverg' at host: localhost
2007-10-25 22:43:11.462 DataDirect: Deleting temporary files

```

---

### Post by Lido on 2008-01-07
I'm having the exact same problem. I click the "Retrieve Lineups" button and nothing happens, then when I try to run mythfilldatabase I get the 401 unauthorized and 500 internal server errors. I double and triple checked my username and password so I don't think that's the problem. I think the issue is on schedulesdirect's end. I emailed them and they told me to retry today and I was able to connect (though for whatever reason no listing info is showing up in mythtv).

---

### Post by mikeylikesit on 2008-01-20
im having the same problem were you guys able to get it to work correctly? 

thanks

---

### Post by dwf_starband on 2008-01-24
im having the same problem with a previously working account, it just stoped getting the lineups one day and I havent been able to get any since.

dennis

---

