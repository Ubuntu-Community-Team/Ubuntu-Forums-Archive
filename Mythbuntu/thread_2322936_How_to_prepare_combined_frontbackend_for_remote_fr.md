---
title: "How to prepare combined front/backend for remote frontend?"
date: 2016-05-01
forum: Mythbuntu
---

### Post by JamesNorris on 2016-05-01
I've been running MythTV as a combined front/backend for almost ten years, but now I have a RPi2 and an Android tablet which I would like to run frontends on. I have the tablet ready to go already. 

I have configured my router so the backend machine now has a static network address, but when I set mysql to accept network connections from within MCC with 0000 as the key on the backend. Unfortunately, doing this somehow stops me from being able to connect the frontend to the backend on the local machine and the remote frontend also does not work. 

Any ideas what I'm doing wrong?

---

### Post by aelfric55 on 2016-05-02
Start by checking your mythbackend log, then your frontend log.

From the ground up, the problem could be 1) the mysql server isn't running. 2) The mysql server is running, but is running while looking only at localhost (a.k.a. 127.0.0.1) for connections, and not on the IP address. 3) Mysql is running, and on the ip address, but is not configured to accept login credentials from tcpip via the ip address and will only accept a login via localhost. 4) Mysql server is in general correctly configured and is running while looking for ip address connections, but mythtv-setup has not been reconfigured from localhost to the backend ip address and is still searching for the database on localhost. 5) Mysql and the backend are correctly configured and the backend is running on the backend ip address, but the frontend has not been correctly configured to connect to the database on the backend ip address, and is still looking for it on localhost.

Looking at the logs should indicate whereabouts the daisy chain seems to be breaking down, and will give you a better idea where to attack the problem.

---

