---
title: "[SOLVED] Guide Data Wrong"
date: 2008-10-09
forum: Mythbuntu
---

### Post by false_apology on 2008-10-09
I've been noticing some weirdness with my guide data since I setup MythTV. I'm using Myth v0.21.20080304-1 on Ubuntu 8.04.1. It seems that when I open the guide, or watch LiveTV, the descriptions are wrong or the show designations are wrong. I don't know if this is just a display thing in the front end, or if the data is wrong in the myth database. For example, tonight it showed from 8-9 on NBC (8.1 here) is "Survivor Gabon". But Survivor is on CBS, not NBC. And sometimes the show will be right but it will display the description for something COMPLETELY different. This seems to happen on and off, its not ALWAYS wrong, it somehow "fixes" itself and the breaks again.

I have a subscription through Schedules Direct to get my TV listing data. Any ideas what could be causing this? Anyone else experience similar issues? Is there an easy way to tell if the guide data is actually bad or if the frontend is just displaying the wrong info?

Thanks a lot.

---

### Post by newlinux on 2008-10-10
I haven't had this problem, but maybe at some point something in your guide data was screwed up. might be time to just try refreshing it all:

```

mythfilldatabase --refresh-all

```

and see if that helps. Also make sure there are no errors with your database tables - you can run the optimize and repair script on them.

---

### Post by false_apology on 2008-10-13
Thanks, I'll give it a try.

---

### Post by false_apology on 2008-10-14
I ran that command and found the "optimize tables" perl script and ran that. This seemed to fix it, but after an hour or two it happened again. (It was saying Antiques Road Show was on CBS!). I was tinkering a little more and I *think* the problem was I had the "Use EIT data" set in my mythbackend setup. Not sure if this is possible, but I think Schedules Direct and EIT were conflicting with eachother giving me this weird output on the guide. So I un-ticked that option and re-ran the "refresh all" command. So far so good for about 24 hours, so hopefully that resolved it.

Thanks

---

