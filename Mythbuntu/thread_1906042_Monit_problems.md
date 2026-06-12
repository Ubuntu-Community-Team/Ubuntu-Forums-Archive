---
title: "Monit problems"
date: 2012-01-08
forum: Mythbuntu
---

### Post by timbim on 2012-01-08
Hi all,

Getting towards the end of configuring my myth backend, I'm trying to set up monitoring using monit according to the [wiki guide]("http://www.mythtv.org/wiki/StatusMonitoringHowTo#Installation").

I can get monit to run and start its webserver correctly, but when I try to start monitoring mythbackend, I get stuck at initializing for mythbackend and Execution failed for mysql on the web interface.  I'm using exactly the config from the howto for these two monitoring processes, started manually by me with both services working fully.

Looking at /var/run, there isn't a directory mythtv, and I can't find mythbackend.pid anywhere.  There is a directory called mysqld, but it only contains mysqld.sock.  I'm thinking this might be the cause of the problem?

I'm running Ubuntu 11.04 with everything installed from standard repos in the past couple of days.

Any ideas what's going wrong here and what I can do to solve it?

Tim

---

### Post by newlinux on 2012-01-10
I forgot what version it happened, but since ubuntu moved to using upstart it no long writes a PID file for mythbackend. Do you need monit with upstart for mysql and mythbackend? If so, for mythbackend you'll want to do something like modify the /etc/init/mythtv-backend.conf upstart configuration to write a PID file and give the PID file proper permissions.

---

