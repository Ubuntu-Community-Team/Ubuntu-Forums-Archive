---
title: "mplayer maxes out CPU, but only when run from cron or nohup?"
date: 2011-01-22
forum: Multimedia Software
---

### Post by fang2415 on 2011-01-22
I've got a cron job set up to capture a radio station's mp3 stream for a few hours each week using mplayer.  Recently I've noticed that this job will max out the CPU while it's running (top shows it using 96% or so).  The mplayer command is:
```
mplayer -really-quiet -dumpaudio -dumpfile /home/fang2415/podcasts/thisishell`date +%Y%m%d`.mp3 http://live.wnur.org:8094/listen.pls
```

When I run the same command from a terminal, top shows its CPU usage below 1%.  But when I run "nohup [the command]", CPU usage is also ~96%.

Does anybody know what's going on?  Why would cron and nohup use CPU differently than an ordinary terminal?

---

