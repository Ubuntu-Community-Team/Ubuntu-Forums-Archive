---
title: "mpd restart each time boot Ubuntu 14.04"
date: 2016-01-12
forum: Multimedia Software
---

### Post by snapback77 on 2016-01-12
MPD installed on Ubuntu 14.04.  Works beautifully until I shut down or reboot.  If so, I must restart MPD to listen to music.  MPD does not start with login.  
Searching helped some.  But, the thread ended without a solution.
1. sudo gedit /etc/default/mpd              START_MPD=true
2. My log: Jan 12 21:55 : pulse_output: Failed to open "My Pulse Output" [pulse]: failed to connect: Connection refused
Then, I restart MPD and everything is fine but annoying. 
Help

---

### Post by shantiq on 2016-01-19
Hi Snapback if you create an autostart file it should be back when you next start up

copy

```
[Desktop Entry]
Encoding=UTF-8
Type=Application
Name=Music Player Daemon
Comment=Server for playing audio files
Exec=mpd
StartupNotify=false
Terminal=false
Hidden=false
X-GNOME-Autostart-enabled=false
```


and save in 

```
~/.config/autostart
``` as mpd.desktop


see pic >>[ATTACH=CONFIG]266831[/ATTACH]

---

