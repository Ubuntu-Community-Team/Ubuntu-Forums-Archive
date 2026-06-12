---
title: "Master backend waking up slave"
date: 2011-01-16
forum: Mythbuntu
---

### Post by can2002 on 2011-01-16
[SIZE="3"][FONT="Verdana"]I've been running a single backend server for a while now - it's also running Asterisk for my phone system plus a few other services, hence it remains on 24x7.  It has a Nova-T 500 card plus a HVR-4000 card that's used for DVB-S/S2 purposes only.  All has worked fine other than I began to start conflicts with my growing recording list...

I recently purchased a couple of extra tuner cards plus a PC with the intention if installing it in my loft and normally be powered off.  My plan was to switch it on via Wake-On-LAN as and when I need the extra tuners.  It's configured as a slave backend and if I switch it on manually, I can view either live TV (by manually selecting the additional inputs) or schedule recordings.  I've also confirmed that WOL is working fine.

My problem is with the part I assumed would be fairly easy - getting my Master to switch it on and off as necessary.  I'd previously seen (and experimented with successfully) the Startup/Wakeup option page; however reading the descriptions of the options, that page seems to suggest all backends (including the master) will be shut-down down.  The next page "Backend Wakeup Settings" looked more promising and the "Sleep Command" and "Wake Command" options appeared to be exactly what I needed (specifically, the description mentions "The command used to put this slave to sleep/wake this slave from sleep".  I edited these settings while running mythtv-setup on the slave backend.  The commands reside on a directory on my master backend that is exported via NFS4.

Initially I configured the wake and sleep scripts to just place an entry in a log file so I could check it worked.  I then shut down my slave backend, scheduled three recordings (on different Muxes) and immediately saw a problem as Mythweb showed the third recording as a conflict (i.e. it seemed to ignore the availability of the tuner in my slave backend).  There was no entries in the log file I created to capture the wake and sleep commands.

Just to make sure I'd not messed up my slave backend, I manually powered it on via a WOL command and scheduled another recording, which worked fine.  I still had my 'tail -f' command running against the logfile mentioned and I noticed that the master was repeatedly running the wake command.

To summarise, it seems in my configuration I can only get the master backed to run my slave wakeup command if I've already powered on the latter.  I'm clearly missing some vital (and probably obvious) point here - I would greatly appreciate it if anyone could shed some light.

For reference, my master backend is running Ubuntu server 10.04 with the 0.23.1 MythTV PPA; my slave backend is running 10.10 and the same version of MythTV (via the PPA).  

Cheers in advance,
Chris[/FONT][/SIZE]

---

### Post by nickrout on 2011-01-17
I am thinking that your question MAY be outside the scope of what you will find an answer to in this forum. I suggest you try the mythtv-users mailing list, I know that there are quite a few experts there and have seen wakeups discussed there several times.

[http://www.mythtv.org/mailman/listinfo/mythtv-users/](http://www.mythtv.org/mailman/listinfo/mythtv-users/)

---

### Post by can2002 on 2011-01-31
Hi there,

Thanks for the reply and sorry for the slow response.

In advance of posting on the MythTV mailing list I checked again to see whether I could updated to 0.24 of MythTV on my master back-end (Lucid) as I thought it would make sense to be on the latest version.

After upgrading both back-ends and my front-ends I can happily confirm that the wakeup/sleep functionality is working.  

In case anyone else struggles, the process for sleeping appears to be for the master to send an instruction to the slave to execute the sleep script whereas wake script is run on the master.  When the slave shuts down it, its status changes to 'asleep' in mythweb.

Cheers,
Chris

---

### Post by brenthaag on 2011-09-04
Do you mind sharing the shutdown or wakeup scripts that you used?  Also, are these commands ONLY input in the slave backend configuration? Or both MBE and SBE?

---

### Post by can2002 on 2011-09-05
[FONT="Verdana"]Hi there,

As background, I've placed all my Myth stuff on a dedicated RAID drive on my MBE and exported it via NFS.  The slave mounts this to exactly the same path on boot.  I have a scripts sub-directory in my myth directory and put the two scripts there.  The sleep script is below:[/FONT]

[INDENT][FONT="Courier New"][SIZE="2"][COLOR="Red"]#!/bin/bash

# put sbe to sleep

lock_file='/tmp/blockshut'
log_file='/var/log/mythtv/sbe.log'

/bin/sleep 60

if [ -f $lock_file ]; then
    echo "`/bin/date`: Shutdown blocked" >> $log_file
else
    echo "`/bin/date`: Putting sbe to sleep" >> $log_file
    /usr/bin/sudo /sbin/halt -p
fi
[/COLOR][/SIZE][/FONT][/INDENT]

[FONT="Verdana"]The wake script is below:[/FONT]

[INDENT][FONT="Courier New"][SIZE="2"][COLOR="Red"]#!/bin/bash

# send WOL command to SBE
wol_cmd='/usr/bin/sudo /usr/bin/wakeonlan 00:01:02:03:04:05'

$wol_cmd >> /var/log/mythtv/sbe.log
echo "`/bin/date`: Waking up sbe" >> /var/log/mythtv/sbe.log
[/COLOR][/SIZE][/FONT][/INDENT]

[FONT="Verdana"]The sleep script is executed on the SBE, but the master sends it a 'go to sleep' signal that triggers execution.  The wake command is executed on the MBE; however they are both specified in mythtv-setup on the SBE, which is not particularly intuitive.

As you'll see from the sleep script, I put a check option in there to abort shutdown if a file exists in the tmp directory - you also need to use visudo on the SBE to allow the mythtv user to launch halt without prompting for a password.

It took a while to crack it and the attached scripts are not particularly flashy, but they get the job done and it's proved a fairly reliable solution.

Cheers,
Chris[/FONT]

---

### Post by brenthaag on 2011-09-07
Thanks, can2002...I will play with it this weekend, so I don't mess up any recordings during the week.

---

### Post by brenthaag on 2011-09-10
It works! However, now I have to figure out what do on the recordings...my frontend is on the master backend and any of the recordings on the slave backend are inaccessible when it is "asleep" (I thought the master backend might wake it up when needed for this purpose). So, now it looks like I need to look at NFS mounting...evn though I prefer Storage Groups, because they are much more fool proof! (if you have any suggestions, I would love some!)

Thanks for all your help.

---

### Post by can2002 on 2011-09-13
Hiya and no problem.

I've exported my whole MythTV RAID drive via NFS (on the MBE) and I mount it on the SBE, hence I record everything to the same path.

Cheers,
Chris

---

