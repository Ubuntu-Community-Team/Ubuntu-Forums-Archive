---
title: "Script which checks if user is connected via VNC. HOW?"
date: 2010-05-04
forum: Networking &amp; Wireless
---

### Post by produnis on 2010-05-04
Hi folks,

my Lucid-PC runs x11vnc (port 5900)
I would like to check with a script,
if a user is currently connected to my Lucid-PC via VNC...

How could this be done?

Thx in advance..

---

### Post by iponeverything on 2010-05-04
VNC logs the connection. Just adapt a existing log watcher script or create your own.

---

### Post by produnis on 2010-05-04
thx for your answer,

unfortunately, I am too stupid to read from x11vnc.log if a user is currently connected. The logfile (I started x11vnc with -o Option) prints out something every 2 seconds... And all the messages make absolutely no sense to me...
:(

---

### Post by produnis on 2010-05-04
maybe there is a way to somehow check whether port 5900 (this is my vnc port) is "in use" ?

---

### Post by krunge on 2010-05-04
Once your x11vnc is running as a server you can query it by running it again like this to query the currently connected clients:
```
x11vnc -Q clients
```
You need to do this in the same environment that x11vnc is running (e.g. same $DISPLAY, etc.)
The output looks something like this:
```

# x11vnc -Q clients
>>> sending remote command: "qry=clients" via X11VNC_REMOTE X property.
aro=clients:0x1:127.0.0.1:58666:runge:none:localhost:KMBCF:0:1272995388

```
It is cryptic, but the part after the "clients:" should be comma separated list for each connected client.

To get a history of clients that have connected you will need to scrape the x11vnc log output.

---

### Post by produnis on 2010-05-04
Thank you very much.
Additionally, I found that 
```
netstat -anp |grep 5900
```works, too


A little script could look like this:

> 
#!/bin/bash
VNC_CONNECT=$(netstat -anp |grep -i 5900 | wc -l)
if [ $VNC_CONNECT -ge 3 ]; then
   echo "Client is connect"
else
   echo "No Client connected"
fi


---

