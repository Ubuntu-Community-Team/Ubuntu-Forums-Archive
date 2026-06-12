---
title: "Pulse Has Decided to Stop Working"
date: 2020-10-01
forum: Multimedia Software
---

### Post by wewantutopia on 2020-10-01
Hello, I'm running 16.04.  This system has run essentially flawlessly for years.  Yesterday pulseaudio decided it was going to stop working.  I've made no changes.

Here is the syslog output

```
Oct  1 08:12:53 dk systemd[1485]: Stopped Sound Service.Oct  1 08:13:16 dk systemd[1485]: Starting Sound Service...
Oct  1 08:13:16 dk rtkit-daemon[1921]: Successfully made thread 4403 of process 4403 (n/a) owned by '1000' high priority at nice level -11.
Oct  1 08:13:16 dk rtkit-daemon[1921]: Supervising 5 threads of 2 processes of 1 users.
Oct  1 08:13:16 dk pulseaudio[4403]: E: [pulseaudio] pid.c: Daemon already running.
Oct  1 08:13:16 dk pulseaudio[4403]: E: [pulseaudio] main.c: pa_pid_file_create() failed.
Oct  1 08:13:16 dk systemd[1485]: pulseaudio.service: Main process exited, code=exited, status=1/FAILURE
Oct  1 08:13:16 dk systemd[1485]: Failed to start Sound Service.
Oct  1 08:13:16 dk systemd[1485]: pulseaudio.service: Unit entered failed state.
Oct  1 08:13:16 dk systemd[1485]: pulseaudio.service: Failed with result 'exit-code'.
Oct  1 08:13:16 dk systemd[1485]: pulseaudio.service: Service hold-off time over, scheduling restart.
Oct  1 08:13:16 dk systemd[1485]: Stopped Sound Service.
Oct  1 08:13:16 dk systemd[1485]: Starting Sound Service...
Oct  1 08:13:16 dk rtkit-daemon[1921]: Successfully made thread 4407 of process 4407 (n/a) owned by '1000' high priority at nice level -11.
Oct  1 08:13:16 dk rtkit-daemon[1921]: Supervising 5 threads of 2 processes of 1 users.
Oct  1 08:13:16 dk pulseaudio[4407]: E: [pulseaudio] pid.c: Daemon already running.
Oct  1 08:13:16 dk pulseaudio[4407]: E: [pulseaudio] main.c: pa_pid_file_create() failed.
Oct  1 08:13:16 dk systemd[1485]: pulseaudio.service: Main process exited, code=exited, status=1/FAILURE
Oct  1 08:13:16 dk systemd[1485]: Failed to start Sound Service.
Oct  1 08:13:16 dk systemd[1485]: pulseaudio.service: Unit entered failed state.
Oct  1 08:13:16 dk systemd[1485]: pulseaudio.service: Failed with result 'exit-code'.
Oct  1 08:13:16 dk systemd[1485]: pulseaudio.service: Service hold-off time over, scheduling restart.
Oct  1 08:13:16 dk systemd[1485]: Stopped Sound Service.
Oct  1 08:13:17 dk systemd[1485]: Starting Sound Service...
Oct  1 08:13:17 dk rtkit-daemon[1921]: Successfully made thread 4410 of process 4410 (n/a) owned by '1000' high priority at nice level -11.
Oct  1 08:13:17 dk rtkit-daemon[1921]: Supervising 5 threads of 2 processes of 1 users.
Oct  1 08:13:17 dk pulseaudio[4410]: E: [pulseaudio] pid.c: Daemon already running.
Oct  1 08:13:17 dk pulseaudio[4410]: E: [pulseaudio] main.c: pa_pid_file_create() failed.
Oct  1 08:13:17 dk systemd[1485]: pulseaudio.service: Main process exited, code=exited, status=1/FAILURE
Oct  1 08:13:17 dk systemd[1485]: Failed to start Sound Service.
Oct  1 08:13:17 dk systemd[1485]: pulseaudio.service: Unit entered failed state.
Oct  1 08:13:17 dk systemd[1485]: pulseaudio.service: Failed with result 'exit-code'.
Oct  1 08:13:17 dk systemd[1485]: pulseaudio.service: Service hold-off time over, scheduling restart.
Oct  1 08:13:17 dk systemd[1485]: Stopped Sound Service.
Oct  1 08:13:17 dk systemd[1485]: Starting Sound Service...
Oct  1 08:13:17 dk rtkit-daemon[1921]: Successfully made thread 4412 of process 4412 (n/a) owned by '1000' high priority at nice level -11.
Oct  1 08:13:17 dk rtkit-daemon[1921]: Supervising 5 threads of 2 processes of 1 users.
Oct  1 08:13:17 dk pulseaudio[4412]: E: [pulseaudio] pid.c: Daemon already running.
Oct  1 08:13:17 dk pulseaudio[4412]: E: [pulseaudio] main.c: pa_pid_file_create() failed.
Oct  1 08:13:17 dk systemd[1485]: pulseaudio.service: Main process exited, code=exited, status=1/FAILURE
Oct  1 08:13:17 dk systemd[1485]: Failed to start Sound Service.
Oct  1 08:13:17 dk systemd[1485]: pulseaudio.service: Unit entered failed state.
Oct  1 08:13:17 dk systemd[1485]: pulseaudio.service: Failed with result 'exit-code'.
Oct  1 08:13:17 dk systemd[1485]: pulseaudio.service: Service hold-off time over, scheduling restart.
Oct  1 08:13:17 dk systemd[1485]: Stopped Sound Service.
Oct  1 08:13:17 dk systemd[1485]: Starting Sound Service...
Oct  1 08:13:17 dk rtkit-daemon[1921]: Successfully made thread 4414 of process 4414 (n/a) owned by '1000' high priority at nice level -11.
Oct  1 08:13:17 dk rtkit-daemon[1921]: Supervising 5 threads of 2 processes of 1 users.
Oct  1 08:13:17 dk pulseaudio[4414]: E: [pulseaudio] pid.c: Daemon already running.
Oct  1 08:13:17 dk pulseaudio[4414]: E: [pulseaudio] main.c: pa_pid_file_create() failed.
Oct  1 08:13:17 dk systemd[1485]: pulseaudio.service: Main process exited, code=exited, status=1/FAILURE
Oct  1 08:13:17 dk systemd[1485]: Failed to start Sound Service.
Oct  1 08:13:17 dk systemd[1485]: pulseaudio.service: Unit entered failed state.
Oct  1 08:13:17 dk systemd[1485]: pulseaudio.service: Failed with result 'exit-code'.
Oct  1 08:13:17 dk systemd[1485]: pulseaudio.service: Service hold-off time over, scheduling restart.
Oct  1 08:13:17 dk systemd[1485]: Stopped Sound Service.
Oct  1 08:13:17 dk systemd[1485]: pulseaudio.service: Start request repeated too quickly.
Oct  1 08:13:17 dk systemd[1485]: Failed to start Sound Service.
Oct  1 08:13:17 dk systemd[1485]: pulseaudio.service: Unit entered failed state.
Oct  1 08:13:17 dk systemd[1485]: pulseaudio.service: Failed with result 'start-limit-hit'.
```

I've already purged and reinstalled pulseaudio.  It seemed to work yesterday but this morning, after boot up, I'm having the same issue.

Any ideas?  

Thanks!

---

### Post by wewantutopia on 2020-10-07
This issue persists.  Some days it works fine others nothing.  Sound settings shows no "device for sound output"  or "device for sound input". 

 ```
 aplay -l
``` outputs

```
**** List of PLAYBACK Hardware Devices ****card 0: PCH [HDA Intel PCH], device 0: ALC269VC Analog [ALC269VC Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

so everything looks good there.


```
ps x | grep pulseaudio
```  outputs

```
 1502 ?        S<sl   0:00 /usr/bin/pulseaudio --daemonize=no 3722 pts/2    S+     0:00 grep --color=auto pulseaudio

```





Any ideas?  Thanks!

---

