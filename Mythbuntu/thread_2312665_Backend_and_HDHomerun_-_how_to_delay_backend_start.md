---
title: "Backend and HDHomerun - how to delay backend start"
date: 2016-02-06
forum: Mythbuntu
---

### Post by nmw01223 on 2016-02-06
I am using 14.04 LTS, 0.27.5, all up to date.

I have been trying to get an HDHomerun Connect tuner to work. For various reasons (practical and logistical) the HDHR is not connected via my router, but is connected peer to peer on Eth0, with Eth0 set to link local.

This all works, but unfortunately it takes 10-15 seconds to be allocated an IP address. By that time the backend has already started, failed to find the HDHR and that is that. The only way to get the backend to recognise it is to do a backend restart, but that, of course does not work in an unattended situation when the m/c restarts from a shutdown waiting for a record time.

So, I found the Upstart job that starts the backend (mythbackend-start.conf, I think it was called) and in the 'script ... end script' stanza added a delay before the backend was started.

That worked as well, the backend now found the HDHR, but there was a consequence - the m/c will not shutdown properly. When the m/c shuts down it sits for ~5 miinutes at 'wait-for-state stop/waiting', then eventually shuts down. Something gets stuck - but I am not experienced enough with the log files to see what. However, it is completely caused by the change to the Upstart job, take that out again, no problem.

I also notice that it affects going into backend setup: it asks to shutdown the backend in the usual way, but then often the setup doesn't start and you have to do it again, and when you get in to the setup it says the backend is still running. All this is caused by the Upstart job change.

The delay in the backend start script can be as simple as 'sleep 20'.

So, what I would like to know is:
 1. Why does the change to the Upstart job cause this, and
2. If that is not the right way to delay the backend start, what is?

---

### Post by khPWXxF on 2016-02-06
I suspect that it is started with this:

> /etc/init/mythtv-backend.conf

Not sure whether you can just put a sleep 10 in there.
Phil

---

### Post by nmw01223 on 2016-02-13
You are right, that was the file I meant - got the name wrong from memory.

Unfortunately putting 'sleep 20' in there is what causes the problem, though I do not see why.

---

### Post by nmw01223 on 2016-02-21
For use of anyone with a similar problem:

Cause is down to how Upstart works, it tracks the process id of any daemon in case it has to stop it again. If you put a script command in the script ... end script secton, UpStart may pick the wrong one. Whilst one can manage this with care, safest is to put any commands to detect an HDHR into the pre-start script ... end script section, then Upstart is not at risk of getting confused.

The final approach was to add a script which runs a loop into the pre-start section, using hdhomerun_config discover, which returns 1 on no HDHR, 0 if it finds one. On finding one (or on a timeout of ~40 seconds) it stops anyway and the back end can then start.

---

