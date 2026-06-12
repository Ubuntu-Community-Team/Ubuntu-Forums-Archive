---
title: "Live tv does not work but scheduled recording does"
date: 2007-11-12
forum: Mythbuntu
---

### Post by davidtinker on 2007-11-12
Hi All

My Mythtv box (P4 with Haupauge 500 + NVidia card, Ubuntu 7.10) was working well until a couple of days ago. Now I cannot watch live TV. The screen goes black for a few seconds and then returns to the menu. Scheduled recordings are still working and I can watch recorded stuff. So it would seem that all the hardware is in order.

Log file entries:

root@music:~$ tail -f /var/log/mythtv/mythfrontend.log

2007-11-12 20:28:20.011 New DB connection, total: 2
2007-11-12 20:28:20.012 Connected to database 'mythconverg' at host: localhost
2007-11-12 20:28:20.092 Connecting to backend server:
192.168.1.101:6543 (try 1 of 5)
2007-11-12 20:28:20.094 Using protocol version 31
2007-11-12 20:28:20.289 TV: Attempting to change from None to WatchingLiveTV
2007-11-12 20:28:20.290 Using protocol version 31
2007-11-12 20:28:27.304 MythSocket(8385658:21): readStringList: Error,
timeout (quick).
2007-11-12 20:28:27.304 RemoteEncoder::SendReceiveStringList(): No response.
2007-11-12 20:28:27.305 GetEntryAt(-1) failed.
2007-11-12 20:28:27.320 EntryToProgram(0@Thu Jan 1 02:00:00 1970) failed to get pginfo
2007-11-12 20:28:27.320 TV Error: LiveTV not successfully started
2007-11-12 20:28:27.320 TV Error: LiveTV not successfully started
2007-11-12 20:28:27.326 TV: Deleting TV Chain in destructor
2007-11-12 20:28:27.330 DPMS Deactivated
2007-11-12 20:28:27.331 DPMS Reactivated.

root@music:~# tail -f /var/log/mythtv/mythbackend.log

2007-11-12 20:28:20.094 MainServer::HandleAnnounce Monitor
2007-11-12 20:28:20.153 adding: music as a client (events: 0)
2007-11-12 20:28:20.154 MainServer::HandleAnnounce Monitor
2007-11-12 20:28:20.155 adding: music as a client (events: 1)
2007-11-12 20:28:20.290 MainServer::HandleAnnounce Playback
2007-11-12 20:28:20.299 adding: music as a client (events: 0)
2007-11-12 20:28:20.427 TVRec(1): Changing from None to WatchingLiveTV
2007-11-12 20:28:20.503 TVRec(1): HW Tuner: 1->1
2007-11-12 20:28:21.538 ret_pid(0) child(8191) status(0x0)
2007-11-12 20:28:22.543 ret_pid(0) child(8191) status(0x0)
2007-11-12 20:28:23.550 ret_pid(0) child(8191) status(0x0)
2007-11-12 20:28:24.558 ret_pid(0) child(8191) status(0x0)
2007-11-12 20:28:25.566 ret_pid(0) child(8191) status(0x0)
2007-11-12 20:28:26.572 ret_pid(0) child(8191) status(0x0)
2007-11-12 20:28:27.580 ret_pid(0) child(8191) status(0x0)
2007-11-12 20:28:28.588 ret_pid(8191) child(8191) status(0x0)
2007-11-12 20:28:28.595 External Tuning program exited with no error
2007-11-12 20:28:29.690 TVRec(1): Changing from WatchingLiveTV to None
2007-11-12 20:28:30.561 Finished recording Justice: channel 1106
2007-11-12 20:28:30.575 MythSocket(81855b8:-1): writeStringList: Error, socket went unconnected.

Any ideas?

Thanks
David

---

### Post by sica on 2007-11-12
That used to happen to me. I had since re-installed so I never figured it out. 

My guess was that it was working, but upon reboot. I automatically logged in and that user did not have proper access to the video capture card.

---

### Post by 7bigjohn on 2007-11-14
The same thing happened to me.  I have two PVR150's and the problem only seems to happen when one ot the cards is recording.  It's like it's not taking advantage of the second card.  I know both cards configured correctly and are working because they worked just fine with other distro's.

---

### Post by superm1 on 2007-11-14
Can we perhaps see if dmesg lists any justice about what the cards are doing at this time?

---

### Post by davidtinker on 2007-11-15
I have the problem even when my box is not recording anything. I will try to do some more poking around on the weekend, maybe look at the Mythtv source to try to see what it is up to. Or maybe try rename its database and see if a fresh db solves it .. if so maybe its something in the db that can be manually fixed.

---

### Post by warp99 on 2007-11-17
I think that your database may be locked. Scan you mythbackend.log for lock errors. If you find something like this:

**Table './mythconverg/<name of record>' is marked as crashed and should be repaired**

Then this is the problem. You need to repair the database with the following command:

**mysqlcheck -u mythtv -p  --repair mythconverg <name of record>**

Remember to get your password from Utilities/Setup > Setup > General under the frontend menu before you repair the database. :)

---

### Post by jemmrich on 2007-12-14
> **warp99 said:**
> I think that your database may be locked. Scan you mythbackend.log for lock errors. If you find something like this:

**Table './mythconverg/<name of record>' is marked as crashed and should be repaired**

Then this is the problem. You need to repair the database with the following command:

**mysqlcheck -u mythtv -p  --repair mythconverg <name of record>**

Remember to get your password from Utilities/Setup > Setup > General under the frontend menu before you repair the database. :)

Thanks for this little tidbit.. it had me stumped! :guitar:

---

### Post by davidtinker on 2007-12-25
I finally had some time to figure this out. I created a new mythconverg database and that did not help. It turns out that my channel changing script was taking too long to execute. I shortened some of the sleeps to solve the problem.

I did not consider that as a source of the problem before as scheduled recordings were working perfectly.

Thanks for the help everyone.

---

