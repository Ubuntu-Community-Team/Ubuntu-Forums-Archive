---
title: "Public IP Address Check"
date: 2009-11-05
forum: Networking &amp; Wireless
---

### Post by JohnnySage50307 on 2009-11-05
So, I have converted my Ubuntu Desktop (v9.04 Jaunty) to a server which I access regularly to do research and host a website from.  To date, I have been registering my public IP address with DynDNS; however I am annoyed at the unpredictability that surrounds when my dynamic IP address changes.

I have tried to use **ifconfig** to determine what my public IP address is (I figured I could write a little script to check for changes using this), but it'll only return the IP of my server on my local network.

My question, how can one determine his own public IP address from terminal?

---

### Post by Barriehie on 2009-11-05
> **JohnnySage50307 said:**
> So, I have converted my Ubuntu Desktop (v9.04 Jaunty) to a server which I access regularly to do research and host a website from.  To date, I have been registering my public IP address with DynDNS; however I am annoyed at the unpredictability that surrounds when my dynamic IP address changes.

I have tried to use **ifconfig** to determine what my public IP address is (I figured I could write a little script to check for changes using this), but it'll only return the IP of my server on my local network.

My question, how can one determine his own public IP address from terminal?

I'm using dyndns and they've got a file, ddclient, that sends your IP to dyndns.  They've got a sample .conf file on the site, [here](https://www.dyndns.com/support/clients/#linux).  It's not difficult to setup.

Barrie

IP from terminal:  try sudo dhclient

---

### Post by Iowan on 2009-11-05
There's another thread around here that covers this topic.  I'll look around for it.

Found it:[http://ubuntuforums.org/showpost.php?p=8242196&postcount=3]("http://ubuntuforums.org/showpost.php?p=8242196&postcount=3")

---

### Post by falconindy on 2009-11-05
I wrote a bash script that runs as a nightly cron job.

```
#!/bin/bash

USERNAME=
PASSWORD=
HOSTNAME=
IP=`curl http://www.whatismyip.com/automation/n09230945.asp`

curl -v -k "http://${USERNAME}:${PASSWORD}@members.dyndns.org/nic/update?hostname=${HOSTNAME}&myip=$IP&wildcard=NOCHG&mx=NOCHG&backmx=NOCHG"
```
Fill in username, password and hostname, and drop it in a job via gnome-schedule.

---

### Post by liamria.z01 on 2009-11-05
I successfully use giplet. Just install it with the synaptic manager and put it to the panel. Edit preferences and replace the interface with [www.whatismyip.org]("http://www.whatismyip.org"). Manual check with a left click on the applet.

---

