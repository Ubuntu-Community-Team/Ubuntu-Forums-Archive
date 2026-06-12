---
title: "Any one here using Munin"
date: 2008-04-18
forum: Mythbuntu
---

### Post by ian dobson on 2008-04-18
Hi,

Anyone here (MythTV users) running munin to monitor backend servers/frontend systems?

I'm currently working on a munin plugin for MythTV that monitors Encoders/Jobs/EPG/schedules and need afew users to help test it before I release it to the wide world

Graphics can be see here [http://mail.planet-ian.com/munin/planet-ian.com/index.html](http://mail.planet-ian.com/munin/planet-ian.com/index.html)

Code is here: [http://mail.planet-ian.com/munin/mythtv_status_](http://mail.planet-ian.com/munin/mythtv_status_)

Regards
Ian Dobson

---

### Post by ian dobson on 2008-07-02
Hi,

Updated the script, it now uses alot less resources as it doesn't use the XML status page, which appears to have a leak in mythtv-backend.

Regards
Ian Dobson

---

### Post by UberMiga on 2008-08-15
I love to have a go at it :)

The graph looks very nice indeed.

---

### Post by ian dobson on 2008-08-15
Hi,

You can download th code from the munin webpage [http://munin.projects.linpro.no/](http://munin.projects.linpro.no/)

Regards
Ian Dobson

---

### Post by newlinux on 2008-08-15
I'd never seen munin before. when I get some time I'll look into installing and configuring, since it's in the repos.

---

### Post by newlinux on 2009-07-02
I know it is almost a year later, but I went ahead and set this up. Thanks for the plugin.

---

### Post by ian dobson on 2009-07-02
Hi,

Glad you like it. You can see the myth scripts in action here:- [http://mail.planet-ian.com/munin/planet-ian.com/index.html](http://mail.planet-ian.com/munin/planet-ian.com/index.html)


Regards
Ian Dobson

---

### Post by newlinux on 2009-07-03
I appreciate the script, so I hope i am not sounding like a complainer, but for mythtv_status_schedule the number of upcoming programs seems to include deactivated and duplicate recordings, which aren't going to actually be recorded. the count is way high compared to my actual scheduled recordings, and I think it is because it is counting deactivated and duplicates (I have recording schedules for programs that come on multiple times a day).

But very nice. I appreciate the scripts.

---

### Post by ian dobson on 2009-07-04
> **newlinux said:**
> I appreciate the script, so I hope i am not sounding like a complainer, but for mythtv_status_schedule the number of upcoming programs seems to include deactivated and duplicate recordings, which aren't going to actually be recorded. the count is way high compared to my actual scheduled recordings, and I think it is because it is counting deactivated and duplicates (I have recording schedules for programs that come on multiple times a day).


I've seen this as well and I planned to change the schedule over to using a stacked graph (like recorded) some day. I started to try and decode the status information stored in the database to work out what is what but gave up after a while as I couldn't find any correlatin between the status codes in the db and what mythweb was showing.

 Regards
Ian Dobson

---

### Post by newlinux on 2009-07-04
> **ian dobson said:**
> I've seen this as well and I planned to change the schedule over to using a stacked graph (like recorded) some day. I started to try and decode the status information stored in the database to work out what is what but gave up after a while as I couldn't find any correlatin between the status codes in the db and what mythweb was showing.

 Regards
Ian Dobson

yeah, maybe it's some logic in the scheduler code instead of just a field in the DB that keeps track of this... thanks!

---

### Post by ian dobson on 2009-07-05
Hi,

maybe it the real point. That's one thing I hate about mythtv/most open source projects, documentation is quite often very limited.

Regards
Ian Dobson

---

### Post by ian dobson on 2010-10-02
> **newlinux said:**
> I appreciate the script, so I hope i am not sounding like a complainer, but for mythtv_status_schedule the number of upcoming programs seems to include deactivated and duplicate recordings, which aren't going to actually be recorded. the count is way high compared to my actual scheduled recordings, and I think it is because it is counting deactivated and duplicates (I have recording schedules for programs that come on multiple times a day).

But very nice. I appreciate the scripts.

Well over a year later, and I've found out how you can grab a list of scheduled/repeated/conflicting recordings :-
QUERY_GETALLPENDING through the MythProtocol.

Now I know this I can hack the myth script using the MythTV perl object to grab the schedule info. First of all I'll need to finish off another (mythtv frontend based) project, but once that's done I hack the munin script.

I'll upload a new version to munin exchange once I'm finished.

Regards
Ian Dobson

---

### Post by ian dobson on 2010-10-02
Hi,

OK, just hacked something together using the MythTV object and QUERY_GETALLPENDING. The trend is here:- [http://mail.planet-ian.com/munin/planet-ian.com/alpha2.planet-ian.com/mythtv_status_schedule.html](http://mail.planet-ian.com/munin/planet-ian.com/alpha2.planet-ian.com/mythtv_status_schedule.html)

And the updated encoder trend is here:- [http://mail.planet-ian.com/munin/planet-ian.com/alpha2.planet-ian.com/mythtv_status_encoder.html](http://mail.planet-ian.com/munin/planet-ian.com/alpha2.planet-ian.com/mythtv_status_encoder.html)

I'll update the new script to munin exchange in afew days if everything works as planned.

Regards
Ian Dobson

---

