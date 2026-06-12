---
title: "one chanel has no schedule information"
date: 2012-10-23
forum: Mythbuntu
---

### Post by itlarson on 2012-10-23
One of the chanels in my guide has no information.  This is the same for two different mythtv frontend/backend machines, one running 10.04, the other running 12.04.  Schedules direct appears to have information for the channel, which is 2.3 in Minneapolis/Saint Paul.  Any ideas how to fix this?

---

### Post by mikitz on 2012-10-23
You could try mc2xml and set up an update as a cron job at 3am daily.. This worked for me [http://mc2xml.hosterbox.net/](http://mc2xml.hosterbox.net/)

---

### Post by itlarson on 2012-10-23
Not quite clear on what that does- could you explain?  what does this do that mythfilldatabase doesn't?

so far I havere-scanned channels, deleted and recreated my chanel linup, and run "sudo mythfilldatabase --refresh-all"

---

### Post by klc5555 on 2012-10-24
Check the 5-digit xmltvid number that mythtv has for this particular channel. Either in Channel Editor or from Live TV after pressing the "e" editor key while the offending station is on-screen.

Compare this 5-digit xmltvid number with one SchedulesDirect has for the channel. If they differ, or if mythtv did not have an xmltvid number for the channel at all, manually enter the correct xmltvid  number gotten from SchedulesDirect into either of the two locations indicated above.

Then run mythfilldatabase. Note that --refresh-all will start filling in with _tomorrow's_  listings. If you want today's listings also filled in, it will require an explicit --refresh-today switch.

Note also that some channels, usually local access channels, simply won't have scheduling information, even though SchedulesDirect provides an xmltvid number for them. I don't know whether your Minneapolis station is one of these or not.

---

### Post by itlarson on 2012-10-24
Thanks- I have been suspecting something like that.  The station definitely will have schedule info since it is a local broadcast PBS station.  They have two physical broadcast frequencies, and 2.3 is the first channel on the second frequency.  The recently realigned their stations to make it high-def, which is why I thought re-scanning would work.  I'm wondering if Schedules direct just didn't get the memo about the realignment, and is still using the old ID#?  

I will try to do this tonight and report back if it works.

---

### Post by itlarson on 2012-10-24
That seems to have done it.  I had to run "sudo mythfilldatabase --refresh 1-14" as "refresh-all" is deprecated.  Thanks for the help.

---

### Post by klc5555 on 2012-10-25
Glad it worked.

I'd forgotten about the updated and changed mythfilldatabase options. Thanks for the reminder. You shouldn't have to use "sudo" to run mythfilldatabase, however, and probably mythfilldatabase ought not to run with root privileges in any event, because it has always (at least to me) seemed to be a somewhat insecure script and open to hacking.

---

### Post by itlarson on 2012-10-25
It seemed like it didn't work until I did it as root.  Maybe because I am not user "mythtv"?  

So was this all caused by Schedules Direct using the wrong xmltvid?

---

### Post by klc5555 on 2012-10-25
No, any regular user account ought to be able to run mythfilldatabase if things are set up mostly correctly. 

But the problem wasn't SchedulesDirect using a wrong xmltvid, but rather mythtv having the wrong xmltvid entered (or none). Automated probing for xmltvids isn't completely reliable. Sometimes probing during a scan or rescan doesn't pull the xmltvid in; sometimes I've noticed that when the local cable co. changes frequencies around, after a rescan mythtv will keep the xmltvid of the channel that used to be on a frequency and pair it with the (albeit otherwise correctly identified) station that occupies the frequency now. Other odd interactions happen may happen too between the signal provider and mythtv during scanning, all of which have to be fixed manually but none of which are issues with SchedulesDirect or the information they provide.

With my own cable providers, I've never had a mythtv installation able to pull in most xmltvids. Since SchedulesDirect came online in 2007 I've always had to enter all the xmltvids by hand, and reedit changes manually after every rescan.

---

