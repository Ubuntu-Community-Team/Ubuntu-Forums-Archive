---
title: "ACPI Time is one hour late since upgrade to 0.26"
date: 2012-11-04
forum: Mythbuntu
---

### Post by Steve666 on 2012-11-04
I am running version 0.26 now. Since I upgraded the backend sends now the wrong wakeuptime to setwakeup.sh. It is probably connected to the new timetable feature in 0.26. The problem is now that mythbuntu wakes up one hour too late (since we are in time zone UTC+1) thus missing the scheduled recordings. 
The system time is set to UTC and the timeshift UTC+1 is correctly recognized while the system is live. Therefore, it is probably a bug in the system regarding the time handing over procedure from the backend to setwakeup.sh during the shutdown procedure.
Does anybody else recognized the problem?
Does anybody know if this bug has been detected for fixing?
Does anybody know what I can enter into setwakeup.sh in order to have a quick fix until it is fixed in the mythbuntu development?

---

### Post by jksj on 2012-11-05
I suffered from a similar problem in early 0.26 (August).
Raised ticket [http://code.mythtv.org/trac/ticket/10995](http://code.mythtv.org/trac/ticket/10995).
Later releases of 0.26 fixed it for me (UK based) but the ticket is still open. As a workround add 1 hour to StartupSecsBeforeRecording. You can do this in Mythweb.

---

### Post by Steve666 on 2012-11-11
Thanks for the hint. It works as a workaround. :)
Nevertheless, it is a little odd approach. In MythWeb I can enter 3600 secs, although in the backup setting you cannot enter more than 1200 secs and only the 1200 secs are shown even if I entered the 3600 secs in MythWeb. But as I said, it is a workaround solution until the bug is fixed in the system.

---

### Post by Rotak on 2012-11-12
As another workaround, you can tweak your setwakeup.sh.

Replace
```
SECS=$1
```with
```
SECS=`expr $1 - 3600`
```I used this, because I will never ever remember to remove those additional 3600 secs from the startup time, but I will recognize if a recording fails, once the bug is fixed.

---

### Post by Steve666 on 2012-11-14
Thanks, I was also thinking about tweaking setwakeup.sh, but was not sure about the exact code. Have not tried the option but looks reasonable.

---

### Post by Steve666 on 2012-12-29
Looks like the problem disappeared now after I made a patch on 26th/Dec. :p

---

### Post by nickrout on 2012-12-30
> **Steve666 said:**
> Looks like the problem disappeared now after I made a patch on 26th/Dec. :pPresumably related to this fix [https://github.com/MythTV/mythtv/commit/b28041a11711a2ddd9eb63f8eee0c1ce3009c4ac](https://github.com/MythTV/mythtv/commit/b28041a11711a2ddd9eb63f8eee0c1ce3009c4ac)

---

