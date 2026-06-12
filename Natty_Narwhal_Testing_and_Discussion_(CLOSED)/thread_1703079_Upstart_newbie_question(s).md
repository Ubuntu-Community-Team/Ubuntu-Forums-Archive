---
title: "Upstart newbie question(s)"
date: 2011-03-08
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Pampelmuse on 2011-03-08
Hi all,

I have a question regarding the upstart system in natty (x64).

There is a certain, very complicated application which depends on many other daemons or programs. I will call this application A.

Usually, I start A manually after rebooting (rebooting is not often necessary), and I stop A manually before rebooting.

This must be done since catastrophic data corruption may occur if other daemons / services are stopped while A is still running. Unfortunately, unplanned shutdown events may occur, and I need a way to handle these in an appropriate fashion.

Since natty relies on upstart, I have tried to do so by writing a job file which should be triggered when the system is shut down. I have done a test setup comprising a very simple script (which runs forever) and a very simple job file, but it won't work regardless what I do. I hope somebody can help me out :-)

The script (filename /root/test; as recommended, not set executable):
```

while true; do Dummy=1; done;

```The job file (filename /etc/init/takedown.conf):
```

start on runlevel [3]
console output
kill timeout 320
task
exec /root/test

```I am testing this setup by first going to runlevel 2 (by typing telinit 2) and then going to runlevel 3 (by typing telinit 3). I would expect that the job is triggered every time when going from runlevel 2 to 3; but that does not seem to be the case. Some observations:

- Immediately after having typed "telinit 3" from within runlevel 2, "ps -Alf" does not show any process "/root/test".
- When typing "runlevel" immediately after having typed "telinit 3" from within runlevel 2, the answer is "2 3", meaning that the current runlevel is already 3.

Both observations lead me to the conclusion that the job just is not triggered, so I suspect that I have used the wrong event syntax or the events I need are not implemented so far. To further investigate, I already have changed the very first line of the jobfile to the following variants (and then conducted tests with the appropriate commands):
```

start on runlevel [0]
start on runlevel [6]
start on shutdown
start on starting runlevel [0]
start on starting runlevel [6]
start on starting shutdown

```None of these work, and I am completely stuck now.

I am more than grateful for any help; just let me explain that I really can't change the situation when it comes to the root of the evil, that is, to the complicated application A. So, unfortunately, any advice telling me to change the situation there will be very interesting, but won't help me out.

In other (more abstract) words, I am forced to find a solution for gracefully and completely ending a process when a shutdown or reboot is done, before any other process / service / application is ended. That means that in case of shutdown or reboot, the very first action must completely end the repective application / program / service, and as long as this is not completed, no other action may take place.

As a last resort, I am thinking of linking the shutdown procedure into SsyV's old Kxx scripts for runlevels 0 and 6, of course choosing xx in a way that the shutdown procedure is performed as first one when entering that run level, and hoping that this will work magically (AFAIK, upstart has a compatibility layer and still executes the old init system in parallel to the new one).

Thank you very much,

Peter

---

### Post by Pampelmuse on 2011-03-14
Thank you very much. I have tried that in the meantime and already got a quality reply on one of my questions. In the future, I will go there first.

---

