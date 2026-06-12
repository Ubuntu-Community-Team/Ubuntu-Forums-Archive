---
title: "Run mythcommflag on a remote machine?"
date: 2008-10-02
forum: Mythbuntu
---

### Post by ttabbal on 2008-10-02
I'm running Mythbuntu 8.04. It's working great, except that mythcommflag is causing playback problems. I would like to offload that job to my file server running Ubuntu 8.04. I know it's possible, I'm just not sure where to start. I don't normally keep a monitor/KB attached to that box, so if it can be done via CLI that would be prefered. But I can probably get X working remotely if needed. 

I thought about installing the mythbackend package, but I've read that running a slave backend without tuners is a bad idea. There doesn't seem to be a lot of info on this sort of setup, so any info would be great. Right now, I just set Mythbuntu to only run mythcommflag at night when I'm unlikely to be using the machine for playback. 

The boxes are connected with gigabit ethernet, and already have NFS working between them, so adding new exports is easy.

---

### Post by newlinux on 2008-10-02
I do close to what you are talking about. You do want to install a slave backend, and then you can configure it run jobs (whenever you want, and however many concurrently). You'll want to make sure you've disabled the run jobs on recording host only in the backend (so commflag jobs can be run remotely).

You can install slave backends without tuners with no problem. I have 2 of them. In fact, my primary backend doesn't have any tuners. You'll need to connect the slave to your primary backend in mythtv-setup (from your slave backend). You should be able to run that via ssh X forwarding without an actual X desktop on your fileserver.

---

### Post by newlinux on 2008-10-02
you might get a warning in the logs about not having any tuners, but you can ignore it...

---

### Post by ttabbal on 2008-10-02
Thanks. I'll start looking into that. Good to know about needing mythtv-setup. I wasn't sure about that.

---

### Post by ttabbal on 2008-10-02
It's running and connecting to the master backend. Do I need to NFS mount the recordings directory for mythcommflag to find the recordings or does it use the Myth protocol to do that? 

For those that may search and find this: Don't forget to use mythbuntu-control-centre to enable remote access to the MySQL database. Took me a minute to figure out why I couldn't connect from the other machine.

---

### Post by newlinux on 2008-10-02
Yep, it should use myths protocol so you shouldn't need to mount anything for recordings.

sorry I didn't mention the remote access point, but glad you found it.

---

### Post by ttabbal on 2008-10-02
It seems to be working. I set up a test recording and the file server picked it up and started flagging it. I got this database error from the slave backend log.

```
2008-10-02 15:09:57.843 DB Error (SetInUse):
Query was:
INSERT INTO inuseprograms  (chanid, starttime, recusage, hostname, lastupdatetime,  rechost, recdir )  VALUES  ('1021', '2008-10-02T15:09:00', 'flagger', 'nas', '2008-10-02T15:09:57',  'mythtv', NULL);
Driver error was [2/1048]:
QMYSQL3: Unable to execute query
Database error was:
Column 'recdir' cannot be null
```

---

### Post by newlinux on 2008-10-02
just checked my slave backend logs and get that error too. might come from not setting the storage group up right on the slave backend or something (but it has no tuners so I shouldn't need too) but the commflagging jobs still run fine.

---

