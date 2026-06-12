---
title: "Can't install Plex Media Server on Ubuntu Server 16.04"
date: 2016-11-18
forum: Multimedia Software
---

### Post by joelstitch on 2016-11-18
I have a fresh installation of Ubuntu Server 16.04 running on my server. I was able to install Plex Media Server at first and it was running fine but after uninstalling it and trying to reinstall it now I am facing some errors. This is what I get when I run **sudo apt get install plexmediaserver**

```
sudo apt install plexmediaserver
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  plexmediaserver
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/101 MB of archives.
After this operation, 220 MB of additional disk space will be used.
Selecting previously unselected package plexmediaserver.
(Reading database ... 167202 files and directories currently installed.)
Preparing to unpack .../plexmediaserver_1.2.7.2987-1bef33a_amd64.deb ...
Unpacking plexmediaserver (1.2.7.2987-1bef33a) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for systemd (229-4ubuntu12) ...
Processing triggers for ureadahead (0.100.0-19) ...
Setting up plexmediaserver (1.2.7.2987-1bef33a) ...
OK
Created symlink from /etc/systemd/system/multi-user.target.wants/plexmediaserver.service to /etc/systemd/system/plexmediaserver.service.
Job for plexmediaserver.service failed because the control process exited with error code. See "systemctl status plexmediaserver.service" and "journalctl -xe" for details.
dpkg: error processing package plexmediaserver (--configure):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for ureadahead (0.100.0-19) ...
Errors were encountered while processing:
 plexmediaserver
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I've tried many suggestions found online but none has gotten rid of the problem. I am at a point that I just want to install an alternative because I am giving up on this because its frustrating me so much, I have spent so many hours just trying to figure this out.

---

### Post by TheFu on 2016-11-18
I can confirm that plex runs great on 14.04.5 using the .deb package file from the source guys.  Support for 14.04 is good for a few years and with something like plex, I really don't want something too new. Stable, working, rock solid, supported is important for the "WAF."  Nothing is more important than [WAF]("https://en.wikipedia.org/wiki/Wife_acceptance_factor"), as you know.

My plex is a pure server. No desktop. It only provides access to media for other devices. Mainly a Raspberry-Pi v2, but occasionally laptops, Android, Roku and Chromecast devices.

Plus with a little ssh magic, no need to get a plex account for remote access to your media.
```
$ ssh -f -L 32400:plex:32400 gateway.example.com -NT
```
where gateway is the public IP (or dns) for your WAN and "plex" is the internal name for the plex system.  Basically, this tunnel provides access to the plex webapp inside.  Audio streaming works as is. For video, just adjust the bitrate for the current connection capabilities.

Anyway, sorry I can't help with 16.04. Maybe next year?  The changes to support systemd take some time to catch up, I suppose.

---

### Post by edjski1 on 2016-12-11
> **joelstitch said:**
> I have a fresh installation of Ubuntu Server 16.04 running on my server. I was able to install Plex Media Server at first and it was running fine but after uninstalling it and trying to reinstall it now I am facing some errors. This is what I get when I run **sudo apt get install plexmediaserver**

```
sudo apt install plexmediaserver
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  plexmediaserver
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/101 MB of archives.
After this operation, 220 MB of additional disk space will be used.
Selecting previously unselected package plexmediaserver.
(Reading database ... 167202 files and directories currently installed.)
Preparing to unpack .../plexmediaserver_1.2.7.2987-1bef33a_amd64.deb ...
Unpacking plexmediaserver (1.2.7.2987-1bef33a) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for systemd (229-4ubuntu12) ...
Processing triggers for ureadahead (0.100.0-19) ...
Setting up plexmediaserver (1.2.7.2987-1bef33a) ...
OK
Created symlink from /etc/systemd/system/multi-user.target.wants/plexmediaserver.service to /etc/systemd/system/plexmediaserver.service.
Job for plexmediaserver.service failed because the control process exited with error code. See "systemctl status plexmediaserver.service" and "journalctl -xe" for details.
dpkg: error processing package plexmediaserver (--configure):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for ureadahead (0.100.0-19) ...
Errors were encountered while processing:
 plexmediaserver
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I've tried many suggestions found online but none has gotten rid of the problem. I am at a point that I just want to install an alternative because I am giving up on this because its frustrating me so much, I have spent so many hours just trying to figure this out.
having the exact same issue (same error msg) with plex -very frustrating.

---

