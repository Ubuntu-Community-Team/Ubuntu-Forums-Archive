---
title: "Quick Plex question"
date: 2017-01-12
forum: Multimedia Software
---

### Post by frank2222 on 2017-01-12
Could someone please help me out here.

I've got flex installed on ubuntu just fine but I don't want it to start at startup.

I typ 

sudo service plexmediaserver start

or

service plexmediaserver stop and it works just fine, but if i enter

service plexmediaserver disable I get...

plexmediaserver: unrecognized service

Can anyone explain this or atleast tell me how to keep plex from starting at startup.

Thanx in advance.

---

### Post by curticegough on 2017-01-12
Try searching for **Startup Applications** in the dash.  If plexmediaserver starts automatically on startup, it should be in there.  Disable it.  That should make it stop auto-starting.:)

---

### Post by ajgreeny on 2017-01-12
We also probably need to know which version of Ubuntu you have as the change from upstart to systemd may make a difference to what is needed.

However if you are using 16.04 look for the file /etc/init/plexmediaserver.conf, which is where mine is, and edit the line **start on filesystem and net-device-up IFACE!=lo** shown below in red, by adding a # at the start to comment it out and it will not then be executed at startup of the filesystem.
You will have to do this as root, of course.

That should stop it from starting as you boot the system but you should still be able to start and stop it after that with the **sudo service plexmediaserver start/stop command** which I have as aliases of **plex+** and **plex-**.

```
# plexpms - service job file

description "Plex Media Server"
author "https://plex.tv/"

# Start the media server after network and filesystem
# Otherwise this lead to a unresponsive server
[COLOR="#FF0000"]# start on filesystem and net-device-up IFACE!=lo
[/COLOR]
# When to stop the service
stop on runlevel [016]

# Automatically restart process if crashed
respawn

# What to execute
script
    if [ -r /etc/default/plexmediaserver ]; then
        . /etc/default/plexmediaserver
    fi 
    start-stop-daemon --start -c $PLEX_MEDIA_SERVER_USER --exec /usr/sbin/start_pms
end script
```

---

### Post by frank2222 on 2017-01-15
Thanx so much for taking the time to reply. It's appreciated

---

