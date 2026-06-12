---
title: "EPG scan question"
date: 2008-09-01
forum: Mythbuntu
---

### Post by Markus72 on 2008-09-01
Hi guys,

what is the algorithm for EPG scanning in MythTv?
I remember that with 0.19 or so MythTv scanned the EPG regularly and during the scan it didn't shutdown.
MythWelcome always told me - like when recording - something about EPG scanning.

After I set up Mythbuntu 8.04 there is no such behaviour.
Yes, it scans the EPG but

a) not more than 2 or 3 days in the future (there is more, I'm sure)
b) sometimes stations are not updated for days and so running out of any information
c) sometimes the stations then are updated later (after having 2 days without any EPG)

I have the strong feeling that MythTv doesn't scan the EPG systematically any more...

Why does it behave like it? What can I do against it?

I would expect that it runs the EPG update at least once every day for all stations. 

Any ideas? Help's appreciated

Thanks in advance

Markus

---

### Post by ian dobson on 2008-09-01
Hi,

On my box the EPG comes from the EIT over DVB-c. If you set MythTV to keep the tuners open all the time then MythTV just loops through each Multiplex reading/adding the EIT data.

How long MythTV keeps a multiplex open before going to the next one is configured in the settings database parameters EITCrawIdleStart, EITTransportTimeout. The amount of data you have is dependant on your TV provider. 
Here's a graphic of my EPG data in days:- [http://mail.planet-ian.com/munin/planet-ian.com/alpha2.planet-ian.com-mythtv_programs-day.png](http://mail.planet-ian.com/munin/planet-ian.com/alpha2.planet-ian.com-mythtv_programs-day.png)

If you don't have DVB then the EPG has to come from a different source (internet/mythfilldatabase).

Regards
Ian Dobson

---

### Post by Markus72 on 2008-09-01
Hi Ian,

thanks for your answer.
Where can I set the tuners to stay open if idle?

Thanks
Markus :)

---

### Post by Markus72 on 2008-09-01
Think, I found it. Let's see if something changes...

Thanks!

---

