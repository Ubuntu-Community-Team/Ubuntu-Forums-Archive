---
title: "Myth shutting down with frontend still running"
date: 2014-11-02
forum: Mythbuntu
---

### Post by JasonEde on 2014-11-02
I've had a few problems lately with myth shutting down when the front end is still running... I'm running on mythbuntu 12.04 and myth 0.26 with all the latest updates...

This has only happened recently and has been repeatable. Myth has been started up into mythwelcome and then hit the button to start frontend... Then I've been connecting to the myth from a remote machine to stream a film over wireless and then 5 minutes later I can see the backend scheduling a shutdown.

Nov  2 17:42:32 jason-pc mythlogserver: mythbackend[2158]: I Scheduler scheduler.cpp:2864 (CheckShutdownServer) CheckShutdownServer returned - OK to shutdown
Nov  2 17:42:32 jason-pc mythlogserver: mythbackend[2158]: N Scheduler scheduler.cpp:2949 (ShutdownServer) Running the command to set the next scheduled wakeup time :-#012#011#011#011#011#011#011mythshutdown --setwakeup 2014-11-02T20:49:00

Not sure if the problem is an update or the check shutdown is falsely returning ok when it shouldn't be. I did think that myth should never shutdown if the frontend was running and that certainly used to be the behaviour.

Any thoughts about what to check?

Jason

---

### Post by dannyboy79 on 2014-11-02
are you certain you're running the same mythtv version on your remote frontend? 0.27 is out, maybe give that  a try? should be able to enable the mythbuntu repo's and get 0.27 without much hassle

---

### Post by JasonEde on 2014-11-03
My myth is a combined frontend/backend... At that time I was streaming a program off it using windows media player. I might move up to 0.27, but I need to find a quiet window in our recording schedule so that i have the time to work on it properly if it doesn't go smoothly.

However, I had used VNC to start up the front-end from mythwelcome rather than the remote although that shouldn't have made a difference. When I started it properly with the remote it did seem to stay up.

---

### Post by JasonEde on 2014-11-12
It does seem like if myth front end is started up by VNC and the VNC session connects then it still shuts down after 5 minutes of inactivity, but if the remote is used to power it up then it stays up.

This only happened after recentish updates so I'm guessing behaviour has been changed at some point...

---

### Post by khPWXxF on 2014-11-12
With 0.27, in the frontend setup > general > page 8 there is a field 'Idle time before entering standby mode (minutes):'
Is your 0.26 the same and is it that which is triggering your shutdown?

Phil

---

