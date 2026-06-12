---
title: "mythexport intermittent failure..."
date: 2012-12-09
forum: Mythbuntu
---

### Post by RideMan on 2012-12-09
Greetings!

I am still running 0.24 (I think...whatever the -fixes version was just before the recent update...) and suddenly I am having problems with MythExport.

Every so often...and so far I can't figure out what triggers it...my export jobs all get stalled in the queue, thus preventing any other jobs from running.  Generally the jobs have already died, but they are still stuck in the queue until I delete the mythexport.### files from the export directory.

What I am finding in the MythExport log seems to explain what went wrong:

```

December  8 12:58:36 Farnsworth /usr/bin/mythexport-daemon[1042]: Starting Processing:  1354989516
December  8 12:58:37 Farnsworth /usr/bin/mythexport-daemon[1042]: Can't connect to MythTV: Couldn't communicate with 192.168.2.21 on port 6543:  IO::Socket::INET::MythTV: connect: Connection refused
 at line 88 in /usr/bin/mythexport-daemon
December  8 12:58:42 Farnsworth /usr/bin/mythexport-daemon[1042]: Can't connect to MythTV: Couldn't communicate with 192.168.2.21 on port 6543:  IO::Socket::INET::MythTV: connect: Connection refused
 at line 88 in /usr/bin/mythexport-daemon
December  8 12:58:47 Farnsworth /usr/bin/mythexport-daemon[1042]: Can't connect to MythTV: Couldn't communicate with 192.168.2.21 on port 6543:  IO::Socket::INET::MythTV: connect: Connection refused
 at line 88 in /usr/bin/mythexport-daemon
December  8 12:58:52 Farnsworth /usr/bin/mythexport-daemon[1042]: Can't connect to MythTV: Couldn't communicate with 192.168.2.21 on port 6543:  IO::Socket::INET::MythTV: connect: Connection refused
 at line 88 in /usr/bin/mythexport-daemon
Couldn't connect to MythTV. at /usr/bin/mythexport-daemon line 94.

```

(Farnsworth = localhost = MythTV box, running combined frontend/backend; mythexport is running on this box, box has a static IP address of 192.168.2.21, and at the time of the failure, everything else seems to be working. Box has a good network connection, and the IP address is static anyway, so there is no DHCP server issue here.)

Most of the time this seems to work. Sometimes it does not.  I'm looking for any advice this community might be able to supply--

a) Why am I getting "connection refused" errors...what would cause the database to refuse a connection to the mythexport process?

b) When this happens, the export process dies. When that happens, shouldn't the script be smart enough to automagically delete the lock file, thus purging the failed job so that MythTV can go on and do something else? Any suggestions as to where I should add an instruction to the script to do just that?

I'm afraid I don't know enough about Linux or Perl to understand what is happening here. But if someone knows why I might be getting these refused connections, maybe I can figure out how to fix it. Could it be as simple as the database not allowing enough simultaneous connections; perhaps mythfilldatabase is running at the exact moment that mythexport is doing a query or something? Any ideas?

Thanks!

--Dave Althoff, Jr.

---

