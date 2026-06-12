---
title: "Pulseaudio Real Time help"
date: 2011-01-30
forum: Multimedia Software
---

### Post by NightwishFan on 2011-01-30
In 9.10, you could get pulseaudio to achieve SCHED_FIFO simply by adding yourself to the pulse-rt group. With Ubuntu 10.04 and above this is not needed because of the inclusion of Rtkit. This is where I have a problem.

Even though Rtkit lets me have -11 nice, even if I set it explicitly to use realtime it is always sched_normal. I added myself to all the pulse groups, audio and rtkit and still nothing.

I had an idea that might even be better considering pulseaudio runs as a per user task. I was thinking I could patch my kernel with bfs, which has a pseudo realtime policy for apps that request but do not have permission. This does not work, it always uses sched_normal. I assumed removing rtkit would help, but it did not either.

Does anyone have any answers? If anything I would prefer to have it "request but not have permission" so BFS gives it pseudo real time priority.

---

### Post by tstraumann on 2011-09-24
I thought I observed the same (10.10). However, *only* the IO threads
use the real-time scheduler SCHED_RR; the main program uses a low 'nice'
value. You don't see these thread's priorities when you do just

ps -p <pulseaudio_pid> -o pid,nice,rtprio,sched,command

  PID  NI RTPRIO SCH COMMAND
11637 -11      -   0 /usr/bin/pulseaudio --start --log-target=syslog


If I print info about threads (m) then I see:

ps -p <pulseaudio_pid> m -o pid,tid,nice,rtprio,sched,command

  PID  NI RTPRIO SCH COMMAND
11637   -      -   - /usr/bin/pulseaudio --start --log-target=syslog
    - -11      -   0 -
    -   -      5   2 -
    -   -      5   2 -

---

