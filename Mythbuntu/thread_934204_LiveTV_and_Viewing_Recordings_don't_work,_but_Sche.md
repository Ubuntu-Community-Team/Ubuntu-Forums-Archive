---
title: "LiveTV and Viewing Recordings don't work, but Scheduled recordings actually record"
date: 2008-09-30
forum: Mythbuntu
---

### Post by coastalbendnetworks on 2008-09-30
For about a week, my system has worked perfectly fine. I have a backend only machine and a frontend only machine. Two nights ago, I decided to add a second frontend only machine and share some of it's hdd space through NFS and add it to the Storage Groups.

Everything worked fine that night. Yesterday, I could no longer connect to the backend from the frontends, but there were no errors in the Backend logs, just the frontend logs saying that ti could not connect to the backend, and nothing had changed. After several reboots of everything, I can connect to the backend again. Now, I can no longer view LiveTV or recordings, but I have verified that the backend is still recording scheduled recordings. I have verified that the files also work through VLC.

Here is the error from the log file on one of the frontends:

```
2008-09-30 08:46:21.281 RemoteFile::openSocket(file data socket): Did not get proper responce from /1024_20080930083000.mpg:192.168.25.9
2008-09-30 08:46:21.281 RingBuffer::RingBuffer(): Failed to open remote file (myth://192.168.25.9:6543/1024_20080930083000.mpg)
2008-09-30 08:46:21.288 PlaybackBox Error: Could not open file for preview video.
2008-09-30 08:46:28.813 MythSocket(82aa448:31): readStringList: Error, timeout (quick).
QString::arg(): Argument missing: RemoteFile::openSocket(file data socket): Did not get proper responce from /1024_20080930080000.mpg:192.168.25.9, 6543
2008-09-30 08:46:28.813 RemoteFile::openSocket(file data socket): Did not get proper responce from /1024_20080930080000.mpg:192.168.25.9
2008-09-30 08:46:28.813 RingBuffer::RingBuffer(): Failed to open remote file (myth://192.168.25.9:6543/1024_20080930080000.mpg)
2008-09-30 08:46:28.820 PlaybackBox Error: Could not open file for preview video.
Destroying SipFsm object 
2008-09-30 08:50:12.729 Deleting UPnP client...

```

This is the relevant messages from the backend logs:
```

2008-09-30 08:46:14.279 MainServer::HandleAnnounce Playback
2008-09-30 08:46:14.281 adding: Master as a client (events: 0)
2008-09-30 08:46:14.282 Bad ANN query
2008-09-30 08:46:21.282 Unknown socket closing
2008-09-30 08:46:21.286 Unknown file transfer socket: 0
2008-09-30 08:46:21.807 MainServer::HandleAnnounce Playback
2008-09-30 08:46:21.808 adding: Master as a client (events: 0)
2008-09-30 08:46:21.810 Bad ANN query
2008-09-30 08:46:28.814 Unknown socket closing
2008-09-30 08:46:28.817 Unknown file transfer socket: 0

```

I have two PVR 150's & 1 WinTV Go in this system. They are all detected and functional. I have also verified that the file in question in the frontend logs does exist and does work in VLC.

I don't know what else to do at this point. I have searched google, these forums and the mythtv lists but either searched for the wrong thing or no one else has encountered exactly this problem.

Let me know what other information is needed.

Also, I am running the current MythTV from the Mythbuntu fixes repo. All machines in question are fully updated. Like I said earlier, they all worked perfectly fine up until sometime yesterday while I was at work.

---

### Post by coastalbendnetworks on 2008-10-04
For future reference, since I see so many problems that don't get the resolution posted, I have finally figured this one out, though it doesn't make sense to me.

I reinstalled everything and I was still having the same issue. For whatever reason, the option to ping the backend when you configure the frontend was causing this problem. Once I unchecked that option, everything worked fine. I verified from a command line that I could, indeed, ping the backend from the frontend in question.

Anyway, thankfully it is finally resolved.

---

