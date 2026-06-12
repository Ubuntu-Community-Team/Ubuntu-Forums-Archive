---
title: "Mythtv?"
date: 2013-03-31
forum: Mythbuntu
---

### Post by tmccaffery on 2013-03-31
I intalled mythbuntu and Unable to connect to the master backend at 192.168.1.3:6543. Is it running?

[FONT=Arial]I checked netstat and it's not listening on port

when i try to start it, I get this:

[/FONT]service mythtv-backend start
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.99" (uid=1000 pid=5708 comm="start mythtv-backend ") interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply="0" destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init")

---

### Post by tgm4883 on 2013-03-31
You don't have priviledges to restart services. You need to use sudo.

'sudo service mythtv-backend start'

But there is virtually no information in this post. Did you install the Master Backend when you installed Mythbuntu? Did you run mythtv-setup? Did you tell mythtv-setup the correct IP address (192.168.1.3 instead of 127.0.0.1)? Did you enable the mysql service (or is it the mythtv service?) in the Mythbuntu Control Centre? Does the Backend think it is currently running (sudo service mythtv-backend status)? Do the backend logs say anything special (/var/log/mythtv/mythtv-backend.log)?

---

