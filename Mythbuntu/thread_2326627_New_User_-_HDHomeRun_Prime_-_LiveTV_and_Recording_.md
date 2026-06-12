---
title: "New User - HDHomeRun Prime - LiveTV and Recording doesn't work"
date: 2016-06-02
forum: Mythbuntu
---

### Post by Steven_Wittwer on 2016-06-02
I'm a newbie, but been using software DVR's for about 3 years.  I'm also very network fluent.  With that said, I can't get my HDHR Prime to show live TV or record anything...sure it is simple, but I can't figure it out.  below is what I have done so far:

1. Installed Myth TV
2. Configured the Primes, EPG, etc based on the official WIKI (although it is based on an older version of MythTV, so there are options that were not listed, so I left them as default)
3. Configured a Recording Directory (~/RecordedTV), and added it to the mythTV group (not sure if that is needed or not)
4. Configured the start channel to a legit channel

I can get live TV through the HDHR config app (and also my current software JRiver Media Center - all the channels I am trying are Copy Freely).

I get the guide data, and it is correct.

When I select Live TV, it flashes 'Please wait' for about 1/2 second, then nothing.

If I try to record something, it just says recordings fail.

What am I missing, or what more info can I provide?  

Thanks for any help!!!

P.S.  I have 2 Primes, but I have only configured 1 (all 3 tuners).  I can't imagine this would matter, but figured I should say it just in case.

---

### Post by larsolav on 2016-06-03
Hi,
best thing to do first is to look in the logs:
The log files for MythTV can be found in /var/log/mythtv/. 
The problem is probably backend specific, you can find the log files for mythbackend in /var/log/mythtv/mythbackend.log.
The frontend logs to /var/log/mythtv/mythfrontend.log.

---

### Post by Steven_Wittwer on 2016-06-03
I figured it out...it was permissions.  The recording folder needs to be owned by mythtv as well as in the mythtv group.

---

