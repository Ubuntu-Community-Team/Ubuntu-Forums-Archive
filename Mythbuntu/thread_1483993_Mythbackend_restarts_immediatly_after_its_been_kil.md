---
title: "Mythbackend restarts immediatly after its been killed"
date: 2010-05-15
forum: Mythbuntu
---

### Post by bergqvistjl on 2010-05-15
Hi, just a quick problem (i think, im using mythbuntu 10.04 with the autobuilds option set to 0.24)
Mythbackend refuses to stop, whenever i try to kill the backend using 'sudo killall mythbackend', it restarts, so i usally end up with two mythbackends running. the command to kill and start the backend in mythtv-setup is:
```
killall mythbackend
mythbackend
```
respectivly, it seems to work the first time, but if i go into mythtv-setup again, it tells me the backend is still running, despite the fact ive given the sudo password to kill it. Those two values by the way were there by default when i installed the system.

---

### Post by ian dobson on 2010-05-15
Hi,

mythbackend is started/monitored by upstart, which will respawn the backend when it dies. If you want to stop mythbackend use

stop mythtv-backend

Regards
Ian Dobson

---

### Post by conradin on 2010-05-15
```

kill 9 [PID]

```

or
```

pkill -[signal] [proccess name]

```

kill 9 is essentially the strongest form of kill. killall by default sends SIGTERM unless otherwise specified. SIGKILL aka 9 is the strongest process killing signal.

---

### Post by tgm4883 on 2010-05-15
> **conradin said:**
> ```

kill 9 [PID]

```

or
```

pkill -[signal] [proccess name]

```

kill 9 is essentially the strongest form of kill. killall by default sends SIGTERM unless otherwise specified. SIGKILL aka 9 is the strongest process killing signal.

My understanding is that the issue isn't with the killing of mythbackend, but that it auto-restarts (due to upstart). I don't think what you are suggesting would help

---

### Post by conradin on 2010-05-15
YEah, i geuss I read this wrong. Heres the upstart site which tells you about how to configure jobs.
[http://upstart.ubuntu.com/getting-started.html](http://upstart.ubuntu.com/getting-started.html)

---

### Post by bergqvistjl on 2010-05-15
so what would be the ideal commands for stoppping and starting the backend in the backend setup page then, 'stop mythtv-backend' and 'start mythtv-backend'? And would i need to do it as root?

---

### Post by superm1 on 2010-05-15
> **bergqvistjl said:**
> so what would be the ideal commands for stoppping and starting the backend in the backend setup page then, 'stop mythtv-backend' and 'start mythtv-backend'? And would i need to do it as root?

Yes.

---

