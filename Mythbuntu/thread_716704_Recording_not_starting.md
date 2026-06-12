---
title: "Recording not starting"
date: 2008-03-06
forum: Mythbuntu
---

### Post by axcairns on 2008-03-06
Hey all,

My mythtv server crashed and I had to reinstall so I decided to give mythbuntu gutsy a go. I got everything up and running and can watch tv but cannot get any recording scheduled.

When I schedule through mythweb I see the schedule in the Recording Schedules tab but nothing ever shows up in the Upcoming Recordings tab and nothing records. 

When I schedule through mythfrontend it saves my schedule (which is then visible in mythweb Recording Schedules tab) but when I go back into the program it says the program is not to be recorded.

Any ideas?

Thanks,

Allan

---

### Post by majoridiot on 2008-03-06
> **axcairns said:**
> Hey all,

My mythtv server crashed and I had to reinstall so I decided to give mythbuntu gutsy a go. I got everything up and running and can watch tv but cannot get any recording scheduled.

When I schedule through mythweb I see the schedule in the Recording Schedules tab but nothing ever shows up in the Upcoming Recordings tab and nothing records. 

When I schedule through mythfrontend it saves my schedule (which is then visible in mythweb Recording Schedules tab) but when I go back into the program it says the program is not to be recorded.

Any ideas?

Thanks,

Allan

have you checked the backend logs in /var/log/mythtv to see if there are any errors, etc. that might
help track down what's going wrong?

---

### Post by axcairns on 2008-03-06
Nothing in the log looks relevant -

```
allan@library:~$ cat /var/log/mythtv/mythbackend.log
2008-03-07 08:11:54.607 MainServer::HandleAnnounce Monitor
2008-03-07 08:11:54.627 adding: library as a client (events: 0)
2008-03-07 08:11:59.292 MainServer::HandleAnnounce Monitor
2008-03-07 08:11:59.302 adding: library as a client (events: 0)
allan@library:~$ 
```

---

### Post by newlinux on 2008-03-06
You should look further back in your logs (mythbackend.log.1, mythbackend.log.2, etc.). What reason does it give for the program not to be recorded? Also, have you looked at your tuner status? Can you watch these scheduled programs that don't get recorded live in myth?

---

