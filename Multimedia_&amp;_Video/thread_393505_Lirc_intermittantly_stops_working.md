---
title: "Lirc intermittantly stops working"
date: 2007-03-25
forum: Multimedia &amp; Video
---

### Post by ebike on 2007-03-25
Hi All,

For a year now I have been having trouble with the remote-control for my Mythtv box (a StreamZap device), specifically the lirc daemon.

Every now and then (once or twice a day) the remote will stop working. On investigation, I see that the lirc daemon has gone and I have to do a /etc/init.d/lirc restart to get it back. I also have to restart irxevent.

I have no idea why lirc is dying, there is nothing in the logs to give any clues.

Idealy I would like to know what is going on, but if someone could come up with a workaround script that periodically checks for lirc, and if it is missing re-starts it and irxevent, I would be very grateful. 

Thanks.

---

### Post by ebike on 2007-03-27
Bump

---

### Post by the.unclean.cpp on 2007-03-27
You're a lucky guy :D
I can't figure out lirc at all....the lircd.conf is ok, my tv tuner is suported and my remote control also....I can't figure out what's wrong....
The irexec won't start though...it returns this message when I run it:
```
alex@Hackb0x:~$ irexec
irexec: could not connect to socket
irexec: Connection refused
alex@Hackb0x:~$ sudo irexec
irexec: could not connect to socket
irexec: Connection refused

```
Can you tell me how to configure my box to allow irexec to acces the proper socket?

---

### Post by ebike on 2007-03-29
Most likely an irxevent process is running allready.
Try --> sudo killall irxevent, and then run it again in the background --> irxevent &

Cheers,

---

### Post by the.unclean.cpp on 2007-03-29
Thanks for the help. Didn't work thought...I guess irexec was just one of the problems...I'm searching for more :)

---

### Post by superm1 on 2007-03-29
Well not connecting to socket likely means lircd isn't running. 


With regard to the streamzap error above - In the interim i'd say launch it non-daemon mode and watch why it dies.  Just start it via ssh or something.

---

