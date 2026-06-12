---
title: "Restart after apt-get-update"
date: 2014-05-23
forum: Mythbuntu
---

### Post by red321 on 2014-05-23
Sure this is an easy one.

Recently updated to 14.04. I am running th emythbuntu myth packages on Ubuntu 14.04 desktop. Whenever I apt-get update mythtv-backend, it stops mythbackend and installs but does not restart. 

sudo start mythv-backend works perfectly. I see no errors in any logs. I am sure it restarted on upgrade on 12.04.

So should a package upgrade gracfully restart mythtv-backend ?????

This may be a local problem, as I just tried :

```
john@mythtv:~$ start mythtv-backend
start: Unknown job: mythtv-backend
john@mythtv:~$ sudo start mythtv-backend
mythtv-backend start/running, process 15326
john@mythtv:~$ sudo stop mythtv-backend
mythtv-backend stop/waiting
john@mythtv:~$ su mythtv
Password: 
$ start mythtv-backend
start: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
$ sudo start mythtv-backend
mythtv-backend start/running, process 15398
$ exit
john@mythtv:~$ su
Password: 
root@mythtv:/home/john# start mythtv-backend
start: Unknown job: mythtv-backend
root@mythtv:/home/john# sudo start mythtv-backend
start: Job is already running: mythtv-backend
root@mythtv:/home/john# 

```

Why does root need "sudo" to start mythtv-backend ????? My installation is a continually updated one since 10.04 or so, so it could be a maze of links and confusion from SysVinit to Upstart to systemd . Any pointer appreciated.

---

### Post by blm-ubunet on 2014-05-23
Probably a good thing it does not restart the backend service..
You are meant to run mythtv-setup first after every update/install to allow dB schema updates the best chance of success.

Stopping & starting mythtv-backend service via upstart requires sudo on all installs I have done/debugged.
```
sudo service mythtv-backend [stop|status|start]
```


It is possible that your upstart job configuration for backend is broken.
I think the "start mythtv-backend" & "stop MBE" fall-back to an old sysVinit script if the upstart job is missing.
But I seem to remember the BE sysVinit script was called mythbackend..
Check there is a link to upstart for mythtv-backend in /etc/init.d/..

i.e. this should exist:
```
ln -s /lib/init/upstart-job /etc/init.d/mythtv-backend
```

Documented here:
[http://www.mythtv.org/wiki/Upstart_mythbackend_Configuration](http://www.mythtv.org/wiki/Upstart_mythbackend_Configuration)

---

### Post by red321 on 2014-05-27
Thanks, your additional info was the bit that helped. ( I read it before you updated :-) ) 

Somehow ( probably user error !), the link to the upstart job had become overwritten. So although /etc/init.d/mythtv-backend existed, it was not a soft link to the upstart job. Explains why it was running manually but not via some scripts. Just need to wait for a package update to try out th e original issue.

---

