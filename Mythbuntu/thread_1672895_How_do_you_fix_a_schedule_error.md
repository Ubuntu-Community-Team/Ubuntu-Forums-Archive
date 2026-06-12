---
title: "How do you fix a schedule error?"
date: 2011-01-21
forum: Mythbuntu
---

### Post by keepitsimpleengr on 2011-01-21
I have an error that shows two identical episodes one week apart.  The first (1/26/2011) is incorrect and identical to the second (2/2/2011) one which is correct.

ScheduleDirect's listing is correct.

Is there someway to clear or reset then reload the listings?

---

### Post by tgm4883 on 2011-01-21
IIRC, when mythfilldatabase runs, the current day's schedule gets updated as well as 14 days out gets downloaded. Days 2-13 don't get updated at all. 

There is a mythfilldatabase command that you can run to refresh all of the listings, but unless it's causing problems I'd let it fix itself on that day.

---

### Post by novellahub on 2011-01-21
To refresh all the listings:

```
mythfilldatabase --refresh-all
```

To update just certain day:

```
mythfilldatabase --refresh-day 1
```

For a expanded explanation, go here:

[http://www.mythtv.org/wiki/Mythfilldatabase](http://www.mythtv.org/wiki/Mythfilldatabase)

---

### Post by keepitsimpleengr on 2011-01-22
> **novellahub said:**
> To refresh all the listings:

```
mythfilldatabase --refresh-all
```

To update just certain day:

```
mythfilldatabase --refresh-day 1
```

For a expanded explanation, go here:

[http://www.mythtv.org/wiki/Mythfilldatabase](http://www.mythtv.org/wiki/Mythfilldatabase)

Worked like a charm!

Thanks! :guitar:

---

