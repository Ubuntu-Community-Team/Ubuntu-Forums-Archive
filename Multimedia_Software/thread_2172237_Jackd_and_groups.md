---
title: "Jackd and groups"
date: 2013-09-03
forum: Multimedia Software
---

### Post by as-erwin on 2013-09-03
Jackd (via Qjackctl) worked one minute and then didn't the next.
I had some issues with some groups, and now a group is missing (though I have no idea what the group was, only its GID)
This is the message I get when I start jackd ... Not sure if it helps.

 [COLOR=#ff0000]20:06:59.243 D-BUS: JACK server could not be started. Sorry[/COLOR]
 Cannot read socket fd = 18 err = Success
 CheckRes error
 JackSocketClientChannel read fail
 Cannot open qjackctl client
 Tue Sep  3 20:06:59 2013: ERROR: JackPosixProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out
 Tue Sep  3 20:06:59 2013: ERROR: Driver is not running
 Tue Sep  3 20:06:59 2013: ERROR: Cannot create new client
 Tue Sep  3 20:06:59 2013: ERROR: Unknown request 4294967295
 Tue Sep  3 20:06:59 2013: ERROR: CheckSize error size = 0 Size() = 12
 Tue Sep  3 20:06:59 2013: ERROR: CheckRead error
 Tue Sep  3 20:06:59 2013: Starting jack server...
 Tue Sep  3 20:06:59 2013: ERROR: `default' server already active
 Tue Sep  3 20:06:59 2013: ERROR: Failed to open server
 [COLOR=#ff0000]20:07:06.275 Could not connect to JACK server as client. - Overall operation failed. - Server communication error. Please check the messages window for more info.[/COLOR]
 Tue Sep  3 20:07:00 2013: Saving settings to "/home/thedude/.config/jack/conf.xml" ...

 Cannot read socket fd = 18 err = Success
 CheckRes error

 JackSocketClientChannel read fail
 Cannot open qjackctl client
 Tue Sep  3 20:07:06 2013: ERROR: JackPosixProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out
 Tue Sep  3 20:07:06 2013: ERROR: Driver is not running
 Tue Sep  3 20:07:06 2013: ERROR: Cannot create new client
 Tue Sep  3 20:07:06 2013: ERROR: Unknown request 4294967295
 Tue Sep  3 20:07:06 2013: ERROR: CheckSize error size = 0 Size() = 12
 Tue Sep  3 20:07:06 2013: ERROR: CheckRead error

---

