---
title: "Ping, no internet after upgrade"
date: 2010-08-28
forum: Networking &amp; Wireless
---

### Post by waggers on 2010-08-28
I'm having the exact [same trouble]("http://ubuntuforums.org/showthread.php?p=9777773"). I've just upgraded from Ubuntu 8.4 to 10.4 and suddenly no internet access, but I'm able to ping as above.  I've been using Ubuntu for about a year now but don't know it all that well "under the hood" so don't know where to start looking for a solution. Any help would be much appreciated...

---

### Post by waggers on 2010-08-28
Ok, I've just noticed the Epiphany web browser, and tried it... and it works, I have web access! But of course all my bookmarks, history etc. are in Firefox, and we use Thunderbird for our email, so ideally still need to get these working.  I'm confused as to why one web browser would work and another wouldn't, fresh from an upgrade...

---

### Post by waggers on 2010-08-28
So... I saw that Chromium is available, started to install it; while I was waiting I opened Firefox and suddenly it works. Thunderbird still times out though when trying to access our mail, so I'll carry on working on that.

I'd be interested if any of this helps the others who had the same problems?

---

### Post by waggers on 2010-08-29
Spoke too soon - Firefox and Thunderbird are still timing out but Chrome works fine.  I did come across this thread on the Firefox support forum:
[https://support.mozilla.com/pt-BR/questions/664450](https://support.mozilla.com/pt-BR/questions/664450)

It suggests making some changes to etc/systl.conf, which doesn't exist; I presumed it meant etc/sysctl.conf, but making the said changes to that file had no effect for me.

Given this, plus the [random crashes]("http://ubuntuforums.org/showthread.php?t=1476793&page=2") and the (now resolved) [proc/bus/usb mounting problem]("http://ubuntuforums.org/showthread.php?t=1467081") I'm surprised version 10.04 was deemed ready to release. If I'd known I'd have all these problems I wouldn't have upgraded.

---

### Post by waggers on 2010-08-29
Ok, finally solved the Thunderbird & Firefox problem, by disabling ipv6 in their respective about:config files. Haven't had a crash in a little while either, so fingers crossed

---

### Post by Iowan on 2010-08-29
Moved to new thread.
Remember to mark it [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") when you're done... :)

---

