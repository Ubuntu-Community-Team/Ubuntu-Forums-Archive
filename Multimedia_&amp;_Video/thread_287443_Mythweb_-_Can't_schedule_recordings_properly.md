---
title: "Mythweb - Can't schedule recordings properly"
date: 2006-10-28
forum: Multimedia &amp; Video
---

### Post by clayton on 2006-10-28
I have an Edgy install up and running, and mythtv is working properly (snd_bt87x to boot) with a basic Hauppauge card. Recordings work great when scheduled within mythtv, but when trying to record from mythweb by selecting the tv show listing, it shows up under Recording Schedules (manual) and not under Upcoming Recordings or Backend Status->Scheduled Recordings. So, in short, it's not recording from the web interface. Is anyone else experiencing the same problem?

I can delete channels and change values in the database from Mythweb, by the way, so it doesn't appear to be an access problem. A configuration option maybe?

clayton

---

### Post by acoulson on 2007-02-01
I have the same problem.  Did you ever resolve it?

Andrew

---

### Post by NT4usB on 2007-02-01
A quick google on: *Mythweb - Can't schedule recordings* finds this:

 I uninstalled mythtv and reinstalled it from scratch; now it works. <shrug>.

My suspicion in hindsight, after doing yet more reading, is that it may
have been caused by having two different IP addresses (127.0.0.1 and the
actual IP address) in the two different boxes in that part of
mythtv-setup where you enter two IP addresses. So that's a hint for
anyone who finds this thread in the list archives in the future. 
[http://www.gossamer-threads.com/lists/mythtv/dev/245732](http://www.gossamer-threads.com/lists/mythtv/dev/245732)

---

