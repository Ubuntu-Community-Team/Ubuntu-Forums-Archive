---
title: "Upstream Tkt#10712"
date: 2012-05-30
forum: Mythbuntu
---

### Post by mitchell2345 on 2012-05-30
Hi,
Would anyone be able to tell me when upstream tkt 10712 will end up in the mythbuntu deb's?

[http://code.mythtv.org/trac/ticket/10712](http://code.mythtv.org/trac/ticket/10712)

---

### Post by tgm4883 on 2012-05-30
As we discussed in IRC 

> once it hits 0.25, it will be caught in the next build, which happens daily

---

### Post by nickrout on 2012-05-30
If you keep an eye here you can see when it gets committed:

[https://github.com/MythTV/mythtv/commits/fixes/0.25](https://github.com/MythTV/mythtv/commits/fixes/0.25)

---

### Post by bdp on 2012-06-13
I'm completely jammed up by this. Can anyone say roughly what sort of timeline we're looking at?  It has already been several weeks.  Should I just punt on being able to use my HDHomeRun Prime (without cablecard) for the foreseeable future?

To say that I'm frustrated would be quite an understatement. It took me days of repeatedly installing, purging, and reinstalling mythtv, and trying all kinds of changes to my configuration before I finally found this Ticket that explained why I was unable to successfully integrate my new HDHomeRun Prime into my setup.

---

### Post by tgm4883 on 2012-06-13
> **bdp said:**
> I'm completely jammed up by this. Can anyone say roughly what sort of timeline we're looking at?  It has already been several weeks.  Should I just punt on being able to use my HDHomeRun Prime (without cablecard) for the foreseeable future?

To say that I'm frustrated would be quite an understatement. It took me days of repeatedly installing, purging, and reinstalling mythtv, and trying all kinds of changes to my configuration before I finally found this Ticket that explained why I was unable to successfully integrate my new HDHomeRun Prime into my setup.

It should already be available in the mythbuntu repos  [http://mythbuntu.org/repos](http://mythbuntu.org/repos)

---

### Post by bdp on 2012-06-13
I'm running

0.25.0+fixes.20120608.648f0ae

and still having the problem.  I have an old original HDHomeRun (no cablecard slot) which works fine once I delete all the tuners for the HDHR Prime from my list of tuners.  Combined with all my other struggles with this, I feel pretty sure that this bug is the cause of my problem and that the bug fix has not made it into the mythbuntu repos.

Note that in the next to last comment in [http://code.mythtv.org/trac/ticket/10712]("http://code.mythtv.org/trac/ticket/10712") we see
> Milestone changed from unknown to 0.25.1 and in the last comment the (unanswered) question > Will this get pushed into -fixes? 

What should I make of this?

---

### Post by tgm4883 on 2012-06-13
> **bdp said:**
> I'm running

0.25.0+fixes.20120608.648f0ae

and still having the problem.  I have an old original HDHomeRun (no cablecard slot) which works fine once I delete all the tuners for the HDHR Prime from my list of tuners.  Combined with all my other struggles with this, I feel pretty sure that this bug is the cause of my problem and that the bug fix has not made it into the mythbuntu repos.

Note that in the next to last comment in [http://code.mythtv.org/trac/ticket/10712]("http://code.mythtv.org/trac/ticket/10712") we see
 and in the last comment the (unanswered) question 

What should I make of this?

You're right, I was reading the wrong part of the bug report. Let me ping upstream on this.

---

### Post by bdp on 2012-06-17
Any news on this?

---

### Post by nickrout on 2012-06-17
> **bdp said:**
> Any news on this?

You, like all of us, are able to read the commits list on 025-fixes.

It is showing as committed 11 hours ago. Your post is 1 hour ago.

[https://github.com/MythTV/mythtv/commits/fixes/0.25](https://github.com/MythTV/mythtv/commits/fixes/0.25)

It should therefore be in the next mythbuntu 0.25-fixes build.

---

### Post by bdp on 2012-06-19
Thanks. I had followed your earlier recommendation to do the same and didn't find anything of course (several days ago).  In the ensuing confusion over whether it would appear in fixes or not, I guess I decided that I couldn't trust it and forgot about it.

---

