---
title: "Myth backend firing external tuner channel change command once a minute"
date: 2010-03-24
forum: Mythbuntu
---

### Post by seifertd on 2010-03-24
I am experiencing a bizarre problem that just surfaced today.  I have myth 0.22 on a mythbuntu box running karmic:

Linux myth 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux

Once per minute, I am getting the following output in the mythbackend.log:

2010-03-23 23:02:31.231 mythbackend version: branches/release-0-22-fixes [22594] [www.mythtv.org](www.mythtv.org)
2010-03-23 23:02:31.234 Using runtime prefix = /usr
2010-03-23 23:02:31.235 Using configuration directory = /home/mythtv/.mythtv
2010-03-23 23:02:31.236 Empty LocalHostName.
2010-03-23 23:02:31.237 Using localhost value of myth
2010-03-23 23:02:31.245 New DB connection, total: 1
2010-03-23 23:02:31.249 Connected to database 'mythconverg' at host: localhost
2010-03-23 23:02:31.251 Closing DB connection named 'DBManager0'
2010-03-23 23:02:31.253 Connected to database 'mythconverg' at host: localhost
2010-03-23 23:02:31.256 Current MythTV Schema Version (DBSchemaVer): 1244
2010-03-23 23:02:31.258 MythBackend: Starting up as the master server.
2010-03-23 23:02:31.264 New DB connection, total: 2
2010-03-23 23:02:31.266 Connected to database 'mythconverg' at host: localhost
2010-03-23 23:02:31.270 New DB connection, total: 3
2010-03-23 23:02:31.272 Connected to database 'mythconverg' at host: localhost
2010-03-23 23:02:31.321 ret_pid(7043) child(7043) status(0x0)
2010-03-23 23:02:31.323 External Tuning program exited with no error
2010-03-23 23:02:31.334 New DB scheduler connection
2010-03-23 23:02:31.336 Connected to database 'mythconverg' at host: localhost
2010-03-23 23:02:31.348 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2010-03-23 23:02:31.349 Main::Registering HttpStatus Extension
2010-03-23 23:02:31.350 Enabled verbose msgs:  important general
2010-03-23 23:02:31.353 AutoExpire: CalcParams(): Max required Free Space: 5.0 GB w/freq: 15 min
2010-03-23 23:02:34.343 Reschedule requested for id -1.
2010-03-23 23:02:34.529 Scheduled 97 items in 0.2 = 0.01 match + 0.17 place
2010-03-23 23:02:34.533 Seem to be woken up by USER

The external tuner program (6200ch) is invoked each minute (as you can see by the log lines above.  The problem with this is that it interferes with watching live TV -- the channel is constantly changed to the last tuned channel.  If switch the input on my TV to watch the cable outside of myth (I split the cable signal coming out of the cable box directly into my TV and into the myth box), myth is still chugging along setting the channel to what it thinks it should be.  If I use the remote to change to another channel, 1 minute later, myth will change it back via the firewire connection to what it thinks it should be.

This is making using my cable or myth to watch TV impossible.  I have had to disconnect the firewire cable in order to watch TV.  If I forget to plug it back in, I will miss recordings.

Can anybody please help be diagnose what is going on with my setup?

Thanks in advance,
Doug Seifert

---

### Post by ian dobson on 2010-03-24
Hi,

Could it be that you have EIT enabled for the video source? This might cause mythtv to tune to one channel after the other trying to grab EPG/EIT information from it.

Regards
Ian Dobson

---

### Post by seifertd on 2010-03-24
I don't have EIT enabled.  At any rate, it wants to tune to the same channel every time.  If I go into the TV guide and choose channel 7 for example, then exit out of myth TV, if I switch inputs on my TV so that I am getting a direct cable feed, once per minute I get switched back to channel 7.

---

### Post by seifertd on 2010-03-24
It has something to do with upstart.  I think the upstart system is restarting the mythtv backend once a minute.  The PID of the mythbackend process is changing constantly.  I will debug and report back if I find and fix anything in case anybody runs into this themselves in the future.

---

### Post by ian dobson on 2010-03-24
Hi,

I would have a look in the syslog (/var/log/syslog) to see why mythbackend is dieing all the time. upstart will restart a process that is controls if the process dies due to a seg fault.

Maybe try stopping mythbackend through upstart, then start mythbackend manually from the commandline prompt (as the correct user) to see why myth is going bottom up.

Regards
Ian Dobson

---

### Post by seifertd on 2010-03-24
Thanks for all the suggestions.

I had configured monit to watch the mythbackend before upgrading to the latest version of mythbuntu.  After upgrading to the latest version of mythbuntu which comes with upstart, the mythbackend process was not configured to write out the pid file to /var/run/mythtv/mythbackend.pid.  This was ok at first because after the upgrade, I never restarted monit (I guess I don't need monit with upstart, but that's not relevant here).  Anyway, yesterday, I started the monit service.  Monit was looking for that pid file for the mythbackend and not finding it, thinking the backend was dead, and restarting it once every monit cycle.


To get upstart owned mythbackend to play nice with monit, I did the following:

I added "--pidfile /var/run/mythtv/mythbackend.pid" to the ARGS variable definition in /etc/default/mythtv-backend and then added the following to the /etc/init/mythtv-backend upstart script:

pre-start script
  mkdir -p /var/run/mythtv
  chown mythtv:mythtv /var/run/mythtv
end script

to make sure the backend could create the pid file.  

Now all is well.  I guess I should have just killed monit.

Again, thanks for the suggestions.

---

