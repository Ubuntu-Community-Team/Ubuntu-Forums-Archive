---
title: "Backend Problem - (Failed to bind port 3. Exiting.)"
date: 2009-06-19
forum: Mythbuntu
---

### Post by RTucker on 2009-06-19
Hi,

Something weird happened to my mythbuntu box last night... It was watching live tv and everything was fine then I pressed escape to go back to the main menu. As soon as I pressed escape the back end crashed (front end was still running fine).

Now, every time I try to start the backend (either with mythbackend or /etc/init.d/mythtv-backend) I get 20 or so lines ending with:
```
QServerSocket: failed to bind or listen to the socket
2009-06-18 18:24:39.450 Failed to bind port 3. Exiting.
```

I did search for an answer, but there is only one other mention of this error and there were no replies to it.

I currently the system is completely up to date.

Thanks in advance for any info.

---

### Post by RTucker on 2009-06-19
I've also noticed some other strange things that seem to have started at the same time as this problem.

Firstly, every time the system starts up mythfrontend starts as normal, however a console window and the update manager gui also start (behind mythfrontend).

Also, When i shut the system down it doesn't actually turn off, it goes through the process then just site there with "Power Down" at the top of the screen until you actually turn the power off.

FYI, the mysql is running and I can connect to the mythconverg database...

---

### Post by RTucker on 2009-06-20
Ok, so here's some more info:

```
ps aux | grep mythbackend
``` shows nothing running

netstat shows nothing using port '3'

I have tried removing &#65279;~/.mythtv and /home/mythtv/.mythtv

I have run &#65279;```
sudo dpkg-reconfigure mythtv-database
``` and ```
sudo dpkg-reconfigure mythtv-common
``` and it made no difference.

---

