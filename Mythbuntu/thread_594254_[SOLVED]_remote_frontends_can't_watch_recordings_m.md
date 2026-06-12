---
title: "[SOLVED] remote frontends can't watch recordings moved to new backend"
date: 2007-10-27
forum: Mythbuntu
---

### Post by the Goat on 2007-10-27
This is a weird problem.  I think it has to do with a change in the database maybe.  I built a new backend and installed mythbuntu 7.10 on it.  I copied all the recordings off my old backend to the new backend and backuped and restoried the correct parts of the database to move the recordings.  Now the old recordings play fine through the frontend on the new backend.  But on all my other frontends (over the network) the old recordings wont play (error message below).  The network frontends can play live TV and can play new recordings I make on the new backend.

All the old recordings show up on the network frontends' watch recordings screen.  But when I try to play them the screen flashes black for half a second and goes back to the watch recordings screen.  Here is the error message mythfrontend writes to the terminal:
```

2007-10-27 20:01:26.459 TV: Attempting to change from None to WatchingPreRecorded
2007-10-27 20:01:26.462 RemoteFile::openSocket(control socket): 
                        Could not connect to server "" @ port -1
2007-10-27 20:01:26.462 RemoteFile::openSocket(file data socket): 
                        Could not connect to server "" @ port -1
2007-10-27 20:01:26.462 RingBuffer::RingBuffer(): Failed to open remote file (myth://:/1051_20071026233500.mpg)
0: start_time: 2585.537 duration: 334.426
1: start_time: 2585.502 duration: 334.423


```

---

### Post by superm1 on 2007-10-28
> **the Goat said:**
> This is a weird problem.  I think it has to do with a change in the database maybe.  I built a new backend and installed mythbuntu 7.10 on it.  I copied all the recordings off my old backend to the new backend and backuped and restoried the correct parts of the database to move the recordings.  Now the old recordings play fine through the frontend on the new backend.  But on all my other frontends (over the network) the old recordings wont play (error message below).  The network frontends can play live TV and can play new recordings I make on the new backend.

All the old recordings show up on the network frontends' watch recordings screen.  But when I try to play them the screen flashes black for half a second and goes back to the watch recordings screen.  Here is the error message mythfrontend writes to the terminal:
```

2007-10-27 20:01:26.459 TV: Attempting to change from None to WatchingPreRecorded
2007-10-27 20:01:26.462 RemoteFile::openSocket(control socket): 
                        Could not connect to server "" @ port -1
2007-10-27 20:01:26.462 RemoteFile::openSocket(file data socket): 
                        Could not connect to server "" @ port -1
2007-10-27 20:01:26.462 RingBuffer::RingBuffer(): Failed to open remote file (myth://:/1051_20071026233500.mpg)
0: start_time: 2585.537 duration: 334.426
1: start_time: 2585.502 duration: 334.423


```
Looks to me like you are using a different hostname then you did on the old backend.  Is this correct?

---

### Post by the Goat on 2007-10-28
> **superm1 said:**
> Looks to me like you are using a different hostname then you did on the old backend.  Is this correct?
Yup that is correct.

I figured out that the hostname was the problem a couple of hours ago.  I changed the hostname, dropped and rebuilt the database and I think all my problems are solved.

---

### Post by mrkite00 on 2007-10-28
I just made the same error (renaming my new backend).

For those who would do the same, you have some nice instructions on how to change the hostname and then change the database to reflect the changes:

[http://www.mythtv.org/docs/mythtv-HOWTO-23.html]("http://www.mythtv.org/docs/mythtv-HOWTO-23.html")

Look for section "23.15 Changing your hostname".

---

