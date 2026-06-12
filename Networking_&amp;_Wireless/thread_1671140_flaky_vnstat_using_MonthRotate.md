---
title: "flaky vnstat using MonthRotate"
date: 2011-01-19
forum: Networking &amp; Wireless
---

### Post by terminator14 on 2011-01-19
One of the tools I use to monitor traffic going through my linux based router is vnstat v1.10. My main focus is the amount of traffic that passes through my router each month, because my ISP starts charging extra if you exceed a monthly limit. The problem is - the ISP doesn't count a month from the 1st of the month to the end of the same month, it counts it from a specific day to a month from that day.

Luckily, vnstat comes with a feature that addresses that very problem. In vnstat's config file, there's a settings that reads:

```
MonthRotate #
```

which is used to set this day.

Unfortunately, changing this setting seems to have gotten vnstat confused.

When I first installed vnstat, it ran with the default config file for a few hours. Then, I changed it to count a month beginning on the 9th since that's how my ISP did it. It seemed not to have switched at first but after a few days it seemed like maybe it was working ok. About 2 months later I was on the phone with my ISP and found out they actually use a different date to start and end the monthly cycle, so I changed the setting to the 6th (the new day), and restarted the vnstat daemon once again. Now

```
vnstat -m
```

shows random data. Running the command can show the total for every month counting from the 9th one second, and running exactly the same command a few seconds later will show completely different data for all months which is accurate if you count daily from the 6th. 

Why is vnstat so flaky when it comes to different days of the month? Is there way to reset it's monthly counters (make it recount) without deleting all my daily stats? I tried 

```
vnstat --rebuildtotal
```

but that doesn't seem to have done anything. Or if I clear all data recorded so far, will is it guaranteed to work from then on, as long as I don't change the MonthRotate setting from the 6th anymore?

---

