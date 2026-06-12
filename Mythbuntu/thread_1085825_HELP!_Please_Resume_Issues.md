---
title: "HELP! Please Resume Issues"
date: 2009-03-03
forum: Mythbuntu
---

### Post by rodercot on 2009-03-03
Hey all,

 I have been working on this for a couple weeks. 

 I now have it so my pm-suspend log shows all resumes OK and no issues. But when I try to watch live tv after a resume from suspend I get this in the log

 ```
xbmc@mythbed:~$ tail -f /var/log/pm-suspend.log
2009-03-03 13:05:05.321 New DB connection, total: 3
2009-03-03 13:05:05.321 Connected to database 'mythconverg' at host: 192.168.1.132
2009-03-03 13:05:05.330 NVP::OpenFile(): Error, file not found: /var/lib/mythtv/recordings/1520_20090303130457.mpg
2009-03-03 13:05:05.330 TV Error: StartPlayer(): NVP is not playing after 20000 msec
2009-03-03 13:05:05.386 DPMS Deactivated
2009-03-03 13:05:12.335 MythSocket(9bc9868:32): readStringList: Error, timeout (quick).
2009-03-03 13:05:12.335 RemoteEncoder::SendReceiveStringList(): No response.
2009-03-03 13:05:12.337 TV Error: LiveTV not successfully started
2009-03-03 13:05:12.393 DPMS Reactivated.

```

 Now If I ssh issue a sudo reboot or reboot the machine normally all this goes away and live tv is Just fine. ON Resume when I get the flashing white cursor in the left corner I do see something regarding ATA but it goes by to fast to read and there is nothing in the logs regarding ATA errors.

 Dave

---

### Post by rodercot on 2009-03-04
Finally got this all to work on one of my machines. 
 
 first I created some scripts called 07LCDd and 08lirc and then 01mythtv

 the 07LCDd stops and starts LCDd 
 the 08lirc stops and RESTARTS lirc (start will not work for some reason it needs to say restart)
 and finally the 01mythtv just kills the frontend and then calls another resume script I created. 

 finally the livetv issue was the pvr-150 not unloading ivtv so I created a simple text file called modules and placed it in /etc/pm/sleep.d infact all of my suspend/resume scripts I place in that directory, this will preserve them if a distro upgrade overwrites the /usr/lib/pm-utils defaults.

 you need to chmod +x the scripts in /etc/pm/sleep.d EXCEPT the config script for unloading the ivtv module hence the one I called modules.

 If you would like to see the scripts I use post here and I will post a copy of them. most are a variation of this thread.

 [https://help.ubuntu.com/community/MythTV/PowerSaving](https://help.ubuntu.com/community/MythTV/PowerSaving)

 rgds,

 Dave

---

