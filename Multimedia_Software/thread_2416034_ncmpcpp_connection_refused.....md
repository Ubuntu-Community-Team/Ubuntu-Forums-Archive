---
title: "ncmpcpp connection refused...."
date: 2019-04-04
forum: Multimedia Software
---

### Post by Furycd001 on 2019-04-04
HI Guys. I've just installed mpd, mpc & ncmpcpp. When I first launched ncmpcpp it would not load any music, so I tried pressing "u" to update & also running the update command. After several ducks I ran out of time and had to leave the house so I switched off my laptop. Upon turning on my laptop, ncmpcpp just says connection refused now. [Here is a copy of my MPD config file]("https://paste.ubuntu.com/p/K5XFg48WHC/") && [here is a copy of my ncmpcpp config file]("https://paste.ubuntu.com/p/WbmX8xy7Qt/") Thank you in advanced for all your help and comments....

---

### Post by slickymaster on 2019-04-04
*Thread moved to **Multimedia Software**.*

---

### Post by Furycd001 on 2019-04-04
I tried running the following command....

```
MPD_HOST=localhost mpc status
```

It returns: [B]mpd error: Connection refused

[/B]

---

### Post by Furycd001 on 2019-04-05
I'm trying to run as user & when i try to run mpd I get the following....

```
Apr 05 09:30 : socket: Failed to bind to '/run/mpd/socket': Address already in use
```

---

### Post by Furycd001 on 2019-04-05
What does this mean and how can I go about fixinf it ?? I'm still referencing [this documentation]("https://help.ubuntu.com/community/MPD") on running mpd as a user service....

```

furycd001 >> sudo systemctl stop mpd && sudo systemctl disable mpd
Synchronizing state of mpd.service with SysV init with /lib/systemd/systemd-sysv-install...
Executing /lib/systemd/systemd-sysv-install disable mpd
insserv: warning: current start runlevel(s) (empty) of script `mpd' overrides LSB defaults (2 3 4 5).
insserv: warning: current stop runlevel(s) (0 1 2 3 4 5 6) of script `mpd' overrides LSB defaults (0 1 6).
insserv: warning: current start runlevel(s) (empty) of script `mpd' overrides LSB defaults (2 3 4 5).
insserv: warning: current stop runlevel(s) (0 1 2 3 4 5 6) of script `mpd' overrides LSB defaults (0 1 6).
Removed symlink /etc/systemd/system/sockets.target.wants/mpd.socket.

```

---

### Post by Furycd001 on 2019-04-05
Every time I try to launch mpd I get the same message....
```

Apr 05 22:34 : socket: Failed to bind to '/run/mpd/socket': Address already in use

```

---

### Post by Furycd001 on 2019-04-06
Ok so I managed to fix everything from reading around the internet. Here's what fixed it for me if you happen to read this in the future....

```

First open **/home/username/.mpd** & delete **mpd.db**

Next Open up **mpd.conf** & look for **bind_to_address "/run/mpd/socket"**

Change this to [B]bind_to_address        "localhost"
[/B]
```Save the file. Killall mpd processes and then relaunch. For me mpd now launched without any problems and I was able to open ncmpcpp and start loading in my music library.

---

