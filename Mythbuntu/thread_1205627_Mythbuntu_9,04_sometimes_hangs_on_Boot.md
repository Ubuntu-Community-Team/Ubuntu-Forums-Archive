---
title: "Mythbuntu 9,04 sometimes hangs on Boot"
date: 2009-07-06
forum: Mythbuntu
---

### Post by leafpaul on 2009-07-06
This is an occasional problem which started after upgrading to Mythbuntu 9.04 (64 bit).  Front end and Back end both on the same machine.  The issue(s) are no more than a slight inconvenience but it would be nicer if they didn't happen.

Once in a while, say once per fortnight (2 boots per day), the boot process will hang (this hang is forever no timeout occurs).  The last screen message is "Starting Samba services".  

Machine details:
AMD dual core 5600
Hauppauge Nova T-500 dual tuner
Ethernet Card: Netgear WG311T

The solution is to restart the machine and all will be fine, but does anyone have any idea what might be causing this.  I have searched over the last few months and found nothing matching this issue except possibly this:

[http://ubuntuforums.org/showthread.php?t=1199751&highlight=mythbuntu+boot+issues](http://ubuntuforums.org/showthread.php?t=1199751&highlight=mythbuntu+boot+issues)

Although my issue sounds different: my boot issue is only occasional, the Tuner card is a Hauppauge Nova T-500 dual tuner and I have a fixed IP.

One other interesting thing that happens on my setup with 9.04 that didn't happen with 8.10 is that the wireless network connection now drops on a regular basis.  It will be fine for a period of time and then drop, it has dropped even midway through an active file transfer so it would seem that it is not just inactivity that causes the drop.  ifdown/ifup sorts this out.  This wireless network drop is a daily event ie during approx 4 hours up time daily it is unusual for the connection not to drop.  Not sure if this is related to the boot issue but see the syslog below.

Selected Log Details:

log.smbd (samba)
Nothing is written to this log on a failed boot.

On a successful boot:
[2009/07/06 11:02:22,  0] smbd/server.c:main(1260)
  smbd version 3.3.2 started.

followed by an attempt to connect to my network printer (this fails as the printer is typically switched off)

Syslog:
Jul  6 01:01:48 pvr ntpd[3190]: ntpd 4.2.4p4@1.1520-o Wed May 13 21:10:45 UTC 2009 (1)
Jul  6 01:01:48 pvr ntpd[3191]: precision = 1.000 usec
Jul  6 01:01:48 pvr ntpd[3191]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Jul  6 01:01:48 pvr ntpd[3191]: Listening on interface #1 wildcard, ::#123 Disabled
Jul  6 01:01:48 pvr ntpd[3191]: Listening on interface #2 lo, ::1#123 Enabled
Jul  6 01:01:48 pvr ntpd[3191]: Listening on interface #3 lo, 127.0.0.1#123 Enabled
Jul  6 01:01:48 pvr ntpd[3191]: Listening on interface #4 ath0, 192.168.2.4#123 Enabled
Jul  6 01:01:48 pvr ntpd[3191]: kernel time sync status 0040
Jul  6 01:01:48 pvr ntpd[3191]: frequency initialized -74.886 PPM from /var/lib/ntp/ntp.drift

[B]**********************
Failed boot ends here
**********************[/B]

Next lines on successful boot:
Jul  6 11:02:22 pvr kernel: [   30.753520] ath0: direct probe to AP 00:12:bf:02:a6:e1 try 1
Jul  6 11:02:22 pvr kernel: [   30.756294] ath0 direct probe responded
Jul  6 11:02:22 pvr kernel: [   30.756300] ath0: authenticate with AP 00:12:bf:02:a6:e1
Jul  6 11:02:22 pvr kernel: [   30.773618] ath0: authenticated
Jul  6 11:02:22 pvr kernel: [   30.773627] ath0: associate with AP 00:12:bf:02:a6:e1
Jul  6 11:02:22 pvr kernel: [   30.782338] ath0: RX AssocResp from 00:12:bf:02:a6:e1 (capab=0x431 status=0 aid=2)
Jul  6 11:02:22 pvr kernel: [   30.782345] ath0: associated

Myth Back end Log:

"2009-07-06 01:01:47.928 Using runtime prefix = /usr
2009-07-06 01:01:47.975 Empty LocalHostName.
2009-07-06 01:01:48.017 Using localhost value of pvr
2009-07-06 01:01:48.173 New DB connection, total: 1
2009-07-06 01:01:48.224 Connected to database 'mythconverg' at host: localhost
2009-07-06 01:01:48.321 Closing DB connection named 'DBManager0'
2009-07-06 01:01:48.345 Connected to database 'mythconverg' at host: localhost
2009-07-06 01:01:48.370 New DB connection, total: 2
2009-07-06 01:01:48.409 Connected to database 'mythconverg' at host: localhost
2009-07-06 01:01:48.426 Current Schema Version: 1214
Starting up as the master server."


[B]**********************
Failed boot ends here
**********************[/B]

The next line should be: "New DB connection, total: 3"

---

